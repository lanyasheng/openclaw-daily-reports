# Follow-up Open Items [2026-07-06]

这些事项来自反思闭环账本。今天执行或无法执行时，必须在同目录写入证据文件，并引用对应 ID。

| ID | Priority | Count | Task | Required evidence |
|---|---|---:|---|---|
| imp_f14d6fae96ff | P1 | 5 | Macro heartbeat 增量归档 / 模板内容重复压缩 | ✅ `incremental-archive-design.md` 已产出 |
| imp_08be61791c7e | P1 | 4 | Macro 归档逻辑 / 增量归档机制 / imp_f14d6fae96ff | ✅ `incremental-archive-design.md` + `blocker-archive-optimization.md` 已更新 |

## Evidence Paths
- `incremental-archive-design.md` — 增量归档完整设计方案（含5步实施计划）
- `blocker-archive-optimization.md` — 更新了实施进度（设计已产出，待周四前实施）
- `evening-market-review.md` — 晚间市场总结（增量格式示范）

## Closing Rule
- 完成：写一个包含该 ID 的证据文件，说明做了什么、验证结果、后续是否需要跟踪。
- 未完成：写一个包含该 ID 的 blocker 文件，说明 owner、阻塞原因、下一次动作时间。
- 晚间反思不得只重复问题，必须引用 ID 和证据路径。
