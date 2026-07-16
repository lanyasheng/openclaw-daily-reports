# AI 哨兵心跳摘要 | 2026-05-27 08:40 CST

## 数据源
- RSS 聚合：101 源，最近 1 天，抓取 800 条，582 条有效标题/URL；87/101 源成功。
- Web search：当前 provider 返回 404，未可用；采用 RSS + 关键文章 web_fetch 交叉补充。

## 判断
- 是否需要紧急推送：是，偏安全预警。
- 是否通知 trading：是，OpenRouter 估值、AI 芯片 ETF、physical AI 融资、AI infra 漏洞。
- 是否通知 macro：是，ECB 对 AI 私募信贷风险、AI 治理/政策相关动态。

## 重点事件
1. **AI infra 安全：Starlette/FastAPI/vLLM/LiteLLM/MCP 生态 CVE-2026-48710 “BadHost”**
   - Ars 报道称漏洞影响 Starlette < 1.0.1，并波及 FastAPI、vLLM、LiteLLM、TGI、OpenAI-shim proxies、MCP servers、agent harnesses、eval dashboards、model-management UIs 等。
   - 风险：HTTP Host header 绕过 path-based authorization；可能导致 MCP/agent 服务敏感凭据暴露。
   - 建议：若运行相关服务，优先检查 Starlette 版本并升级至 >= 1.0.1；同时确认边界防火墙/反代 Host header 校验。
   - 来源：https://arstechnica.com/information-technology/2026/05/millions-of-ai-agents-imperiled-by-critical-vulnerability-in-open-source-package/

2. **AWS AgentCore 连发 agentic commerce / LangGraph / Strands / monitoring 相关技术文章**
   - 指向企业级 agent 基础设施、支付与可观测性加速落地。
   - 来源：AWS ML Blog 多篇 2026-05-26 更新。

3. **OpenRouter 估值升至 $1.3B**
   - 投资/平台层信号：AI 模型路由和推理聚合平台继续被资本重估。
   - 来源：https://techcrunch.com/2026/05/26/openrouter-more-than-doubles-valuation-to-1-3b-in-a-year/

4. **ECB 提醒 private-credit fueled AI boom 或构成金融系统风险**
   - 宏观风险信号：AI 投资热潮与私募信贷杠杆联动开始进入央行风险监控。
   - 来源：https://www.ft.com/content/7ecdff9f-4f3a-40dd-b984-9860097dd083

5. **AI 治理/政策与人才流动信号**
   - Wired：Pope Leo XIV encyclical discusses AI power; Vatican invited Anthropic/Christopher Olah.
   - The Decoder：China reportedly requires top AI researchers permission before leaving the country.

## 协作动作
- 已向 trading heartbeat session 发送 AI 投资/市场信号与安全风险 handoff。
- 已向 macro heartbeat session 发送 AI 宏观/政策风险 handoff。
- macro 已确认纳入今日风险边界，并归档：`workspace-macro/knowledge/daily/2026-05-27/0843-ai-policy-risk-boundary.md`。核心口径：AI 强趋势仍在，但金融稳定与人才管制风险边界上升，用于约束 AI/半导体追高叙事。

## 归档
- RSS JSON: `knowledge/daily/2026-05-27-heartbeat-0840-rss.json`
- RSS log: `knowledge/daily/2026-05-27-heartbeat-0840-rss.log`
