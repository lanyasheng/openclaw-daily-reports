# 📄 AI 论文速递 | 2026-05-07 12:00

## 论文清单

### 1. Feedback-Normalized Developer Memory for Reinforcement-Learning Coding Agents: A Safety-Gated MCP Architecture
- **作者:** Mehmet Iscan
- **分类:** cs.SE, cs.CL, cs.LG
- **链接:** https://arxiv.org/abs/2605.01567v1
- **评分:** 17
- **中文解读:** 针对 LLM 编码 Agent 在长周期软件工程任务中的记忆管理问题，本文提出了一种基于反馈归一化的开发者记忆机制，结合 MCP（Model Context Protocol）架构实现安全门控。核心观点是：静态向量存储或通用 RAG 无法支撑强化学习场景下的 Agent 记忆需求，需要引入反馈信号来动态调整记忆权重。对 Agent 开发者和 MCP 生态有直接参考价值。

### 2. Model-First Reasoning LLM Agents: Reducing Hallucinations through Explicit Problem Modeling
- **作者:** Annu Rana, Gaurav Kumar
- **分类:** cs.AI
- **链接:** https://arxiv.org/abs/2512.14474v1
- **评分:** 14
- **中文解读:** LLM 在多步规划任务中约束违反率高、解决方案不一致，本文提出"模型优先"的推理方法——在推理前显式构建问题模型（类似传统 AI 规划中的状态表示），而非依赖 CoT/ReAct 的隐式状态追踪。实验表明显式建模可显著降低幻觉率。对 Agent 规划可靠性提升有启发意义。

### 3. An Agent-Oriented Pluggable Experience-RAG Skill for Experience-Driven Retrieval Strategy Orchestration
- **作者:** Dutao Zhang, Tian Liao
- **分类:** cs.AI
- **链接:** https://arxiv.org/abs/2605.03989v1
- **评分:** 12
- **中文解读:** 不同任务（事实问答、多跳推理、科学验证）对检索策略的偏好差异很大，但现有 RAG 系统通常使用固定检索管线。本文提出 Experience-RAG Skill，一种面向 Agent 的可插拔经验技能，能够根据任务类型动态编排检索策略。核心贡献是"经验驱动"的检索策略选择机制，与 OpenClaw 的 Skill 架构理念高度契合。

### 4. Sheaf-Theoretic Planning: A Categorical Foundation for Resilient Multi-Agent Autonomous Systems
- **作者:** Manuel Hernández, Eduardo Sánchez-Soto
- **分类:** cs.AI
- **链接:** https://arxiv.org/abs/2605.01879v1
- **评分:** 12
- **中文解读:** 将层论（Sheaf Theory）和范畴论引入多 Agent 自主系统的规划框架，为随机和对抗性环境中的多 Agent 协同提供数学基础。传统 MAS 框架依赖单一逻辑系统，而本文的层论方法允许局部一致性聚合为全局一致性。理论深度较高，适合多 Agent 系统架构研究者。

### 5. NORA: A Harness-Engineered Autonomous Research Agent for End-to-End Spatial Data Science
- **作者:** Bing Zhou, Xiao Huang, Huan Ning, Qiusheng Wu, Diya Li
- **分类:** cs.AI
- **链接:** https://arxiv.org/abs/2605.02092v1
- **评分:** 12
- **中文解读:** 现有自主研究 Agent 大多是领域无关的，缺乏专业推理和数据采集能力。NORA 是一个面向空间数据科学的端到端自主研究 Agent，通过 Harness 工程实现专业方法选择、数据采集和分析推理。展示了领域专用 Agent 相比通用 Agent 在垂直领域的优势。

### 6. FeedbackLLM: Metadata driven Multi-Agentic Language Agnostic Test Case Generator with Evolving Prompt and Coverage Feedback
- **作者:** Kushal Jasti 等 5 人
- **分类:** cs.SE, cs.LG
- **链接:** https://arxiv.org/abs/2605.01264v1
- **评分:** 12
- **中文解读:** 传统测试用例生成依赖人工且计算开销大。FeedbackLLM 利用元数据驱动的多 Agent 架构，结合覆盖率反馈和动态 Prompt 演化，实现语言无关的自动化测试生成。多 Agent 协作 + 反馈闭环的设计模式对软件工程自动化有参考价值。

### 7. TDD Governance for Multi-Agent Code Generation via Prompt Engineering
- **作者:** Tarlan Hasanli 等 5 人（图尔库大学）
- **分类:** cs.SE, cs.AI
- **链接:** https://arxiv.org/abs/2604.26615v1
- **评分:** 12
- **中文解读:** LLM 在代码生成中表现出不稳定性和纪律性不足，本文探索通过 Prompt 工程将 TDD（测试驱动开发）的 Red-Green-Refactor 流程注入多 Agent 代码生成管线。核心贡献是"治理"概念——用结构化 Prompt 约束 LLM 的开发纪律，而非放任自由生成。

### 8. MEMSAD: Gradient-Coupled Anomaly Detection for Memory Poisoning in Retrieval-Augmented Agents
- **作者:** Ishrith Gowda
- **分类:** cs.CR, cs.AI, cs.LG
- **链接:** https://arxiv.org/abs/2605.03482v1
- **评分:** 11
- **中文解读:** 持久化外部记忆使 LLM Agent 能够跨会话保持上下文，但其安全性质尚未被正式刻画。本文将记忆投毒攻击形式化为 Stackelberg 博弈，提出 MEMSAD——一种基于梯度耦合的异常检测方法，覆盖三类攻击。随着 RAG Agent 的普及，记忆安全将成为关键基础设施问题。

---

## 可实验假设

1. **经验驱动 RAG 策略编排**（论文 #3）可直接映射到 OpenClaw Skill 架构：将不同检索策略封装为 Skill，由 Agent 根据任务类型动态选择，可能比固定 RAG 管线提升 15-20% 的检索准确率。

2. **TDD 治理 Prompt 模板**（论文 #7）可转化为 Claude Code / Codex 的系统指令增强：在代码生成任务中注入 Red-Green-Refactor 约束，观察生成代码的测试覆盖率和缺陷率变化。

3. **记忆投毒检测**（论文 #8）的梯度耦合方法可集成到持久化 Agent 的记忆写入管线中：每次写入外部记忆前进行异常检测，防止恶意注入污染 Agent 知识库。

## 趋势总结

本周论文呈现三个明显趋势：① **Agent 安全与可靠性**成为核心议题，从记忆投毒检测到 TDD 治理，研究焦点从"让 Agent 能做"转向"让 Agent 做得安全"；② **领域专用 Agent** 开始挑战通用 Agent 范式，NORA 在空间数据科学领域的实践表明垂直领域 Agent 仍有巨大空间；③ **RAG 架构持续进化**，从固定管线走向经验驱动的动态编排，Skill/能力可插拔成为新方向。

---

*生成时间: 2026-05-07 12:00 CST | 数据源: ArXiv API (8 篇)*
