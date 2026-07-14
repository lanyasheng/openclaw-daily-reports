Deltas vs daily-check.md (2026-07-14 07:50 CST)

| Key | Value |
|-----|-------|
| time | 2026-07-14 17:08 CST |
| web_search | ❌ 持续不可用（自 10:19 起无法使用） |
| web_fetch | ❌ 华尔街见闻/路透/BBC 均 fetch failed |
| data_outage_hours | ~7 小时（无任何外部数据源可用） |
| china_trade_june | ❌ 仍未获取（10:00 发布，数据不可得） |
| a_shares_close | 🚫 无法获取（A 股已 15:00 收盘，但无数据） |
| kospi_close | 🚫 无法获取 |
| brent_crude | 🚫 无法获取实时报价 |
| halluz_strait | 🚫 无法获取最新通航状态 |
| next_check_focus | CTA：今晚 22:00 鲍威尔听证（仍需外部数据源） |

### 状态说明
- **数据源全面断裂已持续 7 小时：** 自 10:19 CST 第一次确认 web_search 故障以来，始终未能恢复。
- **17:08 CST 所有数据点仍为不可得：** 中国 6 月贸易数据、A 股收盘、韩股走势、油价、黄金均无法获取。daily-check 的"事件驱动推断框架"是唯一可用参考。
- **22:00 CST 鲍威尔听证是今天最关键事件。** 如果 web_search/web_fetch 仍不可用，将无法实时跟踪。届时需要尝试备用数据获取方案。

### ⏰ 22:00 CST 鲍威尔听证关注要点
- 开场陈述是否提及中东/霍尔木兹局势
- 油价冲击是否影响通胀前景判断
- 是否暗示条件性政策调整
- 市场即时反应（如果数据源恢复）
