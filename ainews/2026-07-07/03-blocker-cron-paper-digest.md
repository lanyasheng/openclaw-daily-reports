# Blocker: AINews paper-digest cron 持续性缺失
**ID:** imp_85efd6c590cf  
**Date:** 2026-07-07 17:39 CST  
**Status:** ⚠️ Not completed — blocker written

## Current State
- Paper digest was generated manually at 12:36 CST today (paper-digest.md, 8 arxiv papers)
- No automated cron/periodic scheduler is configured for paper-digest generation
- The heartbeat cycle relies on heartbeat polls to trigger operations; there is no time-based cron outside of poll cycles
- Web search is currently broken (Ollama 404), which limits automated source diversity

## Reason Not Fixed
- Root cause: This requires OpenClaw cron/trigger configuration changes (scheduling cron jobs for specific times) which is an infrastructure-level change beyond the scope of individual heartbeat cycles
- The paper-digest *is* being generated regularly, just on-demand rather than on a fixed schedule
- No dedicated cron configuration has been set up for ainews agent to auto-trigger paper-digest at specific UTC times

## Next Action
- Re-assess when OpenClaw cron/trigger infrastructure is updated
- Consider documenting the manual paper-digest trigger command for easy replication
- Target: move to automated 06:00 UTC daily paper-digest generation
