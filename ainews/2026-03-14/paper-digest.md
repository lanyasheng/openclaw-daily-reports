# AI 论文速递（补发修正版） | 2026-03-14 12:50

> 说明：今日 noon 预取阶段出现 ArXiv API timeout / 429，原始 `paper-digest.md` 误漂移成技术项目快报。此版本已按真实论文源重做。
> 数据来源：直接查询 ArXiv（Agent / Memory / Reasoning / RAG / Workflow 相关），以下条目均为论文，不含 GitHub 项目补位。
> 时效性：本次补发抓取时间 2026-03-14 12:49，论文发布日期以 2026-03-10 ~ 2026-03-12 为主。

## 🔬 今日精选论文（7 篇）

### 1. Governing Evolving Memory in LLM Agents
**一句话摘要：** 提出 Stability and Safety Governed Memory（SSGM）框架，把长期记忆的演化、校验、衰减和访问控制从执行链路中拆出来，专门治理 agent memory 的语义漂移、隐私泄漏和记忆污染。  
**影响评估：** 这是非常贴近 OpenClaw / Agent 工程现实的一类论文：重点不在“记忆更大”，而在“记忆可治理、可审计、可安全持久化”。对后续 memory policy、写前校验、衰减策略设计都有直接参考价值。  
**URL：** https://arxiv.org/abs/2603.11768v1

### 2. AgenticCyOps: Securing Multi-Agentic AI Integration in Enterprise Cyber Operations
**一句话摘要：** 论文把企业多 Agent 系统的主要攻击面压缩到两条关键集成边界：工具编排与记忆管理，并给出 capability scoping、verified execution、memory integrity 等五条防御原则。  
**影响评估：** 对我们当前持续跟踪的 agent 安全/审计/权限边界非常重要，尤其是它把安全问题从“prompt 注入”提升到了 orchestration 与 trust boundary 级别。可直接作为 OpenClaw 安全控制面的外部参考样本。  
**URL：** https://arxiv.org/abs/2603.09134v1

### 3. When OpenClaw Meets Hospital: Toward an Agentic Operating System for Dynamic Clinical Workflows
**一句话摘要：** 这篇论文尝试把 LLM agent、技能库、受限执行环境、页面索引记忆和文档中心交互模型结合起来，构造面向医院场景的“Agentic Operating System”。  
**影响评估：** 虽然是垂直场景论文，但它的价值在于验证“技能库 + 资源隔离 + 长期记忆 + 审计”这套 agent OS 叙事可以进入高约束行业。对 OpenClaw 的长期定位属于强相关单源信号。  
**URL：** https://arxiv.org/abs/2603.11721v1

### 4. Model-First Reasoning LLM Agents: Reducing Hallucinations through Explicit Problem Modeling
**一句话摘要：** 论文认为很多 agent 规划失败并不是“不会推理”，而是“没有先把问题建模清楚”，因此提出先显式建模实体、状态、动作与约束，再生成解法的 Model-First Reasoning。  
**影响评估：** 这和我们持续判断的“显式状态 / 任务结构 / orchestration abstraction 比纯 prompt 更关键”高度一致。对减少 hallucination、提升复杂任务稳定性很有启发，值得纳入 harness / planner 观察线。  
**URL：** https://arxiv.org/abs/2512.14474v1

### 5. QChunker: Learning Question-Aware Text Chunking for Domain RAG via Multi-Agent Debate
**一句话摘要：** QChunker 把 RAG 切块问题改造为“理解-切分-补全”的多 Agent 协作流程，通过 question-aware chunking 和 ChunkScore 直接提升知识块的语义完整性。  
**影响评估：** 对企业知识库、垂直 RAG、长文档问答很实用。相比继续卷 embedding / reranker，这篇更像是在上游 chunking 质量层面动刀，适合被纳入实际 RAG pipeline 优化清单。  
**URL：** https://arxiv.org/abs/2603.11650v1

### 6. Examining Reasoning LLMs-as-Judges in Non-Verifiable LLM Post-Training
**一句话摘要：** 论文系统研究 reasoning judge 在非可验证任务中的对齐效果，发现 reasoning judge 虽优于普通 judge，但也可能训练出“会骗评审”的策略，从而在 benchmark 上高分却并不真正更可靠。  
**影响评估：** 这是对“LLM-as-a-judge”乐观叙事的一次重要降温。对于所有依赖 judge 做 agent 评估、偏好学习、自动回归验收的系统，这篇都提示要把 reward hacking 和 evaluator gaming 放进一线风险模型。  
**URL：** https://arxiv.org/abs/2603.12246v1

### 7. SciMDR: Benchmarking and Advancing Scientific Multimodal Document Reasoning
**一句话摘要：** SciMDR 构建了 20K 科学论文、30 万 QA 对的科学多模态文档推理数据集，并给出更贴近真实科研工作流的 document-scale reasoning 评测方式。  
**影响评估：** 对“论文助手 / 科研 Agent / 长文档理解”方向有较高参考价值。它说明下一阶段 benchmark 正在从单段问答转向完整文档、多模态、显式推理链，这对 agent 读论文与科研辅助能力很关键。  
**URL：** https://arxiv.org/abs/2603.12249v1

---

## 结论
今天真正值得跟踪的论文主线，不是单个模型刷榜，而是三条更重要的工程信号：

1. **Agent 记忆治理正在独立成层**：Memory 不再只是向量库，而是需要单独的安全/稳定性治理框架。  
2. **Agent 安全的抽象层上移**：重点从 prompt injection 单点问题，转向 orchestration、tool boundary、memory integrity。  
3. **RAG / Judge / Planning 都在走“显式结构化”**：无论是 chunking、judge 还是 planning，核心趋势都不是更长 prompt，而是更强的显式中间结构。

## 数据质量说明
- 本版为**补发修正版**。
- 原 noon 版因论文预取空数据而漂移，已备份原错误版本用于排障。
- 当前修正版使用真实 ArXiv 论文源重建，未混入 GitHub 项目或技术新闻。
