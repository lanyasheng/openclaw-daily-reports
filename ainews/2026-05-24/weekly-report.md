# AI 周报 Part 2 | 2026-W21（5/19 - 5/24）

---

## 项目/论文 TOP 清单 + 下周行动建议

### 🏆 GitHub 项目 TOP 10

| # | 项目 | 星数 | 方向 |
|---|------|------|------|
| 1 | [obra/superpowers](https://github.com/obra/superpowers) | 204K | Agentic 技能框架 |
| 2 | [multica-ai/andrej-karpathy-skills](https://github.com/multica-ai/andrej-karpathy-skills) | 150K | LLM 编码最佳实践 |
| 3 | [anthropics/claude-plugins-official](https://github.com/anthropics/claude-plugins-official) | 26K | Claude 官方插件 |
| 4 | [K-Dense-AI/scientific-agent-skills](https://github.com/K-Dense-AI/scientific-agent-skills) | 25K | 科研 Agent 技能 |
| 5 | [Lum1104/Understand-Anything](https://github.com/Lum1104/Understand-Anything) | 22K | 代码知识图谱 |
| 6 | [humanlayer/12-factor-agents](https://github.com/humanlayer/12-factor-agents) | 22K | 生产级 Agent 原则 |
| 7 | [colbymchenry/codegraph](https://github.com/colbymchenry/codegraph) | 20K | 预索引代码图谱 |
| 8 | [Imbad0202/academic-research-skills](https://github.com/Imbad0202/academic-research-skills) | 20K | 学术研究技能包 |
| 9 | [ChromeDevTools/chrome-devtools-mcp](https://github.com/ChromeDevTools/chrome-devtools-mcp) | 41K | 浏览器调试 MCP |
| 10 | [rohitg00/agentmemory](https://github.com/rohitg00/agentmemory) | 17K | Agent 持久记忆 |

### 📄 论文 TOP 5

| # | 论文 | 贡献 |
|---|------|------|
| 1 | [IdleSpec](https://arxiv.org/abs/2605.22154) | 空闲时间推测性规划，串行→流水线并行 |
| 2 | [GraphFlow](https://arxiv.org/abs/2605.22566) | 图结构 Agent workflow，动态路由+并行 |
| 3 | [Model-First Reasoning](https://arxiv.org/abs/2512.14474) | 先构建数学模型再推理，降低幻觉 |
| 4 | [What Do Agents Communicate?](https://arxiv.org/abs/2605.20548) | 多 Agent 信息交换模式刻画 |
| 5 | [Agentic Compilation](https://arxiv.org/abs/2604.09718) | 编译过程 Agent 化，减少 LLM 重跑 |

### 🎯 下周行动建议（8 条）

1. **[P0] 评估 Skill 生态整合** — Karpathy Skills、Anthropic 插件目录、Chrome DevTools MCP 三条线同时爆发，Skill 标准化已成行业共识。建议研究内容结构，考虑适配 OpenClaw Skill。
2. **[P0] 重新评估模型选型成本** — DeepSeek 永久 75% 折扣后，V4-Pro 输出价格仅为 GPT-5.5 的 1/34。建议对高频 Agent 任务进行成本对比测试。
3. **[P0] 评估 codegraph 集成方案** — 代码知识图谱可直接提升 Agent 代码理解能力，降低 token 消耗。建议本周完成 POC。
4. **[P1] 跟踪 MCP 企业部署** — Anthropic MCP 隧道 + 自托管沙箱 + Chrome DevTools MCP，MCP 正成为 Agent 交互事实标准。
5. **[P1] 关注 Computer Use 移动端** — Codex iPhone 模拟器是信号弹，移动端 Agent 自动化可能成为下一个热点。
6. **[P1] 研究 Agent 记忆基础设施** — TencentDB Agent Memory + GBrain + AgentMemory 三线共振。评估引入结构化持久记忆方案。
7. **[P2] IdleSpec + GraphFlow 组合实验** — 推测性规划嵌入图工作流引擎，可能实现 2-3x 加速。设计实验方案。
8. **[P2] 关注 AI 监管政策分化** — 美国宽松化 vs 亚洲规范化。建立 AI 监管政策跟踪机制。

### 📊 一周话摘要

> 2026-W21 的 AI 世界被三个核心叙事统治：**Skill 生态爆发**（Karpathy 150K 星引爆标准化趋势）、**Agent 基础设施成熟**（记忆层+知识图谱+MCP 隧道+自主部署协议同日涌现）、**成本战白热化**（DeepSeek 永久 75% 折扣+Microsoft 取消 Claude Code+Gemini 3.5 Flash 成本 5.5x）。竞争维度正从"谁的模型更强"全面转向"谁的生态更好、谁的成本更低、谁的 Agent 更可靠"。

---

*归档: knowledge/weekly/2026-W21.md | 2026-05-24 10:00 CST*
