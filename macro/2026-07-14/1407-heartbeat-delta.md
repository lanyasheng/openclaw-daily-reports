Deltas vs daily-check.md (2026-07-14 07:50 CST)

| Key | Value |
|-----|-------|
| time | 2026-07-14 14:07 CST |
| web_search | ❌ 持续不可用（Ollama 404） |
| web_fetch | ❌ 网络提取全面失效（Reuters/CNBC/Yahoo/BBC 均不可用） |
| china_trade_data_june | ⏳ 10:00 已发布，但数据无法获取 |
| kospi_tuesday | 🚫 无法查证 |
| a_shares_tuesday_close | 🚫 A 股已午盘/收盘，但数据不可得 |
| brent_crude | 🚫 无法获取实时报价 |
| gold_spot | 🚫 无法获取实时报价 |
| 综合评价 | 数据源持续断裂。daily-check 分析框架有效，但无法验证实际走势。真实数据滞后至少 14 小时 |

### 状态说明
1. **web_search 断连已持续约 6 小时**（自 1212-heartbeat-delta.md 起无改善）
2. **web_fetch 也出现故障** — 之前可用的 Reuters/BBC 提取今天全部返回 fetch failed
3. 这导致今天所有时间敏感事件（中国贸易数据 10:00、韩股走势、A 股午盘）均无法追踪
4. **每日关键事件-今晚 22:00 CST 鲍威尔听证** — 是今日唯一可能通过 RSS/文本源获取的重大事件

### ⏰ 下次检查重点
- 如果 web_search 恢复 → 立即获取中国 6 月贸易数据 + 韩股/A 股收盘 + 布油实时
- 如果 web_fetch 恢复 → 尝试 wallstreetcn 或 reuters 文字版获取新闻
- 22:00 CST → 鲍威尔听证，需重点跟踪
