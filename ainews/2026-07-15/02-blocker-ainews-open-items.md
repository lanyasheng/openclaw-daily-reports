# Blocker: AINews P1 Open Items (imp_85efd6c590cf / imp_0e2c0e38bd15 / imp_c5138650f643)
**Date**: 2026-07-15 21:30 CST
**Owner**: operator (ainews cannot self-fix)
**Root cause**: `/Users/study/.openclaw/openclaw.json` — cron.jobs array is **empty** (zero jobs defined).

## Status per item

| ID | Status | Reason |
|---|---|---|
| imp_85efd6c590cf | blocked | Ainnews paper-digest cron 缺失，根因：openclaw.json cron.jobs 为空数组，非运行时异常 |
| imp_0e2c0e38bd15 | blocked | AINews cron 调度链路中断，根因同上 — 无 job 定义，调度器无所调度 |
| imp_c5138650f643 | blocked | 标准目录结构缺失，根因同上 — 无 cron 任务执行，自然无归档 |

## Blocker details
- **What is blocked**: cron 自动调度 + 标准目录结构产出
- **Why it can't be fixed by ainews**: openclaw.json 是 operator 层配置文件，需要编辑 cron.jobs 数组并重启 Gateway 方能生效
- **Evidence of root cause**: `cat /Users/study/.openclaw/openclaw.json | python3 -c "import json,sys; d=json.load(sys.stdin); print(d.get('cron',{})); print('jobs:', d.get('cron',{}).get('jobs',[]))"`
- **Manual operation needed**: 编辑 openclaw.json 的 cron.jobs，添加 ainews-morning-digest / ainews-paper-digest / ainews-evening-report 三个任务定义，然后 `openclaw gateway restart`
- **Next action time**: 下次 operator 介入时（无预设时间）

## 今日替代方案
今日 3 份目标文件（morning-digest.md ✅ / paper-digest.md ✅ / evening-report.md ✅）均已通过手动触发产出并完整归档。但依赖 cron 自动调度的问题仍未解决。
