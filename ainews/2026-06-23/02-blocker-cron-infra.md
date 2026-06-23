# Blocker: AINews Cron Jobs Timing Out [2026-06-23]

## Referenced IDs
- `imp_85efd6c590cf` (P1, count=17) — AINews paper-digest cron 持续性缺失
- `imp_c5138650f643` (P1, count=13) — AINews cron 调度链路中断 / 标准目录结构缺失

## Revised Analysis

### The cron infrastructure IS installed — but jobs are timing out

Previous assessments assumed the cron scheduling was missing. This is **incorrect**. OpenClaw's native cron (jobs.json) has all ainews jobs properly configured:

| Job | Schedule | Status | Last Run |
|-----|----------|--------|----------|
| ainews-morning-digest | 08:30 daily | ✅ OK | 42m ago |
| ainews-archive-consistency-check | 08:36/12:36/20:36 | ✅ OK | 31m ago |
| ainews-knowledge-github-sync | 21:40 | ✅ OK | 12h ago |
| ainews-daily-ops-summary | 21:50 | ✅ OK | 11h ago |
| autoresearch-ainews-generate | 22:05 | ✅ OK | 11h ago |
| **ainews-paper-digest** | **12:00 daily** | **❌ ERROR** | **~10min timeout** |
| **ainews-evening-report** | **20:00 daily** | **❌ ERROR** | **timeout** |
| daily-reflection-ainews | 21:30 | ❌ ERROR | timeout |
| study-brain-distill | 23:00 | ❌ ERROR | timeout |

### Paper Digest Root Cause
- **Error diagnostic**: `cron: job execution timed out`
- **Duration**: ~609s (~10 min) before being killed by cron timeout
- **Last success (manual)**: June 21 22:49 — ran in 127s (2 min), delivered to Discord
- **Pattern**: 5 consecutive cron timeouts since early June
- **Model**: deepseek/deepseek-v4-flash (high latency?)
- Manual runs from non-busy hours succeed quickly; scheduled 12:00 runs time out

### Evening Report Root Cause
- Same timeout pattern — likely similar root cause
- Mixed success/failure pattern over the past month

## Blocker Analysis

### Owner
Agent cron setup — `ainews` agent's `openclaw cron` job configuration.

### Root Cause
Not infrastructure absence but **execution timeout**: the cron session is killed before the agent finishes processing. Suspect causes:
1. High model latency (deepseek/deepseek-v4-flash) during peak hours
2. Paper digest at 12:00 coincides with heavy Discord activity or system load
3. Cron timeout window is too short for the current workload

### Next Actions
1. **Short-term**: Manually trigger paper digest at 12:00 today to confirm if it's a reproducible timeout vs. transient issue
2. **Medium-term**: 
   - Increase cron timeout (not yet available via `openclaw cron edit`, would need config change)
   - Switch paper-digest to a faster model (e.g. deepseek/deepseek-chat or qwen3.5-plus which worked historically)
   - Or run at a different time (e.g. 13:00 when system load is lower)
3. **Remove from follow-up only after verifying one successful paper-digest cron run**
