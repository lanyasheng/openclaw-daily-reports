# Blocker: AINews cron 调度链路中断 / 标准目录结构缺失
**ID:** imp_c5138650f643  
**Date:** 2026-07-07 17:39 CST  
**Status:** ⚠️ Not completed — blocker written

## Current State
- Today's directory structure under knowledge/daily/2026-07-07/ contains: morning-digest.md, paper-digest.md, 00-injected-improvements.md, 01-followup-open-items.md
- RSS scan summaries are written to knowledge/daily/rss_YYYY-MM-DD_HHMM.md (flat, not in dated subdirectory)
- JSON/log outputs are mixed across knowledge/daily/ and knowledge/daily/archive/
- No consistent directory separation between raw RSS data and curated summaries

## Reason Not Fixed
- Requires a deliberate redesign of the ainews agent's file management logic — changes to how RSS scan outputs (.json, .log, .md summaries) are versioned and organized
- This is a structural improvement that needs a focused coding session, not a quick fix during a heartbeat check
- The current flat structure is functional even if not ideal

## Next Action
- Propose standard directory layout for ainews outputs and implement in a dedicated improvement session
- Suggested layout:
  - knowledge/daily/YYYY-MM-DD/raw/rss_HHMM.json — raw RSS data
  - knowledge/daily/YYYY-MM-DD/raw/rss_HHMM.log — fetch logs
  - knowledge/daily/YYYY-MM-DD/summary.md — curated daily summary
  - knowledge/daily/YYYY-MM-DD/heartbeat_HHMM.md — per-heartbeat notes
