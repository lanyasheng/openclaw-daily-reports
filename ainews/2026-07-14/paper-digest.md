# 📄 AI 论文速递 | 2026-07-14 12:00

> 来源：ArXiv | 覆盖周期：2026-07-07 ~ 2026-07-09

---

## 📑 论文清单

### 1. Evaluating SageMath-Augmented LLM Agents for Computational and Experimental Mathematics
**🔗** https://arxiv.org/abs/2607.06820v1

提出了一种结合**LLM 推理 + SageMath 可验证反馈**的 ReAct 式智能体框架，用于计算与实验数学。自动形式化与定理证明已有大量探索，但 Agent + 计算机代数系统（CAS）的结合此前关注不足。本文填补了这一空白，证明 CAS 作为外部验证器可显著提升数学推理的可靠性。

**影响评估**：对数学研究自动化有直接参考价值。结合 Agent + CAS 的范式值得关注，尤其是对需要严格验证的科学计算场景。

---

### 2. From Prompts to Contracts: Harness Engineering for Auditable Enterprise LLM Agents
**🔗** https://arxiv.org/abs/2607.08028v1

企业级 LLM 应用常从 prompt + RAG 原型起步，但产品化需要**源码边界、实体路由、应答合约和可复现追踪**。本文提出"Harness Engineering"（控制框架工程）方法，将 agent 行为从脆弱的 prompt 驱动升级为合约化、可审计的执行体系。

**影响评估**：如果你在将 Agent 原型推向生产，这篇论文的核心思路（合约化、可审计、Harness 设计）是必不可少的参考。与当前 MCP/A2A 标准推进方向一致。

---

### 3. TRACE: A Two-Channel Robust Attribution Watermark via Complementary Embeddings for LLM-Agent Trajectories
**🔗** https://arxiv.org/abs/2607.08400v1

LLM Agent 通过转售商到达最终用户时，溯源争议频发。TRACE 提出一种**基于互补嵌入的双通道鲁棒溯源水印**，嵌入在工具调用链日志（而非推理文本）中，即使转售方换模型或重新 branding 也能验证归属。

**影响评估**：Agent 溯源是商业落地中容易忽视的关键问题。TRACE 为 Agent 服务商提供了实用的归属保护方案，特别适合 API 中台和 agent marketplace 场景。

---

### 4. Agent Delivery Engineering Predictive Reliability Framework
**🔗** https://arxiv.org/abs/2607.07689v1

长时延多智能体系统面临基础设施监控无法感知的可靠性风险。ADE-PRF 提出**预测式可靠性框架**，聚合 20 个异构信号在 5 个维度上进行健康轨迹预测，实现从被动故障检测到主动退化预测的升级。

**影响评估**：多 Agent 系统在生产环境中的可靠性是当前最头疼的问题之一。这篇论文提供了系统化的可操作框架，值得生产级 Agent 平台的架构师阅读。

---

### 5. Physics-Audited Agentic Discovery in Scientific Machine Learning
**🔗** https://arxiv.org/abs/2607.07379v1

在科学机器学习中，LLM Agent 可自动发现替代模型并依据误差指标选取最优。但低误差 ≠ 物理合理。本文提出**物理审核机制**，确保 Agent 选出的模型不仅数值精度高，还满足力学守恒律等物理约束。

**影响评估**：对 AI for Science 领域有重要指导意义——纯统计指标不能保证物理可信。任何涉及物理仿真的 Agent 方案都应参考此思路。

---

### 6. From Atomic Actions to Standard Operating Procedures: Iterative Tool Optimization for Self-Evolving LLM Agents
**🔗** https://arxiv.org/abs/2607.07321v1

现有 Agent 框架依赖静态工具集（细粒度原子动作），导致 Agent 需在推理时反复组合基础操作，造成延迟和可靠性损失。本文提出**迭代式工具优化**方法，将重复出现的原子操作序列自动编译为标准操作规程（SOP），实现工具的自动生成与版本化管理。

**影响评估**：这与生产中"Agent 自己造工具"的需求高度契合。如果使用 Claude Code/OpenClaw 等 Agent 平台，SOP 范式可显著降低延迟和 token 消耗。

---

### 7. TTHE: Test-Time Harness Evolution
**🔗** https://arxiv.org/abs/2607.08124v1

LLM Agent 的行为不仅取决于底层模型，还取决于**harness（控制框架）**——即构造上下文、调用工具、验证中间结果和恢复失败的执行程序。现有方法在部署前优化 harness，本文提出**测试时 Harness 进化**，在推理阶段动态调整 harness 结构以适应任务变化。

**影响评估**：与第 2 篇（Harness Engineering）形成姊妹篇。推理时自适应 harness 比部署前静态优化更灵活，适合复杂多变的任务场景。

---

### 8. Tool-Making and Self-Evolving LLM Agents in Low-Latency Systems
**🔗** https://arxiv.org/abs/2607.08010v1

生产环境中的 LLM Agent 在每个请求上都重复生成相同过程的代码，造成延迟和可靠性浪费。本文提出**Agentic Tool-Making 流水线**：在部署前将重复的 SOP 步骤编译为经验证、版本化的工具，运行时直接调用而非现场编码。

**影响评估**：低延迟系统下的工具预编译策略非常实用。对于将 Agent 推向实时交互场景（如客服、编程助手）的开发团队，这是必读文献。

---

## 🧪 可实验假设

1. **Harness Engineering 优于 Prompt Engineering** — 假设在生产级 Agent 中，用合约化 Harness（含审计追踪、源边界、应答合约）替代纯 Prompt 驱动的架构，可使可审计性和故障恢复能力提升 50%+。可在现有 MCP 框架下对比实现。

2. **工具自进化可降低延迟 30%+** — 假设将反复出现的原子操作序列自动编译为 SOP 工具（而非推理时逐行编码），在多轮交互场景下可减少延迟 30-50%。可在 OpenClaw 或其他 Agent 框架中通过拦截工具调用链验证。

3. **Agent 水印溯源在更换模型后仍有效** — 假设 TRACE 的双通道嵌入水印在转售商将模型从 GPT-4 替换为 Claude 4 后，仍能以 >90% 准确率识别原始开发者。可在开源 Agent 框架中复现测试。

---

## 📊 趋势总结

本期论文高度聚焦于 **Agent 工程化成熟度**——从 reliability framework、harness engineering、test-time adaptation 到 tool evolution 和 attribution watermark，说明 LLM Agent 正从 demo/原型阶段快速迈向生产级工程化。值得注意的是，用于科学计算的 Agent 也出现了物理审核等质量保障机制。整体信号：**Agent 架构的"下半场"是可靠性、可审计性和自演化能力**。

✅ 已归档：knowledge/daily/2026-07-14/paper-digest.md
