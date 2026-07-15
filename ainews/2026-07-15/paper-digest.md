arXiv papers 数据充足（8篇，全部7月14日新论文），直接生成论文速递。

📄 AI 论文速递 | 2026-07-15 12:00

---

**1. Do AI Agents Know When a Task Is Simple? Toward Complexity-Aware Reasoning and Execution**
🔗 https://arxiv.org/abs/2607.13034v1

LLM Agent 在工程和信息学工作流中常见「过度消耗上下文」——面对简单任务也采取"全量读取"策略，反复扫描已经读过的文件和依赖。本文提出了复杂度感知推理框架，让 Agent 在行动前先评估任务复杂度，再选择合适的策略。对 Agent 效率优化有直接参考价值。

**2. PalmClaw: A Native On-Device Agent Framework for Mobile Phones**
🔗 https://arxiv.org/abs/2607.13027v1

手机端原生 Agent 框架。现有 LLM Agent 多运行在桌面或服务器，但移动端有独特的触控交互和传感器能力。PalmClaw 直接在手机上调度工具调用和任务执行，适配移动场景。对移动端 agent 应用开发者值得关注。

**3. Can Induced Emotion Bias LLM Behaviors in Sequential Decision Making?**
🔗 https://arxiv.org/abs/2607.12631v1

当 LLM 被部署为自主 Agent 时，用户的情绪影响是否会改变它们的决策行为？本文发现，当研究者向模型注入特定情绪（如焦虑、乐观）后，Agent 在连续决策任务中的表现显著偏移。这对 Agent 安全、情绪操控防御有警示意义。

**4. PM-Bench: Evaluating Prospective Memory in LLM Agents**
🔗 https://arxiv.org/abs/2607.12385v1

前瞻记忆（Prospective Memory）——即 Agent 在忙于其他任务时记住未来某个时间点/状态要执行某项意图的能力——是 Agent 系统的关键短板。PM-Bench 基于 VirtualHome 构建了一套文本基准来评测这一能力。对 Agent 系统「规划-执行-记忆」长链路有价值。

**5. Speculate with Memory: Lossless Acceleration for LLM Agents**
🔗 https://arxiv.org/abs/2607.12236v1

现有推测执行（Speculative Execution）加速 Agent 时，轻量模型在两次任务间丢弃所有状态，无法从经验中改进预测质量。本文引入记忆机制，让推测器在历史交互中学习更准确的下一步预判，实现了无损加速。与 OpenClaw 的 pipeline 优化思路有技术共鸣。

**6. How Many Tasks Are Enough for Agent Benchmark Decisions?**
🔗 https://arxiv.org/abs/2607.12338v1

Agent Benchmark 跑多少任务才够得出可靠结论？本文通过回放已完成的公开 benchmark 数据，分析了局部运行（部分任务）是否支持与完整运行相同的排序结论。对 Agent 评测成本和结论可信度的权衡提供了量化依据。

**7. Rethinking the Evaluation of Harness Evolution for Agents**
🔗 https://arxiv.org/abs/2607.12227v1

本文指出现有 Agent「自动化 harness 进化」方法中，直接用同一个公开 benchmark 做搜索和最终评估会导致过拟合。呼吁分离搜索和最终评价的数据集。对任何做 Agent 自动调优的团队都有提醒作用。

**8. Who Grades the Grader? Co-Evolving Evaluation Metrics and Skills for Self-Improving LLM Agents**
🔗 https://arxiv.org/abs/2607.12790v1

自我进化的 Agent 系统依赖于一个隐蔽假设：存在可靠的评估指标。但在真实场景中这个指标往往不存在。本文提出了"指标进化循环"——让评估指标和 Agent 技能同步协同进化。与 OpenClaw 自改进回路方向高度相关。

---

**🔬 可实验假设**

1. **Speculate with Memory** 的思路可直接迁移到 OpenClaw 的 pipeline 中——在任务间保留推测器的状态缓存，降低重复预测成本。
2. **PalmClaw** 的移动端工具调度设计可作为 OpenClaw 未来移动端 Agent 框架的参考架构。
3. **Co-Evolving Metrics** 的自改进回路与 OpenClaw 现有的 improvement-generator 循环可以结合——让 eval 本身也成为可进化的组件。

---

**📊 趋势总结**

- 本周 arXiv 论文高度聚焦 Agent 系统的效率和可靠性，尤其是评估方法和记忆机制两大方向
- "自我进化 Agent"成为持续热点，但学术界也开始反思评估指标本身的可靠性问题
- 移动端 Agent 和情绪安全是新兴子方向，值得提前布局关注

✅ 已归档：knowledge/daily/2026-07-15/paper-digest.md