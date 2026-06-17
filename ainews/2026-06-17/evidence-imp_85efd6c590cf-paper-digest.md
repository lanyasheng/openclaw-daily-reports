# Evidence: imp_85efd6c590cf — Paper digest cron 持续性缺失

**Date**: 2026-06-17 13:40 CST
**Owner**: ainews heartbeat
**Status**: open

## What was checked
- 12:00 cron slot for `ainews-paper-digest` — `archive-consistency-check` at 12:40 confirmed `missing-no-session`
- No `paper-digest.md` in `knowledge/daily/2026-06-17/` as of 13:40
- cron/jobs.json shows the job is configured (`expr: 0 12 * * *`, `tz: Asia/Shanghai`) but `lastRunStatus`/`lastExecutionTime` are `?` (persistent tracking issue)
- Last successful paper-digest was 2026-06-08 (9 days ago)

## Root cause hypothesis
Cron scheduler metadata tracking is broken (`lastRunStatus=?` across all 79 jobs). The job likely isn't dispatching sessions at all. This is the same issue as imp_c5138650f643 (cron scheduling chain broken).

## Impact
- Missing paper digest for today
- autoresearch-lite will have degraded input tonight (missing 1/4 standard inputs)
- Reader misses daily paper curation

## Next action
1. Track in evening reflection with `missing-no-session` status
2. Consider manual paper digest generation if arXiv RSS feeds still accessible (they are working today)
