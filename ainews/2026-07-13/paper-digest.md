📄 AI 论文速递 | 2026-07-13 12:00

---

## 1. Evaluating SageMath-Augmented LLM Agents for Computational and Experimental Mathematics
**URL:** https://arxiv.org/abs/2607.06820v1

提出一种 ReAct 式 agentic 框架，将 LLM 推理与 SageMath 计算机代数系统（CAS）的验证反馈相结合，用于计算和实验数学问题求解。实验表明，LLM + CAS 闭环可以显著提升符号计算、代数操作等任务的准确率。对想用 agent 做科学计算的团队有直接参考价值。

## 2. From Prompts to Contracts: Harness Engineering for Auditable Enterprise LLM Agents
**URL:** https://arxiv.org/abs/2607.08028v1

提出"工具链工程（Harness Engineering）"方法：通过引入数据源边界、实体路由、答案合约和可复现追踪，将企业级 LLM 应用从原型阶段的 prompt 驱动升级为可审计的生产系统。直击企业落地的合规痛点——不止调 prompt，还要管日志、合约和溯源。

## 3. TRACE: A Two-Channel Robust Attribution Watermark via Complementary Embeddings for LLM-Agent Trajectories
**URL:** https://arxiv.org/abs/2607.08400v1

针对 LLM agent 被第三方转售/换模型后的归属争议，提出双通道鲁棒水印方案，通过对轨迹日志（工具调用链、执行记录，非模型推理层）嵌入互补指纹来实现归属证明。解决了 agent 生态中"谁做的"溯源难题，对 agent marketplace 安全有重要启发。

## 4. Agent Delivery Engineering Predictive Reliability Framework
**URL:** https://arxiv.org/abs/2607.07689v1

提出 ADE 预测可靠性框架（ADE-PRF），汇聚 20 个异构信号实现长时序多 agent 系统的健康轨迹预测，从被动故障检测转向主动寿命预测。对维护大规模多 agent 生产集群的团队是难得的方法论参考。

## 5. Physics-Audited Agentic Discovery in Scientific Machine Learning
**URL:** https://arxiv.org/abs/2607.07379v1

针对 agentic SciML 中单纯依赖误差评分可能选出物理不可行模型的问题，引入物理启发的审计机制，确保代理发现的替代模型既拟合数据又满足力学/物理约束。将 physics-informed 理念从模型层扩展到 agent 决策层。

## 6. From Atomic Actions to Standard Operating Procedures: Iterative Tool Optimization for Self-Evolving LLM Agents
**URL:** https://arxiv.org/abs/2607.07321v1

提出让 LLM agent 从细粒度原子动作（如单次文件读写）自动编译为可复用的 SOP（标准操作程序）工具，并通过迭代优化扩展工具集，实现 agent 的自我进化。对想要提升 agent 工具复用率和执行效率的开发者是实操性很强的思路。

## 7. TTHE: Test-Time Harness Evolution
**URL:** https://arxiv.org/abs/2607.08124v1

核心洞察：agent 的行为不只由底层模型决定，更由"harness"（构造上下文、调用工具、验证结果的执行程序）决定。提出在测试阶段让 harness 自我进化，替代传统的预部署搜索式优化。对 agent 框架设计者有直接的架构启发：把 harness 当作可演化的一等公民。

## 8. Tool-Making and Self-Evolving LLM Agents in Low-Latency Systems
**URL:** https://arxiv.org/abs/2607.08010v1

针对低延迟生产环境中 agent 每次请求重复生成代码的浪费，提出预编译工具制造管线：将 SOP 步骤提前编译为验证过的版本化工具，大幅降低延迟和可靠性风险。与第 6 篇形成互补，一个侧重工具自动发现，一个侧重低延迟部署。

---

### 可实验假设

1. **Harness Engineering 是 agent 产品的下一个瓶颈**：第 2、7 篇从不同角度指向同一个方向——当模型能力足够时，agent 的上限将由外围编排系统（harness）决定。可以实验性地在自己的 agent 框架中引入可追踪的合约式 harness 设计，对比传统 prompt 驱动的方案在可审计性和失败恢复上的差异。

2. **Agent 工具的自动化构建 vs 手动编写**：第 6 篇的 SOP 自动编译 + 第 8 篇的预编译部署，两条路径可以组合为一个 pipeline：agent 从历史执行中自动发现高频重复步骤 → 编译为版本化工具 → 预先部署。值得在 OpenClaw 的 skill/tool 体系中尝试类似的"执行日志 → 新 skill"反馈回路。

3. **Agent 水印与归属追踪**：TRACE（第 3 篇）为 agent 生态的 provenance 问题提供了一种技术路线。如果运行 agent marketplace 或有 agent 输出的版权保护需求，可在 trajectory 层嵌入轻量级指纹，测试水印在模型替换、精简后的鲁棒性。

### 趋势总结

本期论文高度聚焦 agent 工具链工程化方向，harness 设计、SOP 自动编译、可靠性预测、physics-audit、归属水印——几乎所有工作都不是在提升某个模型的精度，而是在解决 agent 在生产环境中的工程可信问题。这与行业从"模型能力竞争"向"基础设施竞争"的迁移一致。值得注意的还有"self-evolving agent"概念被多篇论文同时推进，可能成为下一波 agent 框架的关键范式。
