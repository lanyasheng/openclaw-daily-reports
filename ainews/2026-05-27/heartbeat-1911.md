# AI 哨兵心跳归档｜2026-05-27 19:11 CST

## 数据源检查
- RSS 聚合：101 sources，86 成功，1278 条结果（days=1, limit=200）。
- 主要告警：发现 AI agent / Python ASGI 生态安全风险；发现 AI 投资与宏观风险信号。

## P0 / 需要关注
### BadHost / CVE-2026-48710：Starlette Host Header Auth Bypass
- 来源：Ars Technica、Lobsters/BadHost
- 影响：Starlette < 1.0.1；FastAPI 生态；vLLM、LiteLLM、TGI、OpenAI-shim proxies、MCP servers、agent harnesses、eval dashboards、model-management UIs 等可能受影响。
- 风险：Host header 注入可绕过 path-based authorization；MCP/agent 服务可能暴露第三方凭证与敏感数据。
- 判断：安全紧急程度高；若本机或任何外网服务运行 Starlette/FastAPI/MCP/LLM gateway，应优先排查并升级 Starlette >= 1.0.1。
- URL: https://arstechnica.com/information-technology/2026/05/millions-of-ai-agents-imperiled-by-critical-vulnerability-in-open-source-package/
- URL: https://badhost.org

## 协作信号
### trading
- OpenRouter Series B：融资 $113M，估值 $1.3B；6 个月用量 5x。AI routing / multi-model infra 仍是高增长主线。
- URL: https://techcrunch.com/2026/05/26/openrouter-more-than-doubles-valuation-to-1-3b-in-a-year/

### macro
- ECB 警告 private-credit fueled AI boom 可能带来金融系统风险。
- URL: https://www.ft.com/content/7ecdff9f-4f3a-40dd-b984-9860097dd083
- 中国 AI/监管相关：FT 称中国升级 AI 监控网络；The Decoder 称中国顶级 AI 研究员出境需审批。
- URL: https://www.ft.com/content/f8fa4739-4359-4720-af77-9be1e8370f82
- URL: https://the-decoder.com/china-reportedly-now-requires-top-ai-researchers-to-get-permission-before-leaving-the-country/

## 其他关注
- DeepSWE：新的 agentic coding benchmark，被社交源转发关注。
- Vatican / Pope AI encyclical：AI 权力集中、技术伦理与 Anthropic 参与引发讨论。
