Now let me write the full paper digest report.

📄 AI 论文速递 | 2026-05-28 12:00

本期速递覆盖 8 篇论文，核心信号指向三个方向：**MCP 安全攻防从理论走向 benchmark**、**Skill 形式化在 Runtime 层开启新一轮探索**、**Multi-Agent + RAG 在垂直场景（法律/交通/科学计算）加速落地**。

---

## 📋 论文清单

### 1. MCP 投毒攻击 Benchmark：当工具说明书撒谎时

**论文标题**: When the Manual Lies: A Realistic Benchmark to Evaluate MCP Poisoning Attacks for LLM Agents  
**URL**: https://arxiv.org/abs/2605.24069v1  
**发表时间**: 2026-05-22

首个系统评估 MCP 协议下工具投毒攻击的现实基准。研究聚焦 LLM Agent 通过 MCP 接入外部工具的典型路径——当一个恶意的 MCP server 在其工具描述/参数文档中植入误导性内容，Agent 是否会被诱导执行危险操作？论文构建了覆盖 6 类攻击向量的评测框架，在多个主流 Agent 框架上验证了 MCP 信任链的脆弱性。

**影响评估**: ⚠️ 高。这对所有 MCP 生态是警钟。当前 Agent 普遍无条件信任 MCP server 的「自述文档」，缺少签名校验与沙箱隔离。MCP 安全将在接下来 3-6 个月成为社区焦点议题，类似 npm 供应链安全在 2021 年的爆发路径。


### 2. Formal Skill：将 Agent Skill 从 Markdown 升级为可编程运行时

**论文标题**: Formal Skill: Programmable Runtime Skills for Efficient and Accurate LLM Agents  
**URL**: https://arxiv.org/abs/2605.19604v1  
**发表时间**: 2026-05-19

提出「Formal Skill」概念——将当前以 Markdown/自然语言指令包形式定义的 Agent Skill，升级为可编程、可类型检查、可组合的运行时原语。论文设计了一套形式化描述语言，使 Skill 的执行路径可被静态分析和运行时验证，显著降低 LLM 解析长文档 Skill 时产生的偏差和幻觉。

**影响评估**: ⭐ 高度相关。这与 OpenClaw 生态中 Skill 的演进方向高度一致——从「给 Agent 一段 Markdown 文档」进化到「给 Agent 一组可验证的执行原语」。Skill 的形式化/标准化可能是下一个 Agent 框架竞争的分水岭。


### 3. Device Context Protocol：MCP 向物联网设备的降维适配

**论文标题**: Device Context Protocol: A Compact, Safety-First Architecture for LLM-Driven Control of Constrained Devices  
**URL**: https://arxiv.org/abs/2605.26159v1  
**发表时间**: 2026-05-24

将 MCP 的理念从云端服务下沉到 MCU/嵌入式设备。论文提出「Device Context Protocol」（DCP），在内存受限（KB 级）的硬件上实现 LLM 可调用的设备能力暴露层，强调 Safety-First 架构——所有 LLM 指令必须通过设备端的安全策略引擎校验后才能执行物理操作。

**影响评估**: 趋势信号。MCP 向 IoT 延伸是必然方向。虽然短期内难以标准化，但「LLM→物理世界」的控制链路安全设计对机器人/智能家居/工业控制场景具有前瞻价值。


### 4. LegalGraphRAG：图 RAG + Multi-Agent = 可信法律推理

**论文标题**: LegalGraphRAG: Multi-Agent Graph Retrieval-Augmented Generation for Reliable Legal Reasoning  
**URL**: https://arxiv.org/abs/2605.28120v1  
**发表时间**: 2026-05-27

将 GraphRAG 和 Multi-Agent 架构融合应用于法律推理。核心创新在于：通过多 Agent 分工（检索 Agent + 推理 Agent + 验证 Agent）配合法律知识图谱的结构化索引，解决法律文本异质性高、推理链条依赖判例引用网络的难题。

**影响评估**: 中高。Multi-Agent + GraphRAG 的组合范式正在从通用场景向垂直高价值领域（法律、医疗、金融）渗透。异构知识的结构化索引是多 Agent 能否在专业领域产生可靠推理的关键。


### 5. ConRAG：多视角共识驱动检索解决多跳问答

**论文标题**: ConRAG: Consensus-Driven Multi-View Retrieval for Multi-Hop Question Answering  
**URL**: https://arxiv.org/abs/2605.28093v1  
**发表时间**: 2026-05-27

提出 Consensus-driven RAG——对同一问题从多个语义视角分别检索证据，再通过共识机制聚合多路结果。对比单一检索管线的 RAG，ConRAG 在多跳推理任务上将证据召回率提升了 12-18%，同时减少了错误传播。

**影响评估**: 中等。Multi-View 检索是 RAG 可靠性改进的一个低成本路径（不需要重新训练模型或重建知识图谱），可以作为现有 RAG pipeline 的即插即用增强层。


### 6. ColPackAgent：用 MCP + Agent Skill 驱动科学计算工作流

**论文标题**: ColPackAgent: Agent-Skill-Guided Hard-Particle Monte Carlo Workflows for Colloidal Packing  
**URL**: https://arxiv.org/abs/2605.15625v1  
**发表时间**: 2026-05-15

展示了 MCP 工具服务器 + Agent Skill 如何自动化胶体粒子堆积的 Monte Carlo 模拟。Agent 通过 MCP 调用 Fortran 求解器，自主管理参数空间探索、结果分析和迭代终止判据，将传统需要领域专家手动调参的复杂模拟流程自动化。

**影响评估**: 中低。这是一个「MCP 作为科学计算 API 网关」的有趣案例。虽然领域垂直，但证明了 MCP 不仅是工具调用通道，也可以成为复杂工作流的编排中枢。


### 7. 解耦智能：多 Agent LLM 框架生成可控交通仿真场景

**论文标题**: Decoupled Intelligence: A Multi-Agent LLM Framework for Controllable Traffic Scenario Generation in SUMO  
**URL**: https://arxiv.org/abs/2605.27685v1  
**发表时间**: 2026-05-26

提出「解耦智能」框架——将交通场景生成任务拆分为多个专职 LLM Agent（场景规划 Agent、行为建模 Agent、仿真参数 Agent），各 Agent 通过结构化通信协议协同工作，显著提升了 SUMO 仿真中复杂场景的生成质量和可控性。

**影响评估**: 中等。Multi-Agent 架构在「解耦复杂任务」上的方法论具有跨场景借鉴意义。将整体任务拆解给专职 Agent 而非一个全能 Agent，在可解释性和可调试性上有明显优势。


### 8. 自适应多模态 Agent 框架用于自动工作流执行

**论文标题**: Adaptive Multimodal Agents-Based Framework for Automatic Workflow Execution  
**URL**: https://arxiv.org/abs/2605.28607v1  
**发表时间**: 2026-05-27

提出将多模态大模型（MLLM）的视觉感知能力引入 Agent 工作流执行——Agent 可以直接「看」屏幕/界面而非仅依赖结构化元数据来理解当前状态和下一步操作，从而在 UI 自动化场景中实现更鲁棒的跨应用工作流编配。

**影响评估**: 中等。多模态 Agent 正在模糊「结构化 API 调用」与「人类式 GUI 操作」的边界。对 RPA/AI 操作员类产品有直接启发。


---

## 🧪 可实验假设

1. **MCP 投毒检测沙箱**: 基于论文 #1 的攻击向量，可以构建一个「MCP tool description 扫描器」——在 Agent 接入任意第三方 MCP server 前，用另一个安全 Agent 对工具描述做语义投毒检测和权限分析，验证是否可拦截 80% 以上的投毒尝试。

2. **Formal Skill DSL 原型**: 基于论文 #2 的思路，为 OpenClaw Skill 系统设计一个最小化的「Skill 类型语言」（类似 OpenAPI schema 但面向 Agent 执行步骤），对比 Markdown Skill 与 Formal Skill 在任务完成率和幻觉率上的差异。

3. **ConRAG 多视角检索增强**: 在现有 RAG pipeline 上实现「查询改写 → 多视角检索 → 共识融合」的轻量外挂层，测量对多跳/多证据问题准确率的提升幅度（参考论文 #5 的 12-18% 召回提升）。

---

## 📊 趋势总结

本期论文释放的信号非常清晰：**MCP 安全正在从「意识到风险」进入「量化风险」阶段**——首篇 MCP 投毒 benchmark 的出现标志着协议成熟度迈向下一级台阶的必然阵痛。与此同时，**Skill 的形式化编程（Formal Skill）代表了 Agent 能力封装从文档驱动到代码驱动的一次范式升级**，这可能成为 2026 下半年 Agent 框架竞争的核心差异化方向。Multi-Agent + GraphRAG + 垂直场景的三叉戟组合持续产出，法律/交通/科学计算的落地密度显著高于上一季度。

---

✅ 已归档：knowledge/daily/2026-05-28/paper-digest.md