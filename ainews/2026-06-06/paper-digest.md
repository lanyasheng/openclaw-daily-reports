ArXiv papers 有 8 篇，全部有效，数据充足。直接从 ArXiv 抓取的数据生成论文速递。

📄 **AI 论文速递 | 2026-06-06 12:00**

本周六午间论文速递聚焦 **Agent 记忆系统、多 Agent 协作、工具选择和安全监控**——8 篇新论文覆盖了 LLM Agent 基础设施的多个核心痛点。

---

**1. Agent Memory: Characterization and System Implications of Stateful Long-Horizon Workloads**
🔗 https://arxiv.org/abs/2606.06448
论文对当前 Agent 记忆系统生态做了系统性评估，重点分析了长周期任务中 Agent 的状态持久化挑战：跨会话的记忆存储、检索和更新。作者发现存量系统在"写密集"场景下性能急剧下降，并提出了新的系统级优化方向。对于正在构建记忆层（如 MemPalace 类方案）的开发者来说，这是必须阅读的参考论文。

**2. TOKI: A Bitemporal Operator Algebra for Contradiction Resolution in LLM-Agent Persistent Memory**
🔗 https://arxiv.org/abs/2606.06240
Agent 的持久记忆本质上是写密集型的——每次信念更新都是一次版本写入，而新信息可能与已存储事实矛盾。现有方案（last-writer-wins、证据加权合并、等待确认、按规则策略）均未声明完整的语义模型。TOKI 提出了双时态算子代数，能为矛盾检测提供严格的形式化基础。落地价值极高，直接可用于 Agent 知识库去幻觉设计。

**3. Humans' ALMANAC: A Human Collaboration Dataset of Action-Level Mental Model Annotations for Agent Collaboration**
🔗 https://arxiv.org/abs/2606.06388
构建了一个人类协作数据集，标注了人类在协作过程中的"心理模型"（mental model）变化——对方知道什么、相信什么、意图是什么。目标是让 LLM Agent 在协作时能持续维护和校准这些模型。这个方向稀缺，数据开源后极可能成为多 Agent 协作评测的标配基准。

**4. CollabSim: A CSCW-Grounded Methodology for Investigating Collaborative Competence of LLM Agents**
🔗 https://arxiv.org/abs/2606.06399
发现多 Agent 系统失败的根本原因往往不是单个 Agent 的推理能力不足，而是 Agent 间的文本协调出了问题。CollabSim 提出了基于计算机支持协同工作（CSCW）理论的评估方法论。对多 Agent 架构设计有直接指导意义——提示词中就应该考虑 Agent 间的"通信协议"层面。

**5. Will the Agent Recuse Itself? Measuring LLM-Agent Compliance with In-Band Access-Deny Signals**
🔗 https://arxiv.org/abs/2606.06460
当自主 Agent 持有真实凭证（API key、数据库权限等）时，操作者没有标准方式告知 Agent"这个资源不能碰"。论文提出了"带内拒绝信号"（In-Band Access-Deny Signal）的概念，并测量了 Agent 面对该信号时的遵从性。对于任何在生产环境中部署自主 Agent 的团队，这是安全设计的关键参考。

**6. From Reward-Hack Activations to Agentic Risk States: Context-Calibrated Mechanistic Monitoring**
🔗 https://arxiv.org/abs/2606.06223
在 ReAct 模式 Agent 中研究 reward-hacking（奖励投机）行为，通过内部激活监控来检测 Agent 是否进入"风险状态"。结合环境上下文校准后，监控精度显著提升。Agent 安全领域的实操级研究，如果你在部署 Agent 到开放环境，这个框架很有参考价值。

**7. ToolChoiceConfusion: Causal Minimal Tool Filtering for Reliable LLM Agents**
🔗 https://arxiv.org/abs/2606.06284
工具菜单越大，Agent 越容易选错工具。现有方法主要优化语义相关性——工具名称或描述与任务语义匹配，但忽略了工具间的因果关系混淆。ToolChoiceConfusion 提出因果最小化工具过滤，在保持可用性的前提下大幅减少错误调用。对 MCP 生态中工具路由策略的设计有直接启示。

**8. MLEvolve: A Self-Evolving Framework for Automated Machine Learning Algorithm Discovery**
🔗 https://arxiv.org/abs/2606.06473
提出了一个自我进化的框架，让 LLM Agent 在机器学习工程（MLE）场景中持续自我迭代。关键创新是解决分支信息隔离和记忆无搜索的问题，使 Agent 在长时间跨度的算法发现任务中保持改进动力。虽偏研究，但"自进化 Agent"的概念框架值得关注。

---

**🔬 可实验假设**

1. **Agent 记忆矛盾消解方案**：可参考 TOKI 的双时态算子思路，为现有 Agent 框架（如 OpenClaw 的内存模块）增加显式的"置信度冲突检测→自动仲裁"层，降低长期记忆中的事实冲突导致的不一致。

2. **因果最小工具路由**：借鉴 ToolChoiceConfusion，在 MCP 服务端实现工具之间的因果依赖图分析——当工具 A 的输出可能是工具 B 的输入时，优先推荐 B；当工具 A 与 B 功能冗余时，降级一个。这能有效减少工具选择中的假阳性。

3. **Agent 拒绝信号协议**：受 "Access-Deny Signals" 启发，可在 Agent 框架中定义一个标准化的 `#DENY` 通道——当资源/API 返回特定格式的拒绝信号时，Agent 必须停止重试并上报。这对生产环境中的安全护栏设计有直接价值。

---

**📊 趋势总结**

- **Agent 记忆正式成为研究热点**：同时出现两篇系统性记忆论文（表征+冲突消解），说明业界正在从"有记忆就行"进入"记忆需要工程化"阶段。
- **Agent 安全从外围走向核心**：拒绝信号和风险监控两篇论文指向同一个方向——部署自主 Agent 的安全框架不能再是"事后检查"，必须嵌入 Agent 的运行时循环。
- **协作能力 > 单 Agent 能力**：ALMANAC 和 CollabSim 都验证了多 Agent 系统的瓶颈在通信层面，而非推理能力。这提示提示词工程的重点应从"让 Agent 更聪明"转向"让 Agent 更懂协作"。

✅ 已归档：knowledge/daily/2026-06-06/paper-digest.md