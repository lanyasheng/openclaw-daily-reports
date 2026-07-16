# Follow-up Open Items [2026-07-16]

这些事项来自反思闭环账本。今天执行或无法执行时，必须在同目录写入证据文件，并引用对应 ID。

| ID | Priority | Count | Task | Required evidence |
|---|---|---|---:|---|
| imp_d60357465ff5 | P0 | 54 | Content 发布闭环 / publish queue / 发布回执 | ✅ written → `blocker-imp_d60357465ff5.md` (架构性开发任务，需独立 session) |
| imp_fb69092f27cb | P1 | 36 | Content feedgrab 标准素材链未执行 | ✅ written → `blocker-imp_fb69092f27cb.md` (依赖 publish queue 设计) |
| imp_df587e127123 | P1 | 4 | Content Ripple 传播预测从未执行 (TOOLS.md P0强制) | ✅ written → `blocker-imp_df587e127123.md` (建议标记为 depends on publish queue) |

## 11:32 午间评估

### 三阻塞项统一结论
三个改进项（imp_d60357465ff5 / imp_fb69092f27cb / imp_df587e127123）均属于**架构性基础设施开发**，不能在 heartbeat 扫描间隙执行。推荐处理路径：

1. **分配独立 sub-agent session** 进行全面的 Content Pipeline 架构设计
2. 优先设计发布队列（publish queue）→ 素材链 pipeline → Ripple 预测引擎
3. 最佳执行窗口：18:00 晚间扫描后 2h 安静时段，或 06:00 凌晨安静时段

### 今日内容计划
按 `content-ideas.md` 排期：
- 今晚 20:00 — 选题 3 AI 伴侣下线（日记体→小红书）
- 今晚 21:00 — 选题 1 Inkling 975B（X Thread）
- 今晚 22:00 — 选题 2 国行苹果 AI（小红书）
- 待确认：是否有已生成的初稿可用（需检查 publish/ 目录）

## Closing Rule
- 完成：写一个包含该 ID 的证据文件，说明做了什么、验证结果、后续是否需要跟踪。
- 未完成：写一个包含该 ID 的 blocker 文件，说明 owner、阻塞原因、下一次动作时间。
- 晚间反思不得只重复问题，必须引用 ID 和证据路径。
