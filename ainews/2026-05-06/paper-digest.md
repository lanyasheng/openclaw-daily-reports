# 📄 AI 论文速递 | 2026-05-06 12:00

## 论文清单

### 1. Feedback-Normalized Developer Memory for RL Coding Agents: A Safety-Gated MCP Architecture
- **作者:** Mehmet Iscan
- **分类:** cs.SE, cs.CL, cs.LG
- **链接:** https://arxiv.org/abs/2605.01567v1
- **解读:** 针对 LLM 编程 Agent 在长周期软件工程任务中的持久记忆问题，提出了一种基于安全门控 MCP 架构的反馈归一化开发者记忆机制。传统静态向量存储或通用 RAG 不足以支撑强化学习驱动的编码 Agent，本文通过反馈归一化让 Agent 在仓库、终端、测试和执行轨迹之间形成可演化的记忆回路。对 MCP 生态和 Agent 编程工具有直接参考价值。
- **影响:** ⭐⭐⭐⭐ MCP + Agent 记忆架构的交叉创新

### 2. Model-First Reasoning LLM Agents: Reducing Hallucinations through Explicit Problem Modeling
- **作者:** Annu Rana, Gaurav Kumar
- **分类:** cs.AI
- **链接:** https://arxiv.org/abs/2512.14474v1
- **解读:** LLM 在多步规划任务中约束违反率高、解决方案不一致，CoT 和 ReAct 依赖隐式状态追踪。本文提出"模型优先"推理框架，要求 Agent 在推理前显式构建问题模型（约束、变量、目标），从而显著降低幻觉率。对需要高可靠性的 Agent 规划场景有启发。
- **影响:** ⭐⭐⭐⭐ 多步规划 Agent 的可靠性提升路径

### 3. An Agent-Oriented Pluggable Experience-RAG Skill for Experience-Driven Retrieval Strategy Orchestration
- **作者:** Dutao Zhang, Tian Liao
- **分类:** cs.AI
- **链接:** https://arxiv.org/abs/2605.03989v1
- **解读:** 现有 RAG 系统假设单一检索管线适用于所有任务，但事实问答、多跳推理和科学验证的检索偏好差异很大。本文提出 Experience-RAG Skill，一种面向 Agent 的可插拔经验驱动检索策略编排框架，让 Agent 根据历史经验动态选择最优检索策略。与 OpenClaw Skill 体系思路高度契合。
- **影响:** ⭐⭐⭐⭐ RAG 策略编排的 Agent 化方向

### 4. Sheaf-Theoretic Planning: A Categorical Foundation for Resilient Multi-Agent Autonomous Systems
- **作者:** Manuel Hernández, Eduardo Sánchez-Soto
- **分类:** cs.AI
- **链接:** https://arxiv.org/abs/2605.01879v1
- **解读:** 将层论（Sheaf Theory）和范畴论引入多 Agent 自主系统的规划基础。传统 MAS 依赖单一逻辑框架，难以应对物理世界的随机性和对抗性。本文用范畴论构建弹性规划基础，使 Agent 能在不确定性环境中实现局部一致性的全局协调。理论深度高，适合长期跟踪。
- **影响:** ⭐⭐⭐ 理论性强，短期落地有限但方向值得关注

### 5. NORA: A Harness-Engineered Autonomous Research Agent for End-to-End Spatial Data Science
- **作者:** Bing Zhou 等
- **分类:** cs.AI
- **链接:** https://arxiv.org/abs/2605.02092v1
- **解读:** 现有自主研究 Agent 大多是领域无关的，缺乏空间数据科学所需的专门推理、方法选择和数据采集能力。NORA 是一个面向空间数据科学的端到端自主研究 Agent，通过 Harness 工程实现方法自动选择和空间数据获取。展示了 Agent 在垂直科研领域深度定制的可能性。
- **影响:** ⭐⭐⭐ 垂直领域 Agent 的标杆案例

### 6. FeedbackLLM: Metadata-Driven Multi-Agentic Language-Agnostic Test Case Generator
- **作者:** Kushal Jasti 等
- **分类:** cs.SE, cs.LG
- **链接:** https://arxiv.org/abs/2605.01264v1
- **解读:** 传统测试用例生成依赖人工且计算开销大。FeedbackLLM 提出元数据驱动的多 Agent 架构，通过演化提示和覆盖率反馈自动生成语言无关的测试用例。多 Agent 协作 + 覆盖率闭环的设计，对 CI/CD 中的自动化测试环节有直接应用价值。
- **影响:** ⭐⭐⭐ 测试自动化的多 Agent 实践

### 7. TDD Governance for Multi-Agent Code Generation via Prompt Engineering
- **作者:** Tarlan Hasanli 等
- **分类:** cs.SE, cs.AI
- **链接:** https://arxiv.org/abs/2604.26615v1
- **解读:** LLM 加速开发但缺乏纪律性约束。本文探索通过提示工程将 TDD（测试驱动开发）的 Red-Green-Refactor 流程注入多 Agent 代码生成管线，实现开发纪律的治理。对 Agent 编程的质量控制提供了可操作的框架。
- **影响:** ⭐⭐⭐ TDD + Agent 编程的结合思路

---

## 可实验假设

1. **MCP + 持久记忆 = 编程 Agent 的下一个分水岭。** Paper 1 提出的反馈归一化记忆架构，如果与 OpenClaw Skill 体系结合，可能显著提升 Agent 在长周期编码任务中的稳定性。
2. **显式问题建模可替代部分 CoT 开销。** Paper 2 表明，让 Agent 先建模再推理，可能比无约束的 CoT 更高效且幻觉更少——值得在复杂规划任务中 A/B 测试。
3. **RAG 策略编排需要 Agent 化而非硬编码。** Paper 3 的 Experience-RAG 思路与 OpenClaw 的 Skill 动态路由机制天然互补，可尝试将检索策略作为可插拔 Skill 管理。

## 趋势总结

本周论文的核心信号是 **Agent 工程化**——从记忆管理（Paper 1）、问题建模（Paper 2）、RAG 策略编排（Paper 3）到测试治理（Paper 6/7），论文不再关注"Agent 能不能做"，而是聚焦"如何让 Agent 可靠地做"。同时，MCP 架构正在从协议层向记忆/治理层延伸，成为 Agent 系统的底层基础设施。理论层面，范畴论/层论（Paper 4）的引入暗示多 Agent 系统正在寻找更严谨的数学基础。
