ArXiv 有 8 篇有效论文，满足 ≥ 4 条件。digest_latest.json 中有 papers 类 8 条但未列出具体条目，不过 arXiv 数据充足。现在我需要检查有没有 papers 分类的 RSS 补充条目。

看 digest_latest.json 的 stats，`byCategoryRaw.papers: 8` 但 candidates 中没有一个 `category: "papers"` 的条目——说明 papers RSS 条目已被筛选掉或未进入 candidates 阶段。ArXiv 已有 8 篇，直接使用 arXiv 数据生成论文速递。

📄 **AI 论文速递 | 2026-07-10 12:00**

---

## 今日 8 篇 AI 论文精选

### 1. 🔬 SageMath + LLM Agent：计算数学与实验数学的新范式
**Evaluating SageMath-Augmented LLM Agents for Computational and Experimental Mathematics**
https://arxiv.org/abs/2607.06820v1

作者将 ReAct 式 agent 设置与 SageMath（计算机代数系统）结合，让 LLM agent 在数学推理过程中获得来自 CAS 的可验证反馈。不同于以往的自动形式化与定理证明，这篇工作聚焦于 CAS 在 agentic LLM 工作流中的实际增益价值，为数学计算 Agent 提供了实用基准。

**影响评估**: 对数学研究自动化和 STEM 教育 Agent 有直接实用价值，SageMath 集成方案可复用到其他科学计算场景。

---

### 2. 🏭 从 Prompt 到合约：面向企业级 LLM Agent 的 Harness 工程
**From Prompts to Contracts: Harness Engineering for Auditable Enterprise LLM Agents**
https://arxiv.org/abs/2607.08028v1

企业级 LLM 应用从原型到产品化需要解决数据源边界、实体路由、答案合约和可重现追踪等要求。本文提出了一套 "harness 工程" 方法，将 prompt 驱动的行为升级为合约驱动的可审计架构，确保企业 Agent 行为可追溯、可验证。

**影响评估**: 对于 LLM Agent 在企业落地的合规性和可审计性需求，这是非常有工程参考价值的工作。

---

### 3. 💧 TRACE：面向 LLM-Agent 轨迹的双通道鲁棒溯源水印
**TRACE: A Two-Channel Robust Attribution Watermark via Complementary Embeddings for LLM-Agent Trajectories**
https://arxiv.org/abs/2607.08400v1

LLM agent 经常经由转售商触达终端用户，当归属争议发生时，轨迹日志是关键证据。TRACE 通过互补嵌入技术为 Agent 行为轨迹添加隐式水印，可在不被察觉的情况下实现鲁棒属性溯源，防止模型替换和品牌冒用。

**影响评估**: Agent 经济生态中的重要基础设施，直接解决 Agent 归属溯源难题，对 agent marketplace 模式至关重要。

---

### 4. 📊 ADE-PRF：长期多Agent系统可靠性预测框架
**Agent Delivery Engineering Predictive Reliability Framework**
https://arxiv.org/abs/2607.07689v1

长期运行的多 Agent 系统面临基础设施监控无法覆盖的可靠性风险。ADE-PRF 从 20 个异构信号中进行被动退化检测，通过健康轨迹预测实现主动干预。框架覆盖五个维度，为复杂 Agent 系统提供运维层面的可靠性保障。

**影响评估**: Agent 系统从原型走向生产的"最后一公里"问题，与大厂在生产环境部署 Agent 的痛点高度契合。

---

### 5. 🔬 物理审计：科学机器学习中的 Agentic 发现验证
**Physics-Audited Agentic Discovery in Scientific Machine Learning**
https://arxiv.org/abs/2607.07379v1

在 scientifc machine learning (SciML) 中，LLM agent 可以发现替代模型并自动评分选优。但低误差不一定意味着预测场满足物理约束。本文提出物理审计框架，确保 Agent 选择模型不仅在数值上精确，在力学意义上也合理。

**影响评估**: 科学计算领域的 Agent 应用关键问题，直接关系到 AI 驱动的科学发现可信度。

---

### 6. 🔧 从原子动作到标准作业程序：自进化LLM Agent的工具迭代优化
**From Atomic Actions to Standard Operating Procedures: Iterative Tool Optimization for Self-Evolving LLM Agents**
https://arxiv.org/abs/2607.07321v1

现有 Agent 框架主要依赖细粒度原子动作（如文件 I/O、单次搜索）构成的静态工具集，迫使 Agent 反复编排相同的基本步骤。本文提出让 Agent 将高频调用模式自动编译为标准作业程序（SOP），实现工具的自我迭代进化，显著提升效率。

**影响评估**: 与 SOUL.md 关注的 Agent 自我进化方向高度吻合，对 Agent 框架设计有重要启发。

---

### 7. 🧪 TTHE：测试时 Harness 进化——Agent 行为优化新范式
**TTHE: Test-Time Harness Evolution**
https://arxiv.org/abs/2607.08124v1

LLM Agent 的行为不仅由底层模型决定，还由其"harness"（可执行程序——构造上下文、调用工具、验证中间结果、从失败中恢复的完整管线）决定。现有方法在部署前搜索最优 harness，TTHE 则将这个过程移到运行时，让 Agent 在测试阶段动态进化自己的执行框架。

**影响评估**: 与 "From Prompts to Contracts" 形成互补视角，将 harness 优化的窗口从部署前延伸到运行时，Agent 开发和运维理念的重大转变。

---

### 8. 🛠️ 低延迟系统中的工具制造与自进化 Agent
**Tool-Making and Self-Evolving LLM Agents in Low-Latency Systems**
https://arxiv.org/abs/2607.08010v1

生产环境中 LLM Agent 每次请求都重复生成相同过程代码，造成延迟浪费和可靠性风险。本文用 agentic tool-making pipeline 替代推理时的重复编码循环：将频繁执行的标准操作步骤提前编译为经过验证的版本化工具。

**影响评估**: 与第 6 篇形成姊妹篇，从低延迟系统角度解决 Agent 工具复用问题，工程实践价值高。

---

## 🔬 可实验假设

1. **SageMath Agent 可作为数学教育的 AI 助教原型**——将论文的 ReAct+CAS 方案包装成面向学生的交互式数学解题 Agent，结合当前流行的 tutor agent 趋势。
2. **"SOP 自动编译"机制可以集成到主流 Agent 框架**——第 6 篇和第 8 篇的核心思想可直接在 LangChain / CrewAI / OpenClaw Skill 体系中实现"工具自动升级"插件，将重复行为序列自动转化为可重用工具。
3. **Harness 工程方法可用于 OpenClaw 的 Skill 审计**——第 2 篇的"合约驱动 Harness"方案与 OpenClaw Skill 的安全/权限边界管理需求高度匹配，可探索为 Skill 添加可审计的执行合约层。

---

## 📈 趋势总结

- **Agent 工业化加速**：今日 8 篇论文中有 7 篇直接围绕 Agent 的生产级工程问题（可审计性、归属溯源、可靠性、工具进化、运行时优化），说明 Agent 领域已从"能不能做"进入"如何做好"阶段。
- **Self-Evolving Agent 成主流叙事**：第 6、7、8 三篇均从不同角度探讨 Agent 的自我进化机制（工具级 / harness 级 / 代码编译级），表明"静态部署 -> 运行时自适应"是整个领域的共识方向。
- **数学/科学 Agent 进入验证深水区**：第 1 篇（CAS 集成）和第 5 篇（物理审计）展示了 Agent 在科学计算场景从"能用"到"可信"的进阶路径，"验证"将成为科学 Agent 的核心竞争壁垒。

---

✅ 已归档：knowledge/daily/2026-07-10/paper-digest.md