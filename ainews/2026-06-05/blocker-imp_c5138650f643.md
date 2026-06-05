# Blocker: imp_c5138650f643 — AINews cron 调度链路中断 / 标准目录结构缺失

**Date**: 2026-06-05 21:30 CST
**Owner**: ainews agent (via daily reflection)
**Related ID**: `imp_c5138650f643`
**Count**: 14th bump / 13rd in open-items ledger

## Current Status

- ⛔ No cron scheduling automation implemented or restored
- ⛔ Today: 0/3 standard files produced (morning-digest.md, paper-digest.md, evening-report.md all missing)
- ⛔ Only heartbeat manual evidence and blocker files exist in knowledge/daily/2026-06-05/
- ⛔ Automated cron task status (lastRunStatus/lastExecutionTime) remains "?" in jobs.json
- ✅ RSS aggregator script functional when manually invoked (verified at 06:11 and 06:39)

## Root Cause (Reaffirmed)

The cron scheduling has never been implemented. This is not a "broken" pipeline — it was never configured with automation. The heartbeat system provides manual fallback but does not replace scheduled runs.

## Blocker

**No owner has been assigned or accepted the task of setting up the cron automation.** 
- The 14 prior bumps have produced evidence files but no resolution.
- Ainews agent lacks the system-level permissions/configuration access to add cron jobs to OpenClaw's scheduling system.
- The `--output` flag usage pattern test was noted at 06:39 but no permanent change was applied.

## Suggested Next Action for Owner / Boss

Two binary choices remain:

1. **Implement cron scheduling** (preferred):
   - Add to OpenClaw's cron/jobs.json or system-level crontab
   - Command: `cd /Users/study/.openclaw/workspace-ainews && python3 skills/ai-news-aggregator/scripts/rss_aggregator.py --limit 200 --days 1 --output knowledge/daily/ >> logs/rss_cron.log 2>&1`
   - Frequency: every 2 hours

2. **Accept manual-only** (fallback):
   - Document that RSS aggregator is intentionally manual
   - Fix the heartbeat startup check to auto-trigger first feed of day
   - Close imp_c5138650f643 as "accepted limitation"

**This item should be escalated to boss for decision if not resolved by 2026-06-06.**
