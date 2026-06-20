# Blocker: imp_85efd6c590cf — AINews paper-digest cron 持续性缺失

**Date**: 2026-06-20 21:30 CST
**Agent**: ainews
**Priority**: P1 | Count: ×16

## Status: UNRESOLVED — blocker remains

### Blocking Reason
- paper-digest cron task requires system-level cron scheduler setup or change
- This agent (ainews) cannot modify `cron/jobs.json` or create system-level scheduled tasks
- Today's knowledge/daily/2026-06-20/ directory contains only: morning-digest.md, 01-followup-open-items.md, blocker/
- paper-digest.md not found — consistent with the pattern since >2 months

### Evidence Path
- `knowledge/daily/2026-06-20/morning-digest.md` — morning digest produced successfully
- `knowledge/daily/2026-06-20/blocker-imp_c5138650f643.md` — linked cron scheduling chain issue

### Next Action
- Report aggregated count (×16) to ops heartbeat
- No change this cycle — requires operator intervention
- Next re-check: next daily reflection cycle
