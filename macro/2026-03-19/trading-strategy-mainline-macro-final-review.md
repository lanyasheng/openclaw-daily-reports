# 交易策略优化主线：最终宏观审阅与下一步方向建议

日期：2026-03-19
DRI：macro
范围：基于当前主线真值（runtime/metrics/capital-flow/runtime-doc-v3/P0-2b/real_backtest tests 已收口）做 macro 侧最终审阅。**只审系统稳健性，不重写交易结论。**

---

## 一、结论

### 1.1 总判断
当前系统已经具备了**可运行、可回测、可追踪 runtime factor contract** 的主干，但从 macro 视角看，它现在更像：

> **“价格主导 + 少量运行时 overlay 的波段系统”**，
> 而不是一个已经具备**宏观 veto / regime gating / 事件风控**能力的中短波段系统。

换句话说：
- **作为工程主干**：当前状态是合格的，可以进入“结果验收/下一轮规划”阶段；
- **作为跨 regime 稳健系统**：当前 macro 层还不够，尤其缺少**宏观 shock 时的一票否决层**。

### 1.2 当前系统隐含的 regime 假设
当前主线隐含了三个假设：

1. **宏观变化是慢变量**
   - 更适合 PMI/景气冷暖这类低频背景，而不是 FOMC/CPI/NFP/油价冲击这类快变量。
2. **价格行为已经吸收了足够多的宏观信息**
   - 允许 `market` 因子用价格横截面 proxy 代替真实宏观 regime。
3. **宏观更多是加减分 overlay，而不是硬 veto**
   - 即使 macro 缺失，主链也继续运行；这保证了鲁棒性，但也意味着宏观尚未成为“刹车系统”。

### 1.3 当前系统在哪些宏观环境下更可能失真
**最容易失真的不是“正常震荡市”，而是 regime 切换和外部冲击市。**

重点是三类：

#### A. 再通胀 / 利率再定价阶段
典型特征：
- 美债长端快速上行
- VIX 抬升
- 油价/商品重新主导风险偏好
- 成长股估值被压缩

此时系统容易失真，因为当前 macro 侧主要支持 PMI / qualitative regime，**不足以表达 duration shock、inflation re-acceleration、oil shock**。

#### B. 重大宏观事件窗口
包括：
- FOMC / CPI / NFP
- 中国 MLF / LPR / 社融 / PMI
- 突发地缘政治与能源冲击

此时最容易出现：
- 前一日 still risk-on，事件后瞬间切成 risk-off
- bar-by-bar 回测在日线层面看起来平滑，但真实交易时点面临 gap risk

当前系统对这类风险**没有显式 event veto**，所以更容易把“事件前后的制度切换”误当成同一种市场。

#### C. A/H/US 传导链失灵阶段
典型特征：
- 港股科技先转弱，但 A 股相关成长滞后补跌
- US 科技仍强，但 CNH / 北向 / 港股已走弱
- 北向和价格出现背离，或者 HK/A decouple

当前系统有 `market` / `capital_flow` / `sentiment`，但**缺少一层明确的“中国传导 veto”**，因此对 A 股中短波段而言，最容易高估外盘 risk-on 的可复制性。

### 1.4 哪些宏观结论不能被现有数据链路支持
当前系统**不能**严肃支持以下几类结论：

1. **“系统已经具备 Fed / 通胀 / 利率路径交易能力”**
   - 现有宏观 runtime 已接线，但还没有 repository-native 的宏观抓取/缓存/标准化主链；
   - 更关键的是，策略模板当前只显式消费 `pmi / manufacturing_pmi / composite_pmi / cn_pmi` 或 qualitative regime。

2. **“当前 market 因子已经等价于 validated macro regime”**
   - `market_engine.py` 已明确写明：这是 minimal runtime market context，**不是 validated macro regime model**。

3. **“宏观 veto 已经真正进入执行风控”**
   - 当前 `risk_gate.py` 的 adverse trace 只看 `market / sentiment / capital_flow`，**没有直接消费 macro**。

4. **“capital flow 已经在长周期/全样本上验证了增强效果”**
   - 当前 acceptance truth 已明确：部分 benchmark/真实股票样本的历史 capital-flow 会落入空数据/fallback 路径，因此不能把“链路跑通”表述成“宏观/资金流 alpha 已验证”。

### 1.5 下一步最值得加的 3 个 macro/risk gate 方向（按优先级）

#### 优先级 1：事件型 Macro Shock Gate
**目标**：把“事件前后不是同一种市场”这件事，显式写进系统。

应覆盖：
- FOMC / CPI / NFP
- 中国 MLF / LPR / 社融 / PMI
- 重大地缘/能源 shock

建议动作：
- 建 `macro_event_gate`：事件前后设置 `watch / active / cooldown` 窗口
- 在事件窗口内：
  - 降低 risk_budget
  - 抬高 entry threshold
  - 或直接 block 新开仓

**为什么排第 1**：
当前最危险的失真来自**制度切换点**，不是平稳期的参数细节。

#### 优先级 2：Rates-FX-Vol Cross-Asset Veto
**目标**：用少量高解释力跨资产指标，补上 PMI 无法覆盖的 risk-off 场景。

最小建议字段：
- `US10Y / 2s10s`
- `VIX`
- `WTI`
- `USDCNH`
- 可选：`DXY`

建议规则：
- `US10Y` 快速上冲 + `VIX` 抬升 → block 高久期/高 beta 进攻
- `WTI` 冲击 + `USDCNH` 承压 → block A/H 成长扩仓
- 多项同时命中 → 触发 `forbidden_set`

**为什么排第 2**：
这层是最小但高价值的“宏观刹车片”，能显著减少“PMI 还行但资产定价已经恶化”的误判。

#### 优先级 3：China Transmission Gate（CNH / 北向 / HK-A decouple）
**目标**：让系统知道“外盘 risk-on 不一定能传到 A 股”。

最小建议字段：
- `USDCNH`
- `northbound_flow`
- `HSTECH vs A-share growth basket` 相对强弱
- `CSI300 / 创业板 / 科创50` breadth

建议规则：
- CNH 走弱 + 北向连续流出 + 港股科技先转弱 → 对 A 股成长/高弹性策略降权或 veto
- 若 US 科技继续强、但 HK/A 传导断裂 → 只允许 reduced size，不允许把美股 risk-on 直接外推到 A 股

**为什么排第 3**：
你的主战场不是纯 US。若没有中国传导 gate，系统会在“全球看起来没问题、A 股其实承压”的阶段反复失真。

### 1.6 下一步方向建议（一句话）
**下一轮不该继续做参数扫参，而应把“宏观制度切换时怎么刹车”做成第一优先级。**

---

## 二、证据

### 2.1 代码/文档真值：macro 已接线，但还是“caller-supplied overlay”，不是闭环主数据面
- `docs/reports/A01_MACRO_RUNTIME_REPORT_20260317.md` 明确写到：
  - macro runtime 已接到默认 bar-by-bar 执行路径；
  - 但 **“No repository-native macro loader/provider existed”**。
- 这意味着当前系统能**消费** macro，但不代表已经有稳定、自洽、可审计的宏观数据供给主链。

### 2.2 策略模板当前真正消费的 macro 很窄
- `research/v2_portfolio/strategy_templates.py`
  - `_MACRO_PMI_KEYS = ("pmi", "manufacturing_pmi", "composite_pmi", "cn_pmi")`
  - `_score_macro_factor()` 优先读取 PMI 数值，或 qualitative `regime` 文本 token
- 结论：
  - 当前 macro 因子主要表达“景气/收缩背景”
  - **并不能直接表达**利率 shock、通胀 surprise、FX stress、商品冲击

### 2.3 当前 market 因子不是 validated macro regime
- `research/v2_portfolio/market_engine.py` 顶部已明确：
  - `This is still a lightweight cross-sectional price-action proxy.`
  - `It is not a validated macro regime model.`
- 结论：
  - 当前 `market` 更像“价格温度计”，不是“宏观制度识别器”

### 2.4 当前执行风控未直接消费 macro veto
- `research/v2_portfolio/risk_gate.py` 的 `_extract_adverse_trace_factors()` 只看：
  - `market`
  - `sentiment`
  - `capital_flow`
- **没有直接纳入 `macro` adverse trace**。
- 结论：
  - 当前宏观更多体现在策略评分，不体现在最终硬风控
  - 这就是“有油门提示、没有宏观刹车”的结构性缺口

### 2.5 资金流/增强因子仍存在 fallback 场景，不能夸大为 alpha 已验真
- `INTEGRATION_ROUND3_ACCEPTANCE_REPORT_20260317.md` 明确写到：
  - benchmark 样本历史 capital-flow 查询会落入空数据/fallback path
  - 不能把 scaffold / fallback 说成“已验证 alpha”
- `REAL_STOCK_BACKTEST_VALIDATION_20260318.md` 也写到：
  - 真实 A 股 4 只股票主链已跑通
  - 但 capital flow 对这些股票过滤后为空，属于 graceful degradation，不是 blocker
- 结论：
  - 主链能跑通 ≠ 因子有效性已被充分支持

### 2.6 当前外部环境本身也提示“不能把系统当纯 risk-on 引擎”
> 2026-03-19 抓取：FRED graph CSV
- `DGS10`: 2026-03-16 = 4.23
- `T10Y2Y`: 2026-03-17 = 0.52
- `VIXCLS`: 2026-03-17 = 22.37
- `DCOILWTICO`: latest available = 2026-03-09 = 94.65

解读：
- 当前并非典型低波动、低利率的舒适 risk-on 环境；
- 而且不同宏观字段的 `as_of` 本身不一致，说明若没有 freshness / event-aware gate，系统很容易把“旧油价+新波动率+新利率”混读成一个单一 regime。

---

## 三、动作

### 3.1 对当前主线的建议定位
- **保留现状**：把当前系统定义为“已完成主干收口、可进入结果验收/下一轮规划”的版本
- **不要夸大**：暂时不要把它描述成“已具备宏观交易/宏观 veto 完整能力”的系统
- **停止扫参线**：认同关闭 P0-2b 参数扫参线，把资源转去做 regime/veto/gate

### 3.2 下一轮建议路线（按先后）

#### Step 1：把 macro 从 overlay 提升到 veto
新增：`macro_event_gate` + `macro_cross_asset_veto`
- 输出到：`forbidden_set` / `forbidden_reason` / `forbidden_codes_triggered`
- 接入点：
  - `strategy_templates.py` 先产生 trace
  - `risk_gate.py` 再消费 hard veto

#### Step 2：冻结一套最小 macro evidence schema
建议最小字段：
- `indicator`
- `value`
- `as_of`
- `release_time`
- `surprise`（若是事件型数据）
- `freshness`
- `source`
- `regime_implication`

原则：
- 不先扩很多 provider
- 先固定真值字段，保证回测/实盘/报告口径一致

#### Step 3：用 3 段宏观窗口做 acceptance，而不是继续全局扫参
建议固定窗口：
1. `2020-04 ~ 2021-12`：流动性修复 / risk-on
2. `2022-03 ~ 2022-10`：通胀冲击 / 紧缩 risk-off
3. `2023-11 ~ 2024-07`：通胀回落 / AI risk-on

验收问题不再是“参数最优吗”，而是：
- 在三种制度下，哪些信号还能用？
- 哪些 regime 下必须 block / reduce size？
- 什么时候策略表现只是 regime beta，而不是可迁移 edge？

### 3.3 给老板的短口径
> 当前交易系统主干已经收口完成，但宏观层仍主要是“overlay”而非“刹车”。下一轮最值得做的不是继续调参，而是补上三类 gate：事件型 macro shock、利率/波动/汇率跨资产 veto、中国传导 veto。这样系统在 regime 切换时会更稳，失真也更少。

---

## 四、路径
- `/Users/study/.openclaw/workspace-macro/knowledge/daily/2026-03-19/trading-strategy-mainline-macro-final-review.md`
