# Evidence: imp_08be61791c7e — Macro 归档逻辑 / 增量归档机制

- **Filed at**: 2026-07-11 08:19 CST
- **Previous count**: 4 (blocked on imp_f14d6fae96ff)
- **Status**: ✅ COMPLETED

## What was done

This task was fully blocked by `imp_f14d6fae96ff` (template redesign + archive script). With that completed, this task is now resolved:

### 1. Archive mechanism deployed
The `scripts/archive-daily.sh` script handles:
- Automatic detection of daily folders older than 30 days
- Move from `knowledge/daily/` → `knowledge/archive/`
- Automatic cleanup of archive folders older than 90 days
- Safe `--dry-run` preview mode

### 2. Template standards deployed
The `.templates/README.md` defines the incremental delta format:
- Delta files are key-value only (no full table reprints)
- heartbeat-status.md references daily-check.md section IDs
- evening-market-review.md references section IDs for corrections

## Verification
- ✅ Archive script exists and tested (3 folders archived)
- ✅ Template README exists and codifies incremental format
- ✅ HEARTBEAT.md references both

## Next
- No further action needed. This task is fully closed.
