# tradability / implementation risk 外部样本卡（A 股 trading system）

日期：2026-03-19  
用途：只服务当前 trading system 下一阶段的最小 implementation risk gate，不扩成行业综述。

---

## 结论

### 一、A 股 research system 最常见、且最容易把回测做“假漂亮”的实现风险

按对当前系统的破坏性排序，我建议优先盯 6 类：

| 风险 | 典型错误 | 为什么危险 | 今天能否纳入最小 gate |
|---|---|---|---|
| 1. 未来函数 / 同 bar 成交作弊 | 用当日收盘生成信号，又按当日收盘成交；或调参后回看同一测试段 | 最容易直接抬高胜率和收益 | **P0：能** |
| 2. 复权口径不一致 | 特征用前复权、成交/收益用原始价，或混用不同数据源复权规则 | 收益、阈值、止损和容量判断都会失真 | **P0：能** |
| 3. 可交易性约束缺失 | 忽略停牌、涨跌停、一字板、零成交、低成交额 | 会把“买不到/卖不掉”的单子算成已成交 | **P0：能** |
| 4. 滑点 / 手续费近似过轻 | 不计印花税、最小佣金、滑点过低 | 小频率或小票策略最容易被虚增 | **P0：能** |
| 5. 容量 / 成交额约束缺失 | 单日下单额占成交额过高 | 纸面收益无法落地，尤其 basket 扩大后 | **P0：能** |
| 6. Universe 非 PIT / survivorship bias | 用今天成分股回测过去 | 会系统性高估策略稳定性 | **P0：能（至少做披露/降级）** |

### 二、今天就能纳入最小 gate 的 5 条

#### Gate-1：信号时点 / 成交时点硬隔离
- 若信号用 **当日收盘后** 数据生成，则成交价只能取：
  - **次日开盘**，或
  - 次日 VWAP / 下一个 bar
- 禁止“当日 close 算信号 + 当日 close 成交”这种默认回测捷径，除非系统里有明确的 **收盘后下单并可在收盘集合竞价成交** 口径，且单独标注。

#### Gate-2：复权口径统一
- 先固定全系统只允许一种研究口径：
  - **研究特征**：前复权/统一 adjusted 口径
  - **成交与真实收益核算**：要么全部走统一 adjusted 口径并保证映射一致，要么显式回到原始价 + corporate actions 现金流处理
- 至少做一条检查：**同一只股票在除权除息日前后，特征、成交价、收益率口径必须一致**。

#### Gate-3：最小 tradability 过滤
- 当天不能成交的单子，不能算成交：
  - 停牌
  - 跌停卖不出 / 涨停买不进
  - 当前 bar 无成交量 / inactive
  - 成交额过低
- 若暂时没有完整盘口，最低也要先做：
  - `suspended == false`
  - `not limit-locked`
  - `volume > 0`
  - `turnover >= 最低阈值`

#### Gate-4：成本模型不能留空
- 股票最小要有：
  - 佣金
  - 卖出印花税
  - 最小佣金（如 5 元）
  - 基础滑点
- 如果今天没有更细模型，先用**保守固定近似**，不要先裸跑。

#### Gate-5：容量约束先做粗门槛
- 任何单笔/单日目标成交额，不能超过当日成交额的一定比例
- 今天先上一个粗阈值就有价值，比如：
  - 单标的目标成交额 ≤ 当日成交额的 **2%~5%**（更保守）
  - 若是 bar 级回测，可额外加 `≤ bar volume 的 5%~10%`
- 这不是为了精确，而是先过滤掉明显不可实现的结果。

### 三、今天不必一次做完，但应列入 P1 的项
- A 股板块差异化涨跌停规则：主板 10%、ST 5%、创业板/科创板 20%、新股/特殊阶段例外
- T+1、100 股整数手、分红配股/送转现金流处理
- 开盘/收盘集合竞价与盘中撮合差异
- 更细的容量模型：按 ADV、盘口冲击、分层滑点而不是固定 bps
- 更严格的 PIT 基本面 / 指数成分 / 风格分类口径

---

## 证据

### 1) Qlib：明确把 PIT、benchmark、成本、涨跌停阈值放进研究/回测主流程

- Qlib 的 PIT 文档明确写到：**财务数据若直接用“最新版本”回测历史，会发生 data leakage**；PIT 数据库的目标是“保证历史时点只看到当时版本的数据”。  
  来源：  
  https://github.com/microsoft/qlib/blob/main/docs/advanced/PIT.rst

- Qlib 的数据文档明确提醒：它的数据是 **adjusted** 的，而且不同数据源的复权方式可能不同；Qlib 甚至明确说可用 `$factor` 还原原始交易价格（如 `$close / $factor`）。这直接说明：**复权口径混用是现实风险，不是理论问题**。  
  来源：  
  https://github.com/microsoft/qlib/blob/main/docs/component/data.rst

- Qlib 的 benchmark workflow 示例把这些 implementation risk 显式配置化了：
  - `benchmark: SH000300`
  - `fit_start_time / fit_end_time`
  - `train / valid / test`
  - `exchange_kwargs.limit_threshold: 0.095`
  - `deal_price: close`
  - `open_cost: 0.0005`
  - `close_cost: 0.0015`
  - `min_cost: 5`

  这说明成熟框架不会把“成本/涨跌停/训练边界”留给口头约定，而是直接做成 backtest config 的一部分。  
  来源：  
  https://github.com/microsoft/qlib/blob/main/examples/benchmarks/LightGBM/workflow_config_lightgbm_Alpha158.yaml

### 2) RQAlpha：最贴近 A 股撮合现实，直接提供了最小 tradability gate 的样板

- RQAlpha 的 `sys_simulation` 模块把下列项都做成显式开关：
  - `matching_type`: `current_bar` / `next_bar` / `vwap`
  - `price_limit`: 涨跌停限制
  - `volume_limit`: 成交量限制
  - `volume_percent`: 单 bar / tick 成交量占比
  - `slippage_model`
  - `slippage`
  - `inactive_limit`: 当前 bar 无成交量不撮合

  这几乎就是我们今天最小 gate 的直接外部样板。  
  来源：  
  https://github.com/ricequant/rqalpha/blob/master/rqalpha/mod/rqalpha_mod_sys_simulation/README.rst

- 更关键的是，RQAlpha 明确写了：`signal` 模式下，订单**不进行撮合，直接产生交易**；这适合屏蔽订单细节，但也意味着它**不适合拿来做 implementation risk 验收**。这条对我们当前阶段尤其重要：**不要用“信号直成交”的捷径去验证 tradability**。  
  来源：  
  https://github.com/ricequant/rqalpha/blob/master/rqalpha/mod/rqalpha_mod_sys_simulation/README.rst

- RQAlpha 的交易税费模块又单独把这些成本项显式配置化：
  - `cn_stock_min_commission = 5`
  - `commission_multiplier`
  - `tax_multiplier`

  说明税费不是“事后乘个系数就行”的附属物，而应成为系统级参数。  
  来源：  
  https://github.com/ricequant/rqalpha/blob/master/rqalpha/mod/rqalpha_mod_sys_transaction_cost/README.rst

### 3) LEAN：虽然不是 A 股原生，但它把“不要用当前 universe 回测过去”说得非常清楚

- LEAN 的 survivorship bias 文档明确指出：如果你用**当前指数成分股回测过去**，通常会高估表现，因为历史中差股票已经被剔除了。  
  来源：  
  https://github.com/QuantConnect/Documentation/blob/master/03%20Writing%20Algorithms/01%20Key%20Concepts/10%20Research%20Guide/08%20Survivorship%20Bias.html

- LEAN 的 look-ahead bias 文档明确指出：不能用同一段历史先优化参数、再拿同一段历史验证；应使用更早数据优化、更新数据测试，或做 walk-forward。  
  来源：  
  https://github.com/QuantConnect/Documentation/blob/master/03%20Writing%20Algorithms/30%20Optimization/01%20Parameters/05%20Look-Ahead%20Bias.html

- LEAN 还明确要求显式 `SetBenchmark` / `set_benchmark`。这对我们当前阶段的意义是：**implementation risk gate 不该只盯成交，还要保证策略对 benchmark 的超额收益是同口径算的**。  
  来源：  
  https://github.com/QuantConnect/Documentation/blob/master/03%20Writing%20Algorithms/02%20Initialization/11%20Set%20Benchmark.html

---

## 动作

### 今日 P0（今天就应该进系统或进入验证脚本）

1. **补 execution timing gate**  
   - 明确：信号时间戳、下单时间戳、成交价格字段  
   - 默认回测口径先统一为：`T日收盘生成信号 -> T+1 开盘/next bar 成交`

2. **补最小 tradability gate**  
   - `停牌过滤 + 涨跌停过滤 + volume>0 + 最低成交额过滤`

3. **补最小成本模型**  
   - 股票佣金 + 卖出印花税 + 最小佣金 + 固定滑点
   - 如果没有更好参数，先用保守口径，不要裸收益

4. **补容量粗门槛**  
   - 单日目标成交额 / bar 成交量占比先卡住，过滤明显不可能成交的组合

5. **补 PIT / 非 PIT 标签**  
   - 如果当前 universe 不是历史动态成分，输出必须明确标 `非 PIT，仅用于方向筛选`

### 今日 P1（本轮主干通了之后尽快补）

1. **板块化涨跌停规则**：主板 / ST / 创业板 / 科创板分开建模  
2. **lot size + T+1**：A 股整数手与当日买入不可卖出约束  
3. **复权一致性自动检查**：抽样校验 feature / fill / return 三套价格口径是否一致  
4. **容量从粗门槛升级为分层模型**：按 ADV、波动率、流动性分桶给不同冲击成本  
5. **PIT universe / 基本面正式化**：指数成分、行业分类、财报口径改为历史时点可得

### 一句话收口

**今天最值得马上落地的，不是更复杂的 alpha，而是先把“能不能买到、卖掉、按什么价成交、成本怎么算、是否偷看未来”这几道门关上。对当前 trading system，implementation risk 的收益修正价值，短期内很可能高于继续堆新信号。**
