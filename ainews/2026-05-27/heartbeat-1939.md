# AI 哨兵心跳归档 — 2026-05-27 19:39 CST

## 检查范围
- RSS 聚合：101 个源，87/101 成功，797 条 1 日内条目。
- GitHub Trending AI/ML：已检查。
- ArXiv agent/LLM 论文：已检查 Top 10。
- 对重点条目进行了网页复核：Ars Technica、TechCrunch、The Decoder。

## 需要关注

### 1. 安全：Starlette/FastAPI 生态 BadHost 漏洞
- Ars Technica 报道：Starlette 漏洞 CVE-2026-48710 / BadHost，影响 Starlette 1.0.1 前版本；Starlette 是 FastAPI 基础组件，vLLM、LiteLLM 等也可能受影响。
- 风险：HTTP Host header 单字符注入绕过 path-based authorization；MCP/agent 服务若暴露在公网且防火墙配置不当，可能泄露第三方凭据。
- 链接：https://arstechnica.com/information-technology/2026/05/millions-of-ai-agents-imperiled-by-critical-vulnerability-in-open-source-package/
- 判断：属于重大技术安全动态，建议进入用户简报。

### 2. 投资/产业：OpenRouter 估值升至约 $1.3B
- TechCrunch 报道：OpenRouter 融资 $113M Series B，CapitalG 领投；NYT 称 post-money 估值约 $1.3B。
- 逻辑：企业多模型路由、推理成本优化、agent 工作流推动 AI gateway 需求。
- 链接：https://techcrunch.com/2026/05/26/openrouter-more-than-doubles-valuation-to-1-3b-in-a-year/
- 已通知 trading。

### 3. 宏观/政策：中国 AI 人才出境许可传闻
- The Decoder 引 Bloomberg：据称中国要求阿里、DeepSeek 等私营部门关键 AI 人才出境前获得官方许可。
- 逻辑：AI 人才、技术外流与国产 AI 供应链保护进一步政策化。
- 链接：https://the-decoder.com/china-reportedly-now-requires-top-ai-researchers-to-get-permission-before-leaving-the-country/
- 已通知 macro。

### 4. Agent 基础设施：AWS AgentCore 密集发布
- AWS ML Blog 同日发布 AgentCore payments、LangGraph serverless multi-agent、Strands + NVIDIA NIM + Bedrock AgentCore 等内容。
- 逻辑：agentic commerce、企业 agent 编排、可观测性与支付成为云厂商争夺点。
- 代表链接：https://aws.amazon.com/blogs/machine-learning/technical-deep-dive-agentcore-payments-and-innovation-in-agentic-commerce/

### 5. GitHub 趋势
- Lum1104/Understand-Anything：代码知识图谱，+4,697 stars/day。
- anthropics/knowledge-work-plugins：Claude Cowork 知识工作插件。
- microsoft/agent-governance-toolkit：AI Agent Governance Toolkit，覆盖 OWASP Agentic Top 10。
- shiyu-coder/Kronos：金融市场基础模型。

## 协作动作
- trading：已发送 OpenRouter / DRAM ETF / AWS AgentCore / NVIDIA Vera 主题线索。
- macro：已发送中国 AI 人才出境许可、AI 监控网络升级、数据中心政策阻力线索。

## 结论
本次心跳发现安全、投资、宏观政策三类需要关注信号；已归档并完成协作通知。