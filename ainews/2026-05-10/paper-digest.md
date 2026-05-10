# 📄 AI 论文速递 | 2026-05-10 08:42

## 论文清单

### 1. Feedback-Normalized Developer Memory for Reinforcement-Learning Coding Agents: A Safety-Gated MCP Architecture
- **作者:** Mehmet Iscan
- **分类:** cs.SE, cs.CL, cs.LG
- **链接:** https://arxiv.org/abs/2605.01567v1
- **解读:** 本文提出了一种基于 MCP（Model Context Protocol）的安全门控记忆架构，用于强化学习驱动的编码 Agent。核心思路是：静态向量存储或通用 RAG 不足以支撑长程软件工程任务中的持续记忆需求，需要引入反馈归一化（Feedback-Normalized）机制来动态调整 Agent 对历史代码、测试、执行轨迹的记忆权重。安全门控层则防止 Agent 在探索过程中积累有毒记忆。这对 Agent 编程工具的长期可靠性有直接参考价值。
- **影响:** ⭐⭐⭐⭐ 与 MCP + Agent 编码直接相关，架构思路可借鉴到 OpenClaw 等 Agent 框架的记忆管理。

### 2. Model-First Reasoning LLM Agents: Reducing Hallucinations through Explicit Problem Modeling
- **作者:** Annu Rana, Gaurav Kumar
- **分类:** cs.AI
- **链接:** https://arxiv.org/abs/2512.14474v1
- **解读:** 针对 LLM 在多步规划任务中频繁违反约束、产生幻觉的问题，本文提出"模型优先"推理范式。与 Chain-of-Thought 和 ReAct 依赖隐式状态追踪不同，该方法要求 Agent 在推理前先构建显式的问题模型（类似约束规划中的形式化建模），再基于模型进行搜索和推理。实验显示该方法显著降低了约束违反率。
- **影响:** ⭐⭐⭐⭐ 对复杂 Agent 工作流的可靠性提升有直接意义，显式建模思路可融入多步任务规划。

### 3. Safactory: A Scalable Agent Factory for Trustworthy Autonomous Intelligence
- **作者:** Xinquan Chen, Zhenyun Yin, Shan He, Bin Huang, Shanzhe Lei
- **分类:** cs.AI, cs.DC
- **链接:** https://arxiv.org/abs/2605.06230v1
- **解读:** Safactory 是一个面向可信自主智能体的可扩展 Agent 工厂框架。随着大模型从对话助手演进为自主 Agent，长程决策、工具使用和真实环境交互成为核心挑战。Safactory 试图将评估、数据管理和 Agent 进化整合到一个统一平台中，解决现有 agentic 基础设施碎片化的问题。
- **影响:** ⭐⭐⭐⭐ 统一的 Agent 工厂概念与 OpenClaw 的 Skill/Agent 生态有共鸣，值得关注其架构设计。

### 4. STALE: Can LLM Agents Know When Their Memories Are No Longer Valid?
- **作者:** Hanxiang Chao, Yihan Bai, Rui Sheng, Tianle Li, Yushi Sun
- **分类:** cs.CL
- **链接:** https://arxiv.org/abs/2605.06527v1
- **解读:** STALE 基准测试聚焦于一个被忽视的问题：LLM Agent 能否感知自身记忆已过期？当前大多数记忆基准仅衡量静态事实检索，忽略了当新证据出现时 Agent 修正已存储信念的能力。本文识别出这一关键失败模式并构建了专门的评测基准，揭示了现有 Agent 在记忆更新方面的严重不足。
- **影响:** ⭐⭐⭐⭐⭐ 记忆时效性是 Agent 系统的核心挑战，该基准对评估和改进 Agent 记忆管理具有重要参考价值。

### 5. LatentRAG: Latent Reasoning and Retrieval for Efficient Agentic RAG
- **作者:** Yijia Zheng, Marcel Worring
- **分类:** cs.CL, cs.LG
- **链接:** https://arxiv.org/abs/2605.06285v1
- **解读:** LatentRAG 将 RAG 从单步检索扩展到多步 Agent 式检索，但在每一步中引入了"潜在推理"（Latent Reasoning）机制——Agent 在内部推理后才决定是否检索、检索什么、以及如何整合多轮检索结果。相比传统 Agentic RAG，该方法在保持多步推理能力的同时显著降低了 token 消耗和延迟。
- **影响:** ⭐⭐⭐⭐ 对高效 Agentic RAG 的优化方向有启发，潜在推理机制值得深入研究。

### 6. Event-Causal RAG: A Retrieval-Augmented Generation Framework for Long Video Reasoning in Complex Scenarios
- **作者:** Peizheng Yan, Yu Zhao, Liang Xie, Juntong Qi, Mingming Wang
- **分类:** cs.AI, cs.CV
- **链接:** https://arxiv.org/abs/2605.06185v1
- **解读:** 本文针对超长视频理解场景提出 Event-Causal RAG 框架。现有大视觉语言模型在短视频上表现良好，但在需要跨长时间跨度保持连贯记忆并推断因果依赖的超长视频推理中表现不足。该框架通过事件因果图结构组织检索内容，使模型能够在极长视频中维持推理一致性。
- **影响:** ⭐⭐⭐ 视频理解方向的前沿探索，对多模态 Agent 的长期记忆机制有借鉴意义。

### 7. Architecture Matters: Comparing RAG Systems under Knowledge Base Poisoning
- **作者:** Samuel Korn
- **分类:** cs.CR, cs.CL, cs.LG
- **链接:** https://arxiv.org/abs/2605.05632v1
- **解读:** 本文系统性地比较了不同 RAG 架构在知识库投毒攻击下的鲁棒性。现有攻击评估几乎都针对简单的 retrieve-then-generate 管道，而本文扩展到多 Agent 辩论、Agentic 检索等复杂架构。研究发现：更复杂的架构（如多 Agent 辩论）在某些投毒场景下反而比简单管道更脆弱，因为攻击可以沿着推理链传播。
- **影响:** ⭐⭐⭐⭐⭐ RAG 安全是生产部署的关键问题，该研究为架构选型提供了重要参考——复杂度不等于安全性。

### 8. MAS-Algorithm: A Workflow for Solving Algorithmic Programming Problems with a Multi-Agent System
- **作者:** Yuliang Xu, Xiang Xu, Yao Wan, Hu Wei, Tong Jia
- **分类:** cs.AI, cs.SE
- **链接:** https://arxiv.org/abs/2605.05949v1
- **解读:** MAS-Algorithm 提出了一种多 Agent 协作解决算法编程问题的工作流。与依赖单一模型能力的方案不同，该方法将算法问题分解为多个子任务，由不同角色的 Agent 分别负责问题分析、算法设计、代码实现和测试验证。实验表明多 Agent 协作在结构化推理任务上优于单模型方案。
- **影响:** ⭐⭐⭐ 多 Agent 协作编程的具体实践，角色分工思路可借鉴到编码 Agent 的设计中。

---

## 可实验假设

1. **记忆时效性检测可作为 Agent 自我监控的核心指标。** STALE 基准揭示了 Agent 在记忆更新上的系统性失败，若能在 Agent 框架中集成类似 STALE 的自检机制，Agent 的长期可靠性将显著提升。

2. **RAG 架构的复杂度与安全性的关系可能呈倒 U 型。** Architecture Matters 的研究暗示：简单管道在投毒攻击下可能比复杂多 Agent 架构更鲁棒。这意味着在生产环境中，RAG 的安全性评估需要与架构选择同步进行，而非事后补救。

3. **显式问题建模是降低 Agent 幻觉的关键路径。** Model-First Reasoning 表明，让 Agent 在推理前构建显式问题模型（而非直接生成）能显著降低约束违反率。这一思路可推广到更广泛的 Agent 任务规划场景。

## 趋势总结

本周论文的核心主题高度聚焦于 **Agent 记忆管理** 和 **RAG 架构演进**。STALE（记忆时效性）、Feedback-Normalized Memory（安全门控记忆）和 LatentRAG（潜在推理检索）三条线索共同指向一个方向：Agent 系统的核心瓶颈正在从"模型能力"转向"记忆与检索的可靠性"。同时，Architecture Matters 提醒我们：在 RAG 安全问题上，架构选择比模型选择更关键。
