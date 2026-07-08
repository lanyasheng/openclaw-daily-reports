I have all the data. Let me check the digests for papers-specific RSS entries to see if there are any additional paper sources.

Looking at the RSS digest, the `category=papers` entries are not explicitly marked - the digest only has category stats showing 9 raw papers items, but the candidates list doesn't have clearly separated papers. That's fine — the ArXiv file has 8 papers, which is sufficient. Let me now compose the full paper digest.

📄 AI 论文速递 | 2026-07-08 12:00

今日论文聚焦 Agent 基准测试、多智能体协作、Agent 训练数据策展等前沿方向，共 8 篇。

---

🔬 一、论文清单

---

1️⃣ PolyWorkBench：多语言长周期 LLM Agent 基准测试
https://arxiv.org/abs/2607.06008v1

现有 Agent 基准几乎默认单语言设定——整个推理、工具调用、环境交互都在英语下完成。PolyWorkBench 首次系统性地构建多语言长周期任务基准，覆盖多种自然语言下 Agent 的规划、工具使用与交互能力。对于正在搭建全球化 Agent 产品的团队，这是一个不可忽视的信号：你的 Agent 在英语环境跑通，不代表在中文/日语/阿拉伯语下同样可靠。

影响评估：★★★★ 多语言 Agent 评估缺口的重要填补，对跨国部署有直接参考价值。

---

2️⃣ 从蓝图到现实：基于 LLM 多智能体模拟建模与应用 Putnam 社会资本理论
https://arxiv.org/abs/2607.06080v1

将 Putnam 的社会资本理论（SCT）——集体行动与社区繁荣的基础理论——首次用 LLM 多智能体模拟实现。传统实证方法在可控性和可复现性上有天然限制，而本文构建了理论对齐的多智能体环境，让社会资本的形成、积累和衰减过程可被定量观察。社科研究方法论的一次重要升级。

影响评估：★★★★ 社科+AI 交叉研究的示范性工作，Agent 社会模拟从此有了理论锚点。

---

3️⃣ 前沿 LLM Agent 经济体的信息极限与吸引子动力学
https://arxiv.org/abs/2607.06001v1

一个预注册实验：用小规模 Claude Opus 4.8 Agent 构建微型经济体，验证两个定量预测——市场耦合下的财富增长信息论容量区域，以及平均场残差吸引子。这意味着 Agent 经济的行为边界可以从信息论角度进行预测。实验设计标准严格，结论具有启发性。

影响评估：★★★ 跨学科趣味十足，信息论视角切入多 Agent 经济行为建模，值得关注后续规模化验证。

---

4️⃣ Onnes：面向量子计算低温故障诊断的物理约束多Agent LLM 模拟器
https://arxiv.org/abs/2607.05805v1

稀释制冷机是超导量子计算机的基础设施，但其故障诊断仍停留在阈值告警阶段——"出事了"，但"哪里出事了"不知道。Onnes 构建了稀释制冷机的物理数字孪生模拟器，以 LLM Agent 协作进行故障根因分析。AI for Science 在量子计算基础设施运维层的落地案例。

影响评估：★★★★ 物理约束+LLM Agent 的方法论可迁移到其他复杂工程系统故障诊断。

---

5️⃣ 开局即注定失败：基于记忆控制探针级联的 LLM Agent 轨迹早期中止
https://arxiv.org/abs/2607.06503v1

LLM Agent 解决多步任务时，常陷入注定失败的轨迹却继续消耗大量推理算力。本文发现：Agent 失败可以从其内部表征中早期预测——通过轻量级探针级联（recall-controlled probe cascade）在早期步骤预测失败概率，从而提前中止无效轨迹。直接节约推理成本，对于大规模 Agent 部署是实用的效率优化方案。

影响评估：★★★★★ 成本优化刚需，思路简洁有效，适合快速工程落地。

---

6️⃣ 基于信息增益的 Rollout 策略优化：多轮 LLM Agent 的自适应树状 Rollout
https://arxiv.org/abs/2607.06223v1

RL 在提升 LLM Agent 长周期搜索任务上有潜力，但现有方法面临 rollout 预算硬性分配、非关键路径浪费算力的瓶颈。本文提出基于信息增益的自适应树状 rollout 策略——每次 rollout 前评估哪个分支能带来最多信息增量，动态分配计算资源。比固定 rollout 更高效，可与其他推理时搜索策略叠加使用。

影响评估：★★★★ 树搜索+信息论引导的策略思路清晰，与 MCTS 类方法结合潜力大。

---

7️⃣ 部分可观测下的审慎协作：LLM Agent 联合决策研究
https://arxiv.org/abs/2607.06157v1

人类协作中自然会通过沟通来对齐信息、达成共识。本文研究 LLM Agent 在部分可观测联合决策任务中的审慎行为（deliberation）。发现：Agent 之间的沟通策略、信息共享时机对协作质量有显著影响。对于构建多 Agent 协作系统的团队，理解和设计 Agent 间的"讨论"规则至关重要。

影响评估：★★★ 多 Agent 协作中沟通策略的实证研究，产品设计层面有参考意义。

---

8️⃣ CurateEvo：面向 Agent 后训练的数据策展进化方法
https://arxiv.org/abs/2607.06140v1

LLM Agent 后训练（post-training）管线中，数据策展通常被视为固定预处理步骤，主要关注数据增强却忽略了持续优化。CurateEvo 提出让数据策展过程与训练同步进化——根据环境反馈动态调整训练数据的选择和权重。从"固定数据集→Agent"到"Agent↔动态数据"的范式转变。

影响评估：★★★★ 数据策展+训练循环进化的思路有实用价值，长期来看可能改变 Agent 后训练的工程实践。

---

🧪 二、可实验假设

1️⃣ 【推断时成本优化】"Doomed from the Start" 的探针级联早期中止方法可移植到当前主流 Agent 框架（如 LangGraph / CrewAI）中。验证方式：在 3 个典型多步任务上部署，对比有无早期中止的平均推理成本和任务成功率。

2️⃣ 【多Agent协作效率】CurateEvo 的动态数据策展策略与 Doomded from the Start 的早期中止可组成"数据-推理"联合优化管线。验证方式：在一组固定 Agent 任务上，同时应用两种方法，观察较单独使用的叠加收益。

3️⃣ 【跨语言 Agent 鲁棒性】PolyWorkBench 的方法论可复用到团队自己的 Agent 产品中做多语言回归测试。验证方式：选取核心 5 个 Agent 工作流，在英中日三语上执行相同任务并对比成功率与延迟。

---

📊 三、趋势总结

- Agent 评估正在从"英语单场景  → 多语言/多文化/多理论框架"深度扩展，PolyWorkBench 和社会资本建模是两个典型的横纵延伸方向。
- 成本控制成为 Agent 研究的显性主题——早期中止、自适应 rollout、动态数据策展三篇论文从不同维度指向同一个目标：让 Agent 推理更聪明、更经济。
- 多 Agent 系统正在从"能不能合作"走向"怎样更好地合作"——信息论边界、审慎沟通策略、物理约束模拟，意味着 Agent 协作的研究工具箱正在加速丰富。

✅ 已归档：knowledge/daily/2026-07-08/paper-digest.md