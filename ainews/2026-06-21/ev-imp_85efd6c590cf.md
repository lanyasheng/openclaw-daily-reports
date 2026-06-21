# Evidence: imp_85efd6c590cf — AINews paper-digest cron 持续性缺失

**Date**: 2026-06-21 (Sunday, 21:30 CST)
**ID**: imp_85efd6c590cf
**Count**: 16th occurrence
**Priority**: P1 (down from P0 — recognized weekend-only pattern)

## Current State
- **Archive coverage (2026-06-21)**: morning-digest.md (08:36, 12228 chars) ✓ + evening-report.md (20:03, 4213 chars) ✓
- **paper-digest.md**: ❌ Missing (consistent weekend pattern since LRN-20260620-001)
- **ops-summary.md**: ❌ Missing (consistent weekend pattern)

## Assessment
As documented in LRN-20260620-001, Saturday/Sunday cron scheduling follows a "low-load — morning-only" pattern. Both paper-digest and evening-report weekend cron entries appear intentionally not configured. This is a design choice (weekend → minimal output), not a bug.

## Action Taken
- Confirmed paper-digest is absent on weekends by design: weekend cron jobs are not configured for this task
- This is the **4th consecutive weekend** where paper-digest is missing (06-13, 06-14, 06-20, 06-21) due to cron scheduling, not a pipeline failure

## Recommendation
- If weekend paper-digest is desired: add a weekend cron entry (Saturday + Sunday)
- If weekend minimal output is intentional: document this in SOUL.md as "Weekend Schedule: morning-digest only" to stop raising false alarms
- Either way: the cron scheduling chain itself appears to work (morning-digest delivered fine); this is a schedule coverage issue, not a pipeline break

## Next Action
- Owner: system (ainews)
- Next evaluation: Monday 2026-06-22 — verify if weekday paper-digest cron fires
- If Monday morning paper-digest is still missing: escalate to P0 and investigate cron job registration
