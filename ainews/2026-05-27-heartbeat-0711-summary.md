# AI 哨兵心跳摘要 — 2026-05-27 07:11 CST

数据源：RSS 聚合 101 源，归档：`knowledge/daily/2026-05-27-heartbeat-0711-rss.json`；日志：`knowledge/daily/2026-05-27-heartbeat-0711-rss.log`。

## 需关注

1. **BadHost / Starlette 漏洞影响 AI Agent/MCP 生态**
   - 来源：Ars Technica
   - 要点：Starlette < 1.0.1 存在 CVE-2026-48710（BadHost），单字符 Host header 绕过路径授权；FastAPI、vLLM、LiteLLM、TGI、OpenAI-shim 代理、MCP servers、agent harnesses、eval dashboards 等可能受影响。Starlette 已发布 1.0.1。
   - URL: https://arstechnica.com/information-technology/2026/05/millions-of-ai-agents-imperiled-by-critical-vulnerability-in-open-source-package/
   - 判断：安全类重大动态，值得紧急提示。

2. **OpenRouter 完成 1.13 亿美元 B 轮，估值约 13 亿美元**
   - 来源：TechCrunch
   - 要点：CapitalG 领投；OpenRouter 称月处理 100T tokens，约 8M 全球用户，过去 6 个月 weekly tokens 约 5x。
   - URL: https://techcrunch.com/2026/05/26/openrouter-more-than-doubles-valuation-to-1-3b-in-a-year/
   - 判断：AI 基础设施/模型路由商业化信号，已转 trading。

3. **中国据报扩大顶级 AI 人才出境审批**
   - 来源：The Decoder / Bloomberg 引述
   - 要点：Alibaba、DeepSeek 等私营企业战略 AI 项目人员出境需官方批准；与 AI 技术安全、人才流动、芯片/软件自主化相关。
   - URL: https://the-decoder.com/china-reportedly-now-requires-top-ai-researchers-to-get-permission-before-leaving-the-country/
   - 判断：AI 政策/地缘科技信号，已转 macro。

4. **ECB 警示 private-credit fuelled AI boom 对金融系统构成风险**
   - 来源：Financial Times
   - URL: https://www.ft.com/content/7ecdff9f-4f3a-40dd-b984-9860097dd083
   - 判断：AI 资本开支/信用周期风险，已转 macro。

## 其他值得留意
- FT：Chipmaker ETF 因 AI 热潮快速达到 100 亿美元估值。
- FT：ByteDance 为 AI 团队发特殊股票以防挖角。
- FT：AI 招聘工具导致“clear racial disparities”。
- Wired：教皇首份 AI 通谕关注技术权力集中，Anthropic 受邀参与发布。
