# Blocking Issue: AINews Cron Infrastructure

## References
- **imp_85efd6c590cf** (P1, seen 17×): AINews paper-digest cron 持续性缺失
- **imp_c5138650f643** (P1, seen 13×): AINews cron 调度链路中断 / 标准目录结构缺失

## Investigation (2026-07-06 18:39 CST)

### Config audit
- `/Users/study/.openclaw/openclaw.json` → `cron` section contains only `{"maxConcurrentRuns": 8}`
- **No cron job definitions exist.** No heartbeat cron, no paper-digest cron, no scheduled RSS scan jobs.
- All heartbeat polls are running on-demand (manual/trigger-based), not on a schedule.
- Agent `ainews` is registered in `agents.list` but has no associated cron definitions.

### Root cause
The cron infrastructure was never wired up. The `cron` key exists in the config but has zero job entries. The heartbeat functions through manual polling (this session), not through any automated schedule.

### Blocking factors
1. No `cron.jobs[]` array in the configuration — no jobs to execute
2. No paper-digest script or pipeline exists in the workspace that a cron job could invoke
3. No standard directory structure was ever defined/checked in for automated pipelines
4. Requires editing `openclaw.json` to add job definitions, which is a config-level change

### Recommended next steps
1. Define cron jobs in `openclaw.json`:
   - Heartbeat RSS scan: e.g., every 30-60 min
   - Paper digest (arxiv): daily or every 6h
   - GitHub trending: every 6h
2. Create corresponding scripts/handlers in workspace-ainews
3. Wire up agent `ainews` to the cron schedule

### Suggested cron config (for reference)
```json
{
  "cron": {
    "maxConcurrentRuns": 8,
    "jobs": [
      {
        "id": "heartbeat-rss",
        "description": "RSS news scan for ainews agent",
        "schedule": "*/30 * * * *",
        "target": {
          "agentId": "ainews",
          "task": "Scan RSS news sources for AI/tech developments. Follow HEARTBEAT.md. Archive to knowledge/daily/."
        }
      }
    ]
  }
}
```

### Owner
Config-level changes require OpenClaw operator (gateway restart after editing openclaw.json).

### Next action time
Re-evaluate after config changes are applied or if alternative approach (e.g., launchd/cron on macOS) is chosen.
