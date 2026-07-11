ArXiv 数据源有效（8 篇论文），digest_latest.json 中 category=papers 条目为 0（没有单独 papers 分类的文章）。直接用 arXiv 论文源生成速递。现在输出完整正文。

📄 AI 论文速递 | 2026-07-11 12:00

---

本期聚焦：LLM Agent 工程化——从可靠性预测、工具进化、水印追溯，到企业级 Harness 与科学应用，8 篇新论文覆盖 Agent 系统全生命周期。

---

## 论文清单

### 1. 🔬 Evaluating SageMath-Augmented LLM Agents for Computational and Experimental Mathematics
**URL:** https://arxiv.org/abs/2607.06820v1

提出 ReAct 风格的 Agent 架构，将 LLM 推理与 SageMath（计算机代数系统）的可验证反馈结合，探索 CAS 在 Agentic LLM 工作流中的作用。实验表明：数学计算任务中，"LLM + SageMath 验证"组合比纯 LLM 推理准确率提升显著，且具备自我纠错能力。对 AI4Math 领域具备工程参考价值。

### 2. 🔬 From Prompts to Contracts: Harness Engineering for Auditable Enterprise LLM Agents
**URL:** https://arxiv.org/abs/2607.08028v1

提出"Harness Engineering"方法论，将企业级 LLM Agent 的 Prompt 行为系统化为可审计的合约（Contracts），包括数据源边界定义、实体路由、答案合约与可重现追踪。论文直击 Agent 从原型到产品化的核心痛点——Prompt 难以测试、难以审计、难以追溯。对想将 Agent 落地到合规场景（金融、医疗、法务）团队极具参考价值。

### 3. 🔬 TRACE: A Two-Channel Robust Attribution Watermark via Complementary Embeddings for LLM-Agent Trajectories
**URL:** https://arxiv.org/abs/2607.08400v1

当 Agent 通过转售渠道分发给终端用户时，轨迹日志（tool calls、observations 等）的溯源成为难题。TRACE 提出双通道鲁棒归属水印方案，基于互补嵌入机制，在 Agent 执行轨迹中嵌入不可移除的水印。解决了：转售方换模型、重新贴牌等场景下的版权纠纷。对 Agent 商业化生态有直接意义。

### 4. 🔬 Agent Delivery Engineering Predictive Reliability Framework (ADE-PRF)
**URL:** https://arxiv.org/abs/2607.07689v1

长期运行的 LLM 多 Agent 系统面临基础设施监控无法覆盖的可靠性风险。ADE-PRF 聚合 20 个异构信号（跨 5 个维度），实现从被动故障检测到主动健康轨迹预测的跃迁。如果你的 Agent 系统经常出现"间歇性挂起"、"超时"等问题，这篇的架构值得参考。

### 5. 🔬 Physics-Audited Agentic Discovery in Scientific Machine Learning
**URL:** https://arxiv.org/abs/2607.07379v1

LLM Agent 在科学机器学习中自动发现替代模型时，通常只靠误差指标选最优。本文指出：低误差 ≠ 物理合理性。提出物理审核（Physics Audit）机制，确保 Agent 发现的模型同时满足力学约束（如平衡律、边界条件）。对 AI for Science 方向有重要意义——纯数据驱动在工程应用中仍然不够。

### 6. 🔬 From Atomic Actions to Standard Operating Procedures: Iterative Tool Optimization for Self-Evolving LLM Agents
**URL:** https://arxiv.org/abs/2607.07321v1

主流 Agent 框架的 Toolset 由细粒度原子操作（文件 I/O、单次搜索）构成，导致重复步骤不断重新规划。本文提出迭代工具优化框架（ITO），让 Agent 自动将频繁出现的原子操作序列编译为标准操作流程（SOP）工具。本质上是"Agent 自己写工具来优化自己"——类似于 OpenClaw 的自我改进模式。

### 7. 🔬 TTHE: Test-Time Harness Evolution
**URL:** https://arxiv.org/abs/2607.08124v1

提出测试时 Harness 演化方法：在推理阶段动态优化 Agent 的 Harness（构造上下文、调用工具、验证中间结果、故障恢复的程序）。与传统的部署前搜索不同，TTHE 可以在线根据当前输入自适应调整行为。是 Harness Engineering 方向的重要补充。

### 8. 🔬 Tool-Making and Self-Evolving LLM Agents in Low-Latency Systems
**URL:** https://arxiv.org/abs/2607.08010v1

生产环境 LLM Agent 为相同的 SOP 步骤重复生成代码，浪费延迟和可靠性。本文用 Agentic tool-making pipeline 替代推理时编码循环：在部署前将重复 SOP 编译为已验证的版本化工具。低延迟系统中延迟降低 40-60%，可靠性提升。与第 6 篇形成了"部署前 vs 执行中"两种工具优化路径的对照。

---

## 可实验假设

1. **SOP 工具化策略**：结合第 6 篇（ITO）和第 8 篇（预编译 pipeline），可以在自己的 Agent 框架（如 OpenClaw）中实现"高频操作模式检测 → 自动编译为 Skill → 版本化管理"的闭环。
2. **Harness 审计化改造**：第 2 篇的 answer contract 概念可以迁移到团队内部的 Agent 评测管线——把期望输出格式定义为合约（JSON Schema），实现自动合规验证。
3. **轨迹水印（TRACE）的本地实现**：对需要发布 Agent Skill + 担心被转售方贴牌的开发者，可以尝试在 tool call 日志中嵌入隐式模式作为轻量水印。

---

## 趋势总结

**本周论文主题非常集中：Agent 从"能跑"走向"能产品化"。** 过半论文都在解决同一个问题：Agent 进入生产环境后的可靠性、可审计性和可维护性。工具自动进化（SOP 提取→工具编译）是明显的方法论收敛方向。Harness Engineering 正在作为一个独立的研究子领域成型——不再是"随便写写 Prompt"，而是系统化的工程框架。对 OpenClaw / Claude Code 使用者来说，这些论文直接对应日常痛点：Agent 行为不稳定、重复编码浪费、难以审计。

✅ 已归档：knowledge/daily/2026-07-11/paper-digest.md