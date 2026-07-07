# Evidence — imp_f14d6fae96ff — 增量归档 / 模板内容重复压缩

**Date:** 2026-07-07 08:43 CST (updated 17:04 CST)
**Status:** ✅ Step 1 DONE, ✅ Step 2 DONE, Steps 3-5 deferred

## What Was Done

**Step 1 (P1): HEARTBEAT.md updated with archive rules section** ✅
- Added `## 归档规则` section to `/Users/study/.openclaw/workspace-macro/HEARTBEAT.md`
- Content includes:
  - Daily file structure convention (daily-check.md as full report, heartbeat-status.md / evening-market-review.md in incremental format)
  - Incremental format rules for non-morning reports (delta-only data, references to morning report)
  - Cleanup rules (30-day retention in knowledge/daily/ → archive/, 90-day retention in archive/)
  - Improvement item closure process (evidence/blocker file convention)

**Step 2 (P1): ARCHIVE_GUIDE.md created** ✅
- Created `/Users/study/.openclaw/workspace-macro/knowledge/daily/ARCHIVE_GUIDE.md` at 17:04 CST
- Contains: retention rules, archive commands (manual + batch), file structure convention, template conventions, improvement item lifecycle

## Steps 3-5 Still Deferred

| Step | Status | Reason |
|:----:|:------:|--------|
| 3 (daily-check.md template cleanup) | ⏳ Deferred | P2 — requires re-checking current template; low urgency |
| 4 (archive script) | ⏳ Deferred | P2 — manual `find + mv` sufficient for now |
| 5 (archive old dirs) | ⏳ Deferred | P2 — no immediate space pressure |

## Related IDs
- `imp_f14d6fae96ff` — macro heartbeat 增量归档 / 模板内容重复压缩
- `imp_08be61791c7e` — macro 归档逻辑 / 增量归档机制
