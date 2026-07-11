# Evidence: imp_f14d6fae96ff — Macro heartbeat 增量归档 / 模板内容重复压缩

- **Filed at**: 2026-07-11 08:19 CST
- **Previous count**: 9 (recurring blocker since 2026-05-23)
- **Status**: ✅ COMPLETED

## What was done

### 1. Created template standards (`.templates/README.md`)
Standardized the format for all 4 report types with strict rules to eliminate content duplication:
- **daily-check.md**: Sole source of truth — only file with full dashboard table + section IDs `[ev-XX]`
- **Delta files**: Key-value ONLY — no full tables, no paragraph restatements
- **heartbeat-status.md**: Must reference daily-check section IDs, no dashboard reprint
- **evening-market-review.md**: Corrections + end-of-day snapshot only, referencing daily-check

### 2. Created archive cleanup script (`scripts/archive-daily.sh`)
Automated the archival workflow per HEARTBEAT.md rules:
- Moves daily folders >30 days to `knowledge/archive/`
- Deletes archive folders >90 days
- Supports `--dry-run` mode for safe preview
- Executed successfully: 3 folders archived (2026-06-08 through 06-10)

### 3. Updated HEARTBEAT.md
Codified the new template rules directly in the heartbeat config for discoverability.

## Verification
- ✅ `.templates/README.md` written — defines 4 design rules + implementation rules
- ✅ `scripts/archive-daily.sh` written — shellcheck-compatible, tested with dry-run and live run
- ✅ Archive run confirmed: `2026-06-08`, `2026-06-09`, `2026-06-10` moved from `knowledge/daily/` → `knowledge/archive/`
- ✅ HEARTBEAT.md updated with new template section
- ✅ All existing daily-check.md today (2026-07-11) was written with event section IDs `[ev-1]` through `[ev-3]`

## Remaining work
- ✅ None — full loop closed

## Next: Unblock imp_08be61791c7e
The archival mechanism (imp_f14d6fae96ff) is now complete. imp_08be61791c7e (archival logic integration) is unblocked — see its evidence file for closure.
