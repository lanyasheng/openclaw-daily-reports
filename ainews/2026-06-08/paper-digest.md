Now I have all the information needed. Let me write the digest and then archive it.

📄 AI 论文速递 | 2026-06-08 12:00

本周论文专题围绕一个核心主题——**AI Planning（AI 规划）**，共 8 篇高质量论文，覆盖从显式建模、架构映射到推理最优性和启发式进化的关键进展。这批论文集中反映了学界正在系统性地将古典规划思想（搜索、启发式、验证）嫁接到大模型上的趋势。

---

**1. Model-First Reasoning LLM Agents: Reducing Hallucinations through Explicit Problem Modeling**
https://arxiv.org/abs/2512.14474
作者提出 **Model-First Reasoning (MFR)** 范式：让 LLM 先显式构建问题模型（定义实体、状态变量、动作和约束），再生成求解方案。在医疗排程、路径规划、资源分配等场景中，MFR 相比 Chain-of-Thought 和 ReAct 显著降低了约束违背率。消融实验证实「显式建模阶段」是核心增益来源。一句话启示：很多 LLM 规划失败不是推理能力不足，而是缺乏对问题的精确表征。
**影响评估:** ⭐⭐⭐⭐⭐ — 直接对标 Agent 系统的核心痛点（幻觉/约束违规），MFR 是一个可工程化的方向。

**2. AI Planning Framework for LLM-Based Web Agents**
https://arxiv.org/abs/2603.12710
将 Web Agent 架构系统映射到经典规划范式：Step-by-Step → BFS、Tree Search → Best-First Tree Search、Full-Plan-in-Advance → DFS。提出 5 个超越「成功率」的轨迹质量评估指标，并发布了 794 条人工标注的 WebArena 轨迹数据集。实验发现 Step-by-Step 在人类轨迹对齐度上占优（38%），但 Full-Plan-in-Advance 在元素准确率上达 89%。
**影响评估:** ⭐⭐⭐⭐ — 对 Agent 架构选择有实际指导价值，评估指标具有通用性。

**3. Governing AI-Assisted Security Operations: A Design Science Framework**
https://arxiv.org/abs/2605.09534
面向工程管理层的论文——如何在渗透测试、安全运营中引入 Generative AI / RAG / 编码 Agent 而不削弱问责性、隐私和审计能力。提出了一套设计科学框架，涵盖安全运营中 AI 管控的决策支持系统。
**影响评估:** ⭐⭐⭐ — 更适合安全管理者的决策参考，技术深度有限但场景相关性高。

**4. Analysis of Optimality of Large Language Models on Planning Problems**
https://arxiv.org/abs/2604.02910
经典 Blocksworld 和 Path-Star 图上的系统性实验：增强推理的 LLM 比传统 satisficing 规划器（如 LAMA）表现更好；在复杂多目标配置下，LLM 追踪理论最优极限的精度接近完美。作者提出两种假设解释——通过推理 token 执行「算法仿真」和「几何记忆」拓扑结构。
**影响评估:** ⭐⭐⭐⭐⭐ — 首次系统论证 LLM 在多步规划中接近理论最优，对「LLM 只是模式匹配」的观点构成挑战。

**5. LLM-Evolved Domain-Independent Heuristics for Symbolic AI Planning**
https://arxiv.org/abs/2605.29649
让 LLM 通过**进化搜索**生成领域无关的启发式函数（纯 C++），首次超越手工设计的最优启发式。使用 MAP-Elites 存档来维护「信息量-速度」帕累托前沿。从盲目启发式种子进化的效果优于从 FF 强启发式种子起步。生成的程序是纯 C++，可即插即用。
**影响评估:** ⭐⭐⭐⭐⭐ — LLM 生成启发式的关键突破，证明了 LLM 可以作为「算法工程师」辅助甚至超越传统启发式设计。

**6. Two-Fidelity Best-Action Identification for Stochastic Minimax Tree**
https://arxiv.org/abs/2606.01708
研究在随机 Minimax 树中「双保真度最佳动作识别」问题——即在高成本精确评估和低成本启发式评估之间做最优预算分配。直接对标 LLM 长 rollout + MCTS 的组合场景。
**影响评估:** ⭐⭐⭐ — 偏理论，但 MCTS + LLM rollout 在推理时的资源分配问题有实际呼应。

**7. On the Ability of Transformers to Verify Plans**
https://arxiv.org/abs/2603.19954
引入 **C*-RASP** 扩展框架，分析 decoder-only 模型在对象数量（词汇表）和序列长度同时增长时的长度泛化问题。识别了一类古典规划领域，在其中 Transformer 可以「可证明地学会验证长计划」。实验支持理论发现。
**影响评估:** ⭐⭐⭐⭐ — 理论贡献大，为「LLM 能否保证规划正确性」提供了形式化分析框架。

**8. Efficient Test-time Inference for Generative Planning Models**
https://arxiv.org/abs/2606.00618
将经典 Open-Closed List (OCL) 搜索改造为生成式规划模型的推理框架：用一个生成模型做快速 rollout、一个启发式模型做优先级排序。在多个组合规划域中，计算效率和解质量均优于神经符号搜索基线和传统求解器。
**影响评估:** ⭐⭐⭐⭐ — 高效的推理时优化思路，对需要大量 rollout 的 Agent 系统有参考价值。

---

**可实验假设**

1. **MFR + Web Agent 结合**：将 Model-First Reasoning 的显式建模阶段嵌入 Web Agent 系统，有望在复杂多步 Web 任务中减少约束违例和上下文漂移。
2. **LLM 进化启发式 + 实际 Planner 集成**：将 Paper #5 中 LLM 进化出的 C++ 启发式集成到经典规划器（Fast Downward 等），在未见过的任务域上测试覆盖率和求解时间。
3. **双保真度策略在 Agent 推理管线中的应用**：用 Paper #6 的 BAI 框架来动态决定 LLM 推理时的 rollout 深度 vs. 启发式替代，优化 token 预算分配。

---

**趋势总结**

- 本周论文的高度一致性本身就反映了领域趋势：**AI Planning 正经历一次「古典回归」**——学界开始用搜索、启发式、验证等经典方法论系统化地分析和改进 LLM 在规划上的表现，而非单纯依赖规模。
- 几个关键信号：显式建模（MFR）优于隐式推理、LLM 可以进化出超越人工设计的启发式、Transformer 可以形式化地证明规划验证能力——这些都指向 **「混合架构」是 Agent 规划的未来**。
- 对日常 Agent 开发的提示：**不要把所有推理负担交给 LLM 的「暗箱」**，引入显式建模层和结构化搜索可以带来可量化的提升。

✅ 已归档：knowledge/daily/2026-06-08/paper-digest.md