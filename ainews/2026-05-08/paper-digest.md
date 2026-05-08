# 📄 AI 论文速递 | 2026-05-08 12:00

---

## 论文清单

### 1. Feedback-Normalized Developer Memory for Reinforcement-Learning Coding Agents: A Safety-Gated MCP Architecture
**作者:** Mehmet Iscan | **分类:** cs.SE, cs.CL, cs.LG | **发表于:** 2026-05-02
**链接:** https://arxiv.org/abs/2605.01567v1

**解读:** 针对 LLM 编码 Agent 在长周期软件开发中的记忆管理问题，提出了一种基于 MCP（Model Context Protocol）的安全门控记忆架构。论文指出静态向量存储或通用 RAG 无法支撑强化学习编码 Agent 的动态反馈需求，设计了 feedback-normalized 记忆更新机制，让 Agent 能根据执行反馈动态修正记忆，同时通过安全门控防止记忆污染。对 Agent 长期记忆管理有重要参考价值。

**影响评估:** ⭐⭐⭐⭐ MCP 生态 + Agent 记忆管理，直接关联当前编码 Agent 的核心痛点。

---

### 2. Model-First Reasoning LLM Agents: Reducing Hallucinations through Explicit Problem Modeling
**作者:** Annu Rana, Gaurav Kumar | **分类:** cs.AI | **发表于:** 2025-12-16
**链接:** https://arxiv.org/abs/2512.14474v1

**解读:** 当前 LLM 在多步规划任务中幻觉率居高不下，CoT 和 ReAct 等方法依赖隐式状态跟踪，缺乏显式问题建模。本文提出"Model-First"范式——先构建显式问题模型（类似 AI 经典规划中的状态空间表示），再进行推理决策。实验表明该方法显著降低了约束违反率和解决方案不一致性，为 Agent 规划提供了一个新思路。

**影响评估:** ⭐⭐⭐⭐ 将经典 AI 规划思想引入 LLM Agent，思路有启发性。

---

### 3. Safactory: A Scalable Agent Factory for Trustworthy Autonomous Intelligence
**作者:** Xinquan Chen, Zhenyun Yin, Shan He, Bin Huang, Shanzhe Lei | **分类:** cs.AI, cs.DC | **发表于:** 2026-05-07
**链接:** https://arxiv.org/abs/2605.06230v1

**解读:** 面向大模型从对话助手向自主 Agent 演进的趋势，Safactory 提出了一个可扩展的 Agent 工厂框架。当前 agentic 基础设施在评估、数据管理和 Agent 演化方面高度碎片化，Safactory 尝试统一这三个维度，提供从数据准备、训练、评估到持续演化的全流程管线。重点强调"可信"——包括安全性、可审计性和可控性。

**影响评估:** ⭐⭐⭐⭐⭐ 一站式 Agent 工厂框架，如果落地成熟可能成为 Agent 开发基础设施。

---

### 4. STALE: Can LLM Agents Know When Their Memories Are No Longer Valid?
**作者:** Hanxiang Chao, Yihan Bai, Rui Sheng, Tianle Li, Yushi Sun | **分类:** cs.CL | **发表于:** 2026-05-07
**链接:** https://arxiv.org/abs/2605.06527v1

**解读:** 当前 LLM Agent 的记忆基准测试主要衡量静态事实检索能力，忽略了 Agent 在新证据出现时更新已有信念的能力。本文识别出这一关键缺陷，构建了 STALE 基准——测试 Agent 识别记忆过期并主动修正的能力。实验发现主流 LLM Agent 在此任务上表现极差，暴露了长期记忆管理中的重大盲区。

**影响评估:** ⭐⭐⭐⭐⭐ 切中 Agent 记忆管理的核心痛点，基准工具对社区有实用价值。

---

### 5. LatentRAG: Latent Reasoning and Retrieval for Efficient Agentic RAG
**作者:** Yijia Zheng, Marcel Worring | **分类:** cs.CL, cs.LG | **发表于:** 2026-05-07
**链接:** https://arxiv.org/abs/2605.06285v1

**解读:** 单步 RAG 适用于简单问答，但在复杂问题上力不从心；Agentic RAG 通过多步检索提升能力，但代价高昂。LatentRAG 提出在隐空间中进行推理和检索的联合优化——Agent 先在隐空间做推理规划，再按需触发检索，减少不必要的检索调用。实验显示在保持回答质量的同时显著降低了检索开销。

**影响评估:** ⭐⭐⭐⭐ RAG 效率优化方向，对降低 Agent 运行成本有直接意义。

---

### 6. Event-Causal RAG: A Retrieval-Augmented Generation Framework for Long Video Reasoning in Complex Scenarios
**作者:** Peizheng Yan, Yu Zhao, Liang Xie, Juntong Qi, Mingming Wang | **分类:** cs.AI, cs.CV | **发表于:** 2026-05-07
**链接:** https://arxiv.org/abs/2605.06185v1

**解读:** 当前视觉语言模型在短/中视频理解上表现良好，但在超长视频推理中无法保持连贯记忆和跨时间因果推断。Event-Causal RAG 将事件因果关系建模引入 RAG 框架，通过事件图结构组织视频内容，使模型能在超长视频中维持因果链推理。为视频理解 + RAG 的交叉方向提供了新范式。

**影响评估:** ⭐⭐⭐ 视频 + RAG 交叉方向，场景特定但思路新颖。

---

### 7. Architecture Matters: Comparing RAG Systems under Knowledge Base Poisoning
**作者:** Samuel Korn | **分类:** cs.CR, cs.CL, cs.LG | **发表于:** 2026-05-07
**链接:** https://arxiv.org/abs/2605.05632v1

**解读:** RAG 系统面临知识库投毒攻击的威胁，但现有研究几乎只针对 vanilla retrieve-then-generate 管线。本文系统评估了多种高级 RAG 架构（多 Agent 辩论、agentic retrieval 等）在知识库投毒下的鲁棒性。核心发现：架构设计对安全性影响巨大——多 Agent 辩论架构在投毒场景下反而比单 Agent 更脆弱，因为攻击信息会在辩论中被放大。

**影响评估:** ⭐⭐⭐⭐⭐ RAG 安全性的系统性研究，结论反直觉且对生产部署有直接指导意义。

---

### 8. MAS-Algorithm: A Workflow for Solving Algorithmic Programming Problems with a Multi-Agent System
**作者:** Yuliang Xu, Xiang Xu, Yao Wan, Hu Wei, Tong Jia | **分类:** cs.AI, cs.SE | **发表于:** 2026-05-07
**链接:** https://arxiv.org/abs/2605.05949v1

**解读:** 算法编程问题是结构化推理的严格测试床。现有方法主要依赖模型中心策略（架构改进、提示工程等），本文提出多 Agent 协作工作流——不同 Agent 分别承担问题理解、方案设计、代码实现、测试验证等角色，通过结构化工作流协同解决算法题。实验在多个编程竞赛基准上验证了多 Agent 方法的优势。

**影响评估:** ⭐⭐⭐⭐ 多 Agent 编码协作的又一实证，与 Safactory 形成呼应。

---

## 可实验假设

1. **Agent 记忆过期检测将成为标配能力** — STALE 基准暴露了当前 Agent 无法识别记忆失效的问题，结合 Feedback-Normalized Memory 的思路，未来编码 Agent 可能需要内置"记忆有效期"机制，自动标记和刷新过期上下文。

2. **RAG 安全架构需要重新评估** — Architecture Matters 的反直觉发现（多 Agent 辩论在投毒下更脆弱）意味着生产级 RAG 系统不能简单堆叠 Agent 数量来提效，安全审计应纳入架构选型标准。

3. **Agent 工厂化趋势加速** — Safactory 提出的一站式 Agent 工厂 + MAS-Algorithm 的多 Agent 工作流表明，Agent 开发正在从"单模型调优"转向"工厂化流水线"，类似 MLOps → AgentOps 的演进路径。

---

## 趋势总结

今日论文高度聚焦 **Agent 记忆管理** 和 **RAG 架构优化** 两大方向。6 月 7 日单日密集爆发 6 篇论文，说明社区正在集中攻克 Agent 长期记忆的可信性（STALE、Feedback-Normalized Memory）和 RAG 系统的安全/效率平衡（LatentRAG、Architecture Matters、Event-Causal RAG）。Safactory 的 Agent 工厂框架则暗示 Agent 开发正走向工业化流水线模式。

---
