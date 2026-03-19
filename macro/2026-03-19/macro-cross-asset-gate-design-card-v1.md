# Macro / Cross-Asset Gate 设计卡 v1

日期：2026-03-19
DRI：macro
目标：给交易策略框架提供**最小必要集**的宏观/跨资产 gate，只定义前提、区间、否决条件，不替 trading 给最终交易结论。

---

## 一、结论

### A. 当前适合纳入交易框架的最小必要 gate 清单
只保留 3 个：

1. **Macro Shock Gate**
   - 用途：处理 FOMC / CPI / NFP / MLF / LPR 等“制度切换点”
2. **Rates-FX-Vol Cross-Asset Gate**
   - 用途：处理利率、波动率、油价、汇率联动恶化
3. **China Transmission Gate**
   - 用途：处理 CNH / 北向 / HK-A decouple 对 A 股风险偏好的传导失灵

> 这 3 个已经覆盖：事件风险、全球定价约束、中国本地传导。再往上加因子，当前阶段更容易噪音大于增益。

### B. 每个 gate 的输入、频率、触发条件、否决条件

## 1) Macro Shock Gate

### 输入数据
- US: `FOMC`、`CPI`、`NFP`
- China: `MLF`、`LPR`、`官方 PMI`
- 辅助确认：`US10Y`、`VIX`、`USDCNH`、`WTI`

### 更新频率
- 事件驱动
- 在事件前后按 session 刷新，不要求分时回放到分钟级

### 触发条件
- `pre_watch`：事件前 1 个交易日（US 事件按下一个 CN/AH 可交易 session 映射）
- `active`：事件发布后至下一个主要交易 session 结束
- `cooldown`：active 后 1~2 个交易日

### 否决条件
**Hard veto**
- Tier 1 事件（FOMC/CPI/NFP/MLF/LPR/PMI）
- 且 `surprise_magnitude = large`
- 且跨资产确认项 >= 1（`US10Y`、`VIX`、`USDCNH`、`WTI` 中至少一项同步恶化）

**Soft gate**
- pre_watch
- cooldown
- Tier 2 事件（PPI/ISM/社融等）且未出现大 surprise

### 动作建议
- Soft: `risk_budget *= 0.75`，`entry_threshold + 0.05`
- Hard: block 新增 `BUY`，允许减仓/止损

---

## 2) Rates-FX-Vol Cross-Asset Gate

### 输入数据
- `US10Y`
- `T10Y2Y`
- `VIX`
- `WTI`
- `USDCNH`

### 更新频率
- `US10Y / T10Y2Y / VIX`：按 US session close
- `WTI / USDCNH`：准实时 / session-carry

### 触发条件（区间表达）

#### US10Y
- Green: 5d 变动 `< +10bp`
- Amber: `+10bp ~ +25bp`
- Red: `> +25bp`

#### VIX
- Green: `< 18`
- Amber: `18 ~ 25`
- Red: `> 25`

#### WTI
- Green: `< 85`
- Amber: `85 ~ 95`
- Red: `> 95`

#### USDCNH
- Green: 3d 贬值 `< 0.3%`
- Amber: `0.3% ~ 0.8%`
- Red: `> 0.8%`

### 否决条件
**Hard veto**
- `US10Y red + VIX red`
- `VIX red + USDCNH red`
- `WTI red + USDCNH red`
- 或任一 severe（如 VIX>30 / WTI>100）+ 任一 amber/red

**Soft gate**
- `1 red`
- 或 `2 amber`

### freshness 规则
- `US10Y / VIX / USDCNH` 里若有 2 个 `stale/unknown`：不允许做 hard risk-on 结论，只能 soft gate
- 若 hard veto 所需关键字段 stale：改为 `evidence freshness block`，阻止扩大风险

---

## 3) China Transmission Gate

### 输入数据
- `USDCNH`
- `northbound_flow`
- `HSTECH_return_3d`
- `A_growth_proxy_return_3d`（如创业板/科创50/growth basket）

### 更新频率
- `USDCNH`：准实时 / session-carry
- `northbound_flow`：日内 / 日终
- `HK-A spread`：按收盘日频

### 触发条件

#### CNH Stress
- `USDCNH` 进入 red
或
- 连续 2~3 日快速走弱

#### Northbound Breakdown
- Soft: 最近 3 日累计 `< -50 亿`
- Hard 候选: 最近 3 日累计 `< -120 亿`

#### HK-A Decouple
- `HSTECH_3d_return - A_growth_3d_return <= -4%`
- 且 `HSTECH_3d_return < -2%`

### 否决条件
**Hard veto**
- `CNH / northbound / HK-A decouple` 中 **2-of-3 同时触发**

**Soft gate**
- 单项恶化但未 stacked

### 作用范围
- 优先作用于 **A 股成长 / 高 beta / 高弹性 basket**
- 不对红利/防御/资源策略一刀切

---

### C. 哪些可以先规则化，哪些暂时只能人工判定

## 可先规则化（建议立刻做）
1. 事件日历型：FOMC / CPI / NFP / MLF / LPR / PMI
2. 跨资产数值型：US10Y / VIX / WTI / USDCNH
3. 中国传导数值型：北向累计流入流出、HSTECH vs A-growth 3d spread
4. freshness gate：fresh / stale / unknown + TTL 规则

## 暂时只能人工判定
1. 地缘政治 headline 的真假强弱
2. 政策措辞的“超预期程度”文本解读
3. 非结构化传闻 / 媒体放风
4. 极端行情中“市场在交易增长还是交易流动性”的叙事切换

> 这些先保留为人工 review，不要硬塞进 v1 自动 gate。

---

### D. 哪些最容易过拟合/事后归因，必须暂缓
必须暂缓的内容：
1. **太多因子一起上**
   - 如 DXY、金价、铜价、信用利差、ETF 流、行业主力流、海外风格因子同时并入
2. **政策 headline 语义打分自动化**
   - 当前没有稳定结构化真值，极易事后归因
3. **单次事件后的多阈值微调**
   - 容易为历史样本“修参数”，不具备可迁移性
4. **把 market proxy 当 validated macro regime**
   - 现有系统明确不是这个能力层级
5. **把单日北向或单日港股异动直接上升为 hard veto**
   - 单点噪音太大，必须要求 stacked / multi-day confirm

---

### E. 今天能先做的 P0 / P1 清单

## P0（今天就能开做）
1. **冻结 gate contract v1**
   - 统一输出字段：
     - `shock_mode`
     - `risk_budget`
     - `forbidden_set`
     - `forbidden_reason`
     - `forbidden_codes_triggered`
     - `evidence_asof_time`
2. **先做 3 个 gate 的最小 code list**
   - `MACRO_EVENT_SHOCK`
   - `XASSET_VETO`
   - `CHINA_TRANSMISSION_BREAK`
   - 以及对应 soft codes
3. **先把 hard / soft 判定规则写成表驱动配置**
   - 不写死在策略里
4. **补 freshness / TTL 规则**
   - 至少覆盖 `US10Y / VIX / USDCNH / northbound`
5. **先接 risk gate，不先做复杂 alpha 解释**
   - 目标是“能拦截错误风险”，不是“解释所有市场”

## P1（今天若有余力）
1. 做 `event_state = pre_watch / active / cooldown` 的 metadata 输出
2. 给 A 股成长 basket 单独挂 China Transmission Gate
3. 做最小回测切片：
   - 事件周
   - rates spike 周
   - CNH/北向恶化周
4. 加一版日志落点，确保事后能看到：
   - 哪个 gate 触发
   - 是 soft 还是 hard
   - 用了哪些 evidence

---

## 二、证据

1. 当前主线已有 `RegimeSnapshot / shock_mode / forbidden_*`，说明落点已存在，优先级应放在 gate 逻辑，不在 schema 大改。
2. 当前 macro 侧真正能稳定落地的，只有：
   - 事件日历
   - 利率/波动率/汇率/油价
   - CNH/北向/HK-A spread
   这些因子解释力高、可回测、可回退。
3. 当前最容易出错的地方不是“因子不够多”，而是：
   - 事件冲击没被识别
   - 跨资产 stacked risk 没被 veto
   - A/H/US 传导断裂时仍按 risk-on 外推
4. 因此 v1 只保留 3 个 gate，是为了避免“为了看起来全面而堆太多因子”。

---

## 三、动作

### 建议今日执行顺序
1. 先冻结 `macro-cross-asset-gate.v1` 配置表
2. 再接入 risk gate 所需最小输出字段
3. 最后补 3 个场景测试：
   - 事件冲击
   - 利率/波动率 stacked risk
   - 中国传导断裂

### 路径
- `/Users/study/.openclaw/workspace-macro/knowledge/daily/2026-03-19/macro-cross-asset-gate-design-card-v1.md`
