# AI 哨兵心跳归档 — 2026-05-27 15:40 CST

## 检查范围
- 已读取 `/Users/study/.openclaw/workspace-ainews/HEARTBEAT.md`
- RSS 聚合：`rss_aggregator.py --category all --days 1 --limit 80 --json`
- 结果：815 items；87/101 sources 成功；部分源 404/308/500（Google AI Blog、Meta AI Blog、HuggingFace Daily Papers、Semafor AI 等）

## 需要关注的重大 AI/技术动态

### 1. AI Agent 生态安全：Starlette/FastAPI/MCP 相关 BadHost 漏洞
- 来源：Ars Technica
- 标题：Millions of AI agents imperiled by critical vulnerability in open source package
- URL：https://arstechnica.com/information-technology/2026/05/millions-of-ai-agents-imperiled-by-critical-vulnerability-in-open-source-package/
- 要点：CVE-2026-48710 / BadHost 影响 Starlette 1.0.1 之前版本，波及 FastAPI、vLLM、LiteLLM、MCP servers、agent harnesses、eval dashboards、model-management UIs 等 Python AI 工具链；HTTP Host header 可绕过路径授权，可能暴露凭证与第三方账户访问。
- 本机快速检查：当前 `python3` 环境未安装 starlette/fastapi/vllm/litellm；其他虚拟环境或容器未检查。
- 判断：具备紧急推送价值（安全、agent 基建、可执行修复）。

### 2. AI Infra 投融资：OpenRouter Series B / $1.3B 估值
- 来源：TechCrunch
- 标题：OpenRouter more than doubles valuation to $1.3B in a year
- URL：https://techcrunch.com/2026/05/26/openrouter-more-than-doubles-valuation-to-1-3b-in-a-year/
- 要点：OpenRouter 获 $113M Series B，CapitalG 领投，NYT 报道 post-money 估值约 $1.3B；用户 800 万、月处理 100T tokens，约 6 个月前周 5T tokens 增至当前周 25T tokens。
- 判断：AI 推理/多模型路由/agent 基建投资热度强，需同步 trading。

### 3. AI 地缘/政策：China AI talent travel curbs
- 来源：The Decoder（引用 Bloomberg）
- 标题：China reportedly now requires top AI researchers to get permission before leaving the country
- URL：https://the-decoder.com/china-reportedly-now-requires-top-ai-researchers-to-get-permission-before-leaving-the-country/
- 要点：中国 reportedly 要求 Alibaba、DeepSeek 等私营企业关键 AI 项目人才出境需官方许可；与 AI 芯片自主、技术安全、人才流动管控相关。
- 判断：宏观/地缘/产业政策信号，需同步 macro。

### 4. AWS AgentCore / agentic commerce
- 来源：AWS ML Blog
- 标题组：AgentCore payments、Bedrock AgentCore + LangGraph、Strands Agents + NVIDIA NIM 等多篇
- 判断：企业 agent 基建、agentic commerce 落地信号增强，纳入日报但不单独紧急推送。

## 协作信号
- trading：OpenRouter 融资与 AI infra 估值扩张；BadHost 漏洞对 AI agent/MCP 生态短期风险。
- macro：China AI talent travel curbs 属于 AI 地缘/政策信号。

## 结论
- 有需要关注事项，不回复 HEARTBEAT_OK。
- 已归档本次心跳检查。
