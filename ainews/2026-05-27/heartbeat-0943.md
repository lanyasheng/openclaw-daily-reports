# AI 哨兵心跳归档 — 2026-05-27 09:43 CST

## 检查范围
- RSS 聚合：101 源，87/101 成功，近 1 天共 584 条。
- GitHub Trending AI/ML：成功。
- arXiv 脚本：触发超时/429，未作为本轮判断依据。

## 值得关注
1. **Starlette/FastAPI 生态 BadHost 漏洞**（Ars Technica）
   - CVE-2026-48710 / BadHost，影响 Starlette 1.0.1 之前版本；FastAPI、vLLM、LiteLLM、MCP servers、agent harnesses、OpenAI-shim proxies 等可能受影响。
   - 风险：Host header 绕过路径授权，可能暴露 MCP/agent server 的外部服务凭据与敏感数据。
   - 建议：若本机或业务中有公网/内网可访问的 FastAPI/Starlette/MCP 服务，应优先排查版本和边界防护。
   - Source: https://arstechnica.com/information-technology/2026/05/millions-of-ai-agents-imperiled-by-critical-vulnerability-in-open-source-package/

2. **AWS AgentCore Payments / AgentCore 系列动态**（AWS ML Blog）
   - AgentCore payments 进入 preview，支持代理访问付费外部服务、微支付/稳定币等 agentic commerce 基础设施。
   - 方向判断：Agent 平台从“工具调用/编排”继续向“交易/结算基础设施”延伸。
   - Source: https://aws.amazon.com/blogs/machine-learning/technical-deep-dive-agentcore-payments-and-innovation-in-agentic-commerce/

3. **OpenRouter 融资与 AI Gateway 趋势**（TechCrunch）
   - OpenRouter 完成 $113M Series B，据报估值约 $1.3B；月处理 100T tokens，近 6 个月周 token 量 5x。
   - 投资含义：多模型路由、AI Gateway、推理成本优化继续升温。
   - Source: https://techcrunch.com/2026/05/26/openrouter-more-than-doubles-valuation-to-1-3b-in-a-year/

4. **宏观/政策相关**（RSS）
   - FT：ECB 警告 private-credit fuelled AI boom 可能带来金融系统风险。
   - Wired/CBC/HN：Pope Leo 首份 AI encyclical 强调监管、透明度与技术权力集中。
   - The Decoder：中国据报要求顶级 AI 研究人员出国前需获批。

5. **半导体/算力链**（RSS）
   - NVIDIA Vera CPU benchmark/AI factory CPU 叙事。
   - Reuters/HN：Qualcomm 与 ByteDance AI chip deal 报道。
   - Korea Times/HN：SK hynix iHBM self-cooling chips。
   - FT：DRAM/AI excitement 推升 memory ETF。

## 协作动作
- 已准备通知 trading：OpenRouter、AWS AgentCore payments、半导体/算力链、BadHost 对 AI infra 风险的交易/产业线索。
- 已准备通知 macro：ECB AI boom 金融稳定风险、AI 监管/政策、跨境 AI 人才流动限制。

## 紧急推送判断
- **安全项 BadHost** 具备较高优先级，若用户维护 FastAPI/Starlette/MCP/agent 服务，建议单独排查。
- 其余为趋势/政策/投资线索，先交给 macro/trading 消化，不直接打扰用户。