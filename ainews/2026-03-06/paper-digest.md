# AI 论文速递 | 2026-03-06 14:04

**生成时间**: 2026-03-06 14:04 (Asia/Shanghai)
**数据源**: arxiv_papers.json (8 篇候选)
**归档 Agent**: ainews

---

## 论文清单

### 1. Leveraging LLM Parametric Knowledge for Fact Checking without Retrieval
**URL**: https://arxiv.org/abs/2603.05471v1
**类别**: cs.CL, cs.AI
**发布**: 2026-03-05

利用 LLM 内部参数知识进行事实核查，无需外部检索。研究证明经过适当训练的 LLM 可直接作为事实核查器，在多个基准上接近检索增强方法。

**影响评估**: 为 Agent 系统提供轻量级可信度验证方案，降低检索依赖。

---

### 2. Towards Provably Unbiased LLM Judges via Bias-Bounded Evaluation
**URL**: https://arxiv.org/abs/2603.05485v1
**类别**: cs.AI
**发布**: 2026-03-05

提出偏差边界评估框架，为 LLM 作为自动评判器提供可证明的无偏保证。在自主 AI 工作流中，自动化反馈的可靠性至关重要。

**影响评估**: 为 Agent 自我迭代循环提供可验证的奖励信号，减少偏差累积风险。

---

### 3. Planning in 8 Tokens: A Compact Discrete Tokenizer for Latent World Model
**URL**: https://arxiv.org/abs/2603.05438v1
**类别**: cs.CV, cs.AI, cs.RO
**发布**: 2026-03-05

将规划状态压缩至仅 8 个离散 token，实现潜在世界模型的高效决策时规划。在保持性能的同时大幅降低计算开销。

**影响评估**: 为 Agent 长期规划提供轻量级世界模型，适合资源受限场景。

---

### 4. Reasoning Theater: Disentangling Model Beliefs from Chain-of-Thought
**URL**: https://arxiv.org/abs/2603.05488v1
**类别**: cs.CL, cs.AI, cs.LG
**发布**: 2026-03-05

发现推理模型存在"表演性 CoT"现象：模型已确信答案但仍生成冗长推理链。通过激活探测和早期强制回答揭示内部真实信念。

**影响评估**: 对 AI 安全监控有重要意义，CoT 可能无法真实反映模型决策过程。

---

### 5. POET-X: Memory-efficient LLM Training by Scaling Orthogonal Transformation
**URL**: https://arxiv.org/abs/2603.05500v1
**类别**: cs.LG, cs.AI, cs.CL
**发布**: 2026-03-05

通过正交等价变换重参数化框架优化 LLM 训练，在保持频谱特性的同时显著降低显存占用。支持更大规模稳定训练。

**影响评估**: 降低大模型训练门槛，适合个人/小团队微调实验。

---

### 6. NL2GDS: LLM-aided interface for Open Source Chip Design
**URL**: https://arxiv.org/abs/2603.05489v1
**类别**: cs.AR, cs.CY, cs.LO, eess.SY
**发布**: 2026-03-05

自然语言到芯片布局框架，利用 LLM bridge 高层规格与 RTL 实现之间的鸿沟。支持快速原型设计和系统开发。

**影响评估**: AI for Science 在硬件设计领域的落地，降低芯片开发门槛。

---

### 7. An Exploration-Analysis-Disambiguation Reasoning Framework for Word Sense Disambiguation with Low-Parameter LLMs
**URL**: https://arxiv.org/abs/2603.05400v1
**类别**: cs.CL
**发布**: 2026-03-05

提出三阶段推理框架，使小参数 LLM 在词义消歧任务上接近 GPT-4-Turbo 水平。通过探索 - 分析 - 消歧流程弥补参数规模差距。

**影响评估**: 为资源受限场景提供高效 NLP 方案，小模型 + 好框架可匹敌大模型。

---

## 可实验假设

1. **CoT 监控实验**：对本地推理模型进行激活探测，验证"表演性 CoT"现象是否存在于开源模型中，评估安全监控有效性。

2. **8-Token 规划器复现**：在简单网格世界环境中实现 8-token 离散化世界模型，测试规划效率与 token 压缩率的平衡点。

3. **小模型 EAD 框架迁移**：将探索 - 分析 - 消歧框架迁移到其他 NLP 任务（如实体链接、指代消解），验证通用性。

---

## 趋势总结

今日论文聚焦 **Agent 可信度与效率** 两大主题：事实核查无需检索、无偏 LLM 评判器、CoT 可监控性均指向构建可信赖的自主系统。同时，8-token 规划器和 POET-X 训练优化反映社区对**轻量化部署**的持续追求，小模型 + 好框架正成为资源受限场景的主流方案。

---

*归档完成 | 下一篇：memory/2026-03-06.md*
