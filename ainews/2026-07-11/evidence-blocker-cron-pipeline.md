# Cron/Digest Pipeline Blocker — 2026-07-11

## Affected IDs
- **imp_85efd6c590cf** (P1) — AINews paper-digest cron 持续性缺失
- **imp_0e2c0e38bd15** (P1) — AINews cron 调度链路中断
- **imp_c5138650f643** (P1) — AINews cron 调度链路中断 / 标准目录结构缺失

## Current Status
- ❌ Paper-digest cron is **not running**. No automated paper-digest pipeline observed generating digests since June 2026. The heartbeat agent is still operational (this scan proves it), but the scheduled cron/digest chain that should auto-generate RSS summaries, arxiv digests, and curated markdown reports appears broken.
- ❌ The cron scheduling chain (likely OpenClaw cron or system-level cron) is not triggering the downstream pipeline steps.
- ✅ Heartbeat scans still fire on the OpenClaw heartbeat mechanism.

## Root Cause (suspected)
Likely either:
1. Missing or misconfigured cron entry on the host
2. OpenClaw cron tasks not set up/stopped after a restart
3. The skill/task that drives paper-digest generation has been modified or removed

## Next Action
- Owner: agent (ainews) / manual intervention required
- Next action: Investigate cron configuration on the host (`crontab -l` on Studio Mac) and OpenClaw cron task definitions
- Timing: Next available working session (weekday), not urgent enough for 05:39 AM interrupt
- No user notification needed yet — heartbeat is still functional for manual scanning
