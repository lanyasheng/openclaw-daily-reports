# Blocker: imp_c5138650f643 — AINews cron 调度链路中断 / 标准目录结构缺失

**Date**: 2026-06-20 21:30 CST
**Agent**: ainews
**Priority**: P1 | Count: ×13

## Status: UNRESOLVED — partial recovery observed but not sustained

### Blocking Reason
- Cron scheduler state tracking in `cron/jobs.json` shows `lastRunStatus/lastExecutionTime` as "?" for all ainews tasks
- Today's knowledge/daily/2026-06-20/ contains only morning-digest.md — standard three-file structure (morning-digest + paper-digest + evening-report) is still incomplete
- On weekends, observed pattern is 1-2 files only (morning-digest or evening-report)
- Root cause: Requires operator to verify and restore cron scheduling, or to redesign the cron -> agent dispatch pipeline

### Evidence Path
- `knowledge/daily/2026-06-20/morning-digest.md` ✓ (present, 08:36)
- `knowledge/daily/2026-06-20/paper-digest.md` ✗ (missing — linked to imp_85efd6c590cf)
- `knowledge/daily/2026-06-20/evening-report.md` ✗ (missing — no cron dispatch today)

### Next Action
- Report aggregated count (×13) to ops heartbeat
- No change this cycle — requires operator to verify cron/jobs.json dispatch and scheduler status
- Next re-check: next daily reflection cycle
