# Next Round Macro Gates Plan

日期：2026-03-19
DRI：macro
目标：把上一轮 review 的 3 条高优先级方向收敛成**可实现的 macro veto / regime gate 方案**，直接对接现有 `RegimeSnapshot / shock_mode / forbidden_set / forbidden_*` contract。

---

## 一、结论

### 1) 设计总原则
下一轮 macro/risk gate 不做“宏观评论层”，只做三件事：
1. **在制度切换点先刹车**（Macro Shock Gate）
2. **在跨资产定价恶化时阻断错误外推**（Rates-FX-Vol Cross-Asset Veto）
3. **在中国传导链断裂时阻断 A 股 risk-on 错判**（China Transmission Gate）

### 2) 与现有主线 contract 的兼容口径
不建议下一轮先大改 schema。最小实现直接复用现有字段：
- `RegimeSnapshot.regime_tag`
- `RegimeSnapshot.risk_budget`
- `RegimeSnapshot.forbidden_set`
- `RegimeSnapshot.shock_mode`
- `EventContext.forbidden_blocked`
- `forbidden_reason`
- `forbidden_codes_triggered`

**兼容策略：**
- `shock_mode` 继续只用现有三态：`off / watch / active`
- 用户要求的 `cooldown` 不额外扩 enum；先落在 **evidence metadata / event_state** 里，值为：
  - `pre_watch`
  - `active`
  - `cooldown`
- 即：
  - `pre_watch -> shock_mode = watch`
  - `active -> shock_mode = active`
  - `cooldown -> shock_mode = watch`

这样可避免为了一个“cooldown”状态立刻改 schema / tests / log contract。

### 3) soft gate vs hard veto 的明确边界

#### Hard veto（直接 block 新增风险）
满足以下任一类，应直接进入 `forbidden_set`：
1. **事件冲击已确认**：重大事件发布后，`surprise` 超阈值，且跨资产响应确认风险切换
2. **跨资产双红或三红**：Rates / Vol / FX / Oil 中出现 2 个以上 red trigger
3. **中国传导 2-of-3 断裂**：`CNH`、`northbound`、`HK-A decouple` 三项里至少两项恶化
4. **evidence freshness 失真到无法判读**：关键 gate 字段缺失或 stale 达到 blocker 条件时，不允许扩大风险

#### Soft gate（降仓 / 提高阈值 / 减频，不直接 block）
1. 单一因子进入 amber / watch
2. 事件前观察窗（pre-event watch）
3. 事件后未形成 confirm move，但仍在冷却期
4. 中国传导出现单项恶化，但未形成 stacked breakdown

### 4) 下一轮最小实现 Top 3（只保留这 3 个）

#### Top 1：Macro Shock Gate（先做）
原因：最危险的失真来自制度切换点，不来自平稳期参数。

#### Top 2：Rates-FX-Vol Cross-Asset Veto
原因：这是最小但解释力最高的“宏观刹车片”。

#### Top 3：China Transmission Gate
原因：你的主战场是 A 股 / 港股映射，不补这层会反复把 US risk-on 错套到 A 股。

---

## 二、证据

### 1) 现有主线已经有 veto 的承载位，但还没有 macro gate 的正式接线
代码真值已具备：
- `RegimeSnapshot`：`risk_budget / forbidden_set / shock_mode / regime_snapshot_id`
- `EventContext`：`forbidden_blocked / forbidden_reason / forbidden_codes_triggered`
- `MacroRegimeV1`：已封装 frozen interface

这说明下一轮**不缺落点，缺的是 gate 逻辑本身**。

### 2) 现有 risk gate 仍未直接消费 macro
`risk_gate.py` 当前 adverse trace 只读：
- `market`
- `sentiment`
- `capital_flow`

这说明：
- 当前系统的宏观仍主要停留在 overlay / score 层
- 还没有成为真正的 top-down veto

### 3) 当前 strategy macro 消费面太窄，无法承担 veto 职责
`strategy_templates.py` 当前真正读取的 macro 仍主要是：
- `pmi`
- `manufacturing_pmi`
- `composite_pmi`
- `cn_pmi`
或 qualitative regime token。

因此：
- `PMI` 可以继续作为背景因子
- 但不能承担事件冲击 / rates shock / FX stress / oil shock 的 veto 任务

### 4) 现有 freshness 语义已经存在，适合扩到 gate 层
`schema.py` 已有：
- `Freshness = fresh | stale | unknown`

因此 gate 设计无需再发明 freshness 语义，只需把关键字段的 TTL / session 规则补齐。

---

## 三、动作

# A. Macro Shock Gate 设计

## A1. 事件清单（按优先级分层）

### Tier 1：可触发 hard veto 的事件
#### US
- `US_FOMC_RATE`
- `US_FOMC_SEP_DOTPLOT`
- `US_CPI`
- `US_NFP`

#### China
- `CN_MLF`
- `CN_LPR`
- `CN_PMI_OFFICIAL`
- `CN_TS_FSF`（社融 / 信贷总量窗口）

### Tier 2：默认 soft gate，必要时升级 hard 的事件
#### US
- `US_PPI`
- `US_ISM_MANUFACTURING`
- `US_RETAIL_SALES`
- `US_PCE_CORE`

#### China
- `CN_CPI_PPI`
- `CN_EXPORT_IMPORT`
- `CN_GDP`
- `CN_POLITBURO_POLICY_SIGNAL`（仅在被结构化为事件后纳入）

### Tier 3：只做注释/日志，不进入下一轮最小实现
- 地缘 headline
- 临时政策传闻
- 非结构化媒体 headline

> 原则：下一轮最小实现只做 Tier 1 + Tier 2，不引入 headline NLP。

## A2. watch / active / cooldown 规则

### 事件状态模型
新增内部字段：`event_state`
- `pre_watch`
- `active`
- `cooldown`

对现有 schema 的映射：
- `pre_watch -> shock_mode = watch`
- `active -> shock_mode = active`
- `cooldown -> shock_mode = watch`
- 其余 -> `shock_mode = off`

### 默认时间窗（按日线系统设计）

#### US 事件（对 A 股 / 港股策略）
- `pre_watch`：事件前 **1 个交易日** CN session
- `active`：事件发布后到**下一个 CN/AH 可交易 session 结束**
- `cooldown`：再延续 **1~2 个交易日**，取决于是否出现 shock confirm

#### China 事件（对 A 股策略）
- `pre_watch`：事件前 **0.5~1 个交易日**
- `active`：事件当日
- `cooldown`：事件后 **1 个交易日**，若价格/汇率/资金流仍延续冲击，则延至 2 日

### 事件冲击分级

#### Soft gate 条件
- 进入 `pre_watch`
- 进入 `cooldown` 且 shock 未确认
- Tier 2 事件发布但 `surprise` 未超阈值

#### Hard veto 条件
事件必须同时满足：
1. 事件属于 Tier 1
2. `surprise` 超阈值，且方向不利于当前风险暴露
3. 至少一个跨资产确认项同步恶化（如 `US10Y / VIX / USDCNH / WTI`）

### `surprise` 的最小表达方式
下一轮不必追求复杂标准化，先统一：
- `surprise_direction`: `hotter / cooler / stronger / weaker / hawkish / dovish`
- `surprise_magnitude`: `small / medium / large`

建议 hard veto 触发只用：
- `surprise_magnitude == large`
- 或 `surprise_magnitude == medium` 且跨资产确认 >= 2 项

## A3. 事件门控动作

### Soft gate 动作
- `risk_budget *= 0.75`
- `entry_score_threshold += 0.05`
- 禁止加杠杆 / 禁止放大单票仓位

### Hard veto 动作
- `forbidden_set += ['MACRO_EVENT_SHOCK']`
- block 新开 `BUY`
- 已有仓位允许减仓/止损，不强制平仓

## A4. 建议的事件 gate 代码集
- `EVENT_WATCH_US_FOMC`
- `EVENT_WATCH_US_CPI`
- `EVENT_WATCH_US_NFP`
- `EVENT_WATCH_CN_MLF`
- `EVENT_WATCH_CN_LPR`
- `EVENT_ACTIVE_SHOCK`
- `EVENT_COOLDOWN`
- `VETO_EVENT_LARGE_SURPRISE`

---

# B. Rates-FX-Vol Cross-Asset Veto 设计

## B1. 最小字段集（下一轮只做这些）
- `US10Y`
- `T10Y2Y`（2s10s）
- `VIX`
- `WTI`
- `USDCNH`
- 可选但不进最小实现：`DXY`

## B2. freshness / TTL 规则

### 字段 freshness 分类
#### Session-close 型
- `US10Y`
- `T10Y2Y`
- `VIX`

规则：
- 使用最近一个 **US session close**
- 若超过 **1 个 US 交易日未更新** -> `stale`
- 若缺失或超过 **2 个 session** -> blocker 候选

#### Quasi-live 型
- `WTI`
- `USDCNH`

规则：
- 在相关市场活跃时段内，超过 **4 小时未更新** -> `stale`
- 离市场活跃期时，可沿用最近 session 值，但必须标记 `freshness = stale|session_carry`

### freshness 的 gate 规则
- 单字段 stale：最多触发 soft gate，不直接 hard veto
- 关键字段（`US10Y`, `VIX`, `USDCNH`）中若有 **2 个 stale/unknown**：
  - 不允许 hard risk-on 结论
  - 对新增风险至少 soft gate
- 若 hard veto 需要的字段本身 stale：
  - 不做方向性 hard veto
  - 改为 `EVIDENCE_FRESHNESS_BLOCK`，阻止扩大风险

## B3. 阈值/区间表达方式
不建议单点阈值，建议统一成 **green / amber / red 三段**。

### 1) US10Y（利率冲击）
使用两个维度：
- `level_band`
- `5d_delta_bp`

默认区间：
- Green：`5d_delta_bp < +10`
- Amber：`+10 ~ +25`
- Red：`> +25`

可选附加绝对位：
- 若 `US10Y >= 4.5%`，则同等 delta 下上调一级风险

### 2) VIX（波动率）
- Green：`< 18`
- Amber：`18 ~ 25`
- Red：`> 25`
- Severe：`> 30`

### 3) WTI（油价冲击）
- Green：`< 85`
- Amber：`85 ~ 95`
- Red：`> 95`
- Severe：`> 100`

### 4) USDCNH（中国外部约束）
用两个维度：
- `3d_change_pct`
- `absolute_level`

默认区间：
- Green：`3d depreciation < 0.3%`
- Amber：`0.3% ~ 0.8%`
- Red：`> 0.8%`

可选附加绝对位：
- 若 `absolute_level` 突破最近 60 日高分位区间，上调一级

### 5) 2s10s（曲线）
2s10s 不单独做 veto，主要做 regime 解释辅助：
- steepening + rates up：偏再通胀风险
- flattening/inversion + VIX up：偏衰退 / risk-off

## B4. Cross-asset 触发逻辑

### Soft gate
满足任一：
- 1 个 red
- 2 个 amber

动作：
- `risk_budget *= 0.75`
- `forbidden_codes_triggered += ['XASSET_SOFT_GATE']`

### Hard veto
满足任一：
- `US10Y red` + `VIX red`
- `VIX red` + `USDCNH red`
- `WTI red` + `USDCNH red`
- 任一 `severe` + 任一 `amber/red`

动作：
- `forbidden_set += ['XASSET_VETO']`
- `forbidden_reason = 'stacked_cross_asset_risk'`

## B5. 建议的代码集
- `VETO_RATES_SHOCK`
- `VETO_VOL_SPIKE`
- `VETO_OIL_SHOCK`
- `VETO_FX_STRESS`
- `VETO_CROSS_ASSET_STACKED`
- `SOFT_CROSS_ASSET_AMBER`
- `EVIDENCE_FRESHNESS_BLOCK`

---

# C. China Transmission Gate 设计

## C1. 最小字段集
- `USDCNH`
- `northbound_flow`
- `HSTECH_return_3d`
- `A_GROWTH_BASKET_return_3d`（建议用 `创业板ETF / 科创50 / growth basket proxy`）
- 可选补充：`CSI300 breadth`

## C2. 三条核心触发链

### 1) CNH Stress
定义：
- `USDCNH` 进入 red
或
- `USDCNH` 连续 2~3 日快速走弱

作用：
- 代表中国风险资产的外部约束增强

### 2) Northbound Breakdown
定义（默认阈值，后续可校准）：
- 连续 **2/3 日净流出** -> soft
- 连续 **3 日净流出且累计达到较大负值** -> hard 候选

建议默认数值：
- soft：最近 3 日累计 `< -50 亿`
- hard：最近 3 日累计 `< -120 亿`

### 3) HK-A Decouple
定义：
- `HSTECH_3d_return - A_GROWTH_3d_return <= -4%`
且 `HSTECH_3d_return < -2%`

含义：
- 港股科技先走弱，而 A 股成长尚未充分反映
- 对 A 股成长风格是前瞻性负面信号

## C3. 触发逻辑

### Soft gate
满足以下任一：
- CNH Stress
- Northbound soft outflow
- HK-A decouple soft

动作：
- 只对 A 股成长/高弹性 basket 生效
- `risk_budget *= 0.8`
- `entry_score_threshold += 0.05`

### Hard veto
满足以下任一：
- 三项中任意 **2-of-3** 同时触发
- `CNH red` + `northbound hard outflow`
- `HK-A decouple` + `northbound hard outflow`

动作：
- `forbidden_set += ['CHINA_TRANSMISSION_BREAK']`
- block A 股成长/高 beta 的新增 `BUY`
- 对红利/防御/资源策略不必一刀切，可只 soft gate

## C4. China gate 的 hard / soft 分类说明

### 只能先做 soft gate 的部分
- `northbound_flow` 的单日信号
- `HK-A decouple` 的单次偏离
- `CNH` 的轻微走弱

### 可以做 hard veto 的部分
- `CNH red + northbound hard outflow`
- `northbound hard outflow + HK-A decouple`
- `2-of-3 breakdown`

## C5. 建议代码集
- `SOFT_CNH_STRESS`
- `SOFT_NORTHBOUND_OUTFLOW`
- `SOFT_HK_A_DECOUPLE`
- `VETO_CHINA_TRANSMISSION_BREAK`
- `VETO_CNH_NB_STACKED`
- `VETO_HK_A_NB_STACKED`

---

# D. 下一轮最小实现优先级（Top 3）

## Priority 1 — Macro Shock Gate（先接入）
最小实现：
1. 事件日历输入（仅 Tier 1 + Tier 2）
2. `event_state` 计算
3. `shock_mode` 映射
4. 事件 soft/hard 规则写入 `forbidden_*`

**交付标准**：
- 回测中能看见事件前 watch、事件后 active、冷却期 cooldown（metadata）
- 新开 BUY 会被相应 throttle / block

## Priority 2 — Cross-Asset Veto
最小实现：
1. 接 `US10Y / VIX / WTI / USDCNH` 四字段
2. 加 freshness 与 band classification
3. 实现 `1 red or 2 amber => soft`、`stacked red => hard`

**交付标准**：
- 能稳定产出 `VETO_RATES_SHOCK / VETO_VOL_SPIKE / VETO_OIL_SHOCK / VETO_FX_STRESS / VETO_CROSS_ASSET_STACKED`

## Priority 3 — China Transmission Gate
最小实现：
1. 接 `USDCNH / northbound_flow / HSTECH vs A-growth spread`
2. 实现 `2-of-3 breakdown => hard`
3. 仅对 A 股成长/高 beta basket 生效

**交付标准**：
- 能阻断“US/HK 看似 risk-on，但 A 股成长传导已断”的错误扩仓

---

# E. 建议的最小输出 contract（供实现时直接采用）

```json
{
  "macro_gate_snapshot": {
    "as_of": "2026-03-19T09:30:00+08:00",
    "regime_tag": "neutral",
    "risk_budget": 0.75,
    "shock_mode": "watch",
    "event_state": "pre_watch",
    "forbidden_set": [],
    "forbidden_reason": null,
    "forbidden_codes_triggered": [
      "EVENT_WATCH_US_CPI",
      "SOFT_CROSS_ASSET_AMBER"
    ],
    "evidence": {
      "US10Y": {"value": 4.23, "freshness": "fresh"},
      "VIX": {"value": 22.37, "freshness": "fresh"},
      "WTI": {"value": 94.65, "freshness": "stale"},
      "USDCNH": {"value": 6.90, "freshness": "fresh"},
      "northbound_flow": {"value": -32.4, "freshness": "fresh"}
    }
  }
}
```

> 实现原则：先让 `macro_gate_snapshot` 稳定产出，再决定策略层 / risk_gate 层怎么消费更多细节。

---

## 四、路径
- `/Users/study/.openclaw/workspace-macro/knowledge/daily/2026-03-19/next-round-macro-gates-plan.md`
