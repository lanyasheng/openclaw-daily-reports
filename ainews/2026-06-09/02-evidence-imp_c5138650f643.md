# Evidence: imp_c5138650f643 — AINews cron 调度链路中断 / 标准目录结构缺失

**ID**: imp_c5138650f643
**Date**: 2026-06-09 21:30 CST
**Status**: open (partial recovery)

## Check on 2026-06-09

knowledge/daily/2026-06-09/ 目錄包含：
- morning-digest.md ✅
- evening-report.md ✅
- paper-digest.md ❌（缺失）

相比 05-23 的完整 3/3 产出，今日为 2/3。Paper-digest cron 任务调度仍不稳定。

## 证据总结
- 晨报和晚报产出正常（含 URL、影响评估、高质量情报）
- Paper-digest 持续缺失，cron 调度链路未完全恢复
- Autoresearch-lite 降级运行（2/4 输入缺失）

## 下一次动作
- 优先排查 paper-digest cron 任务状态
- 若在明日（2026-06-10）仍缺失，考虑在 cron/jobs.json 中检查其 lastRunStatus
- 此问题已计数 14 次，建议升级为 P0 并触发人工运维会话
