# Blocker — Paper Digest Cron (imp_85efd6c590cf, imp_0e2c0e38bd15, imp_c5138650f643)

**ID**: imp_85efd6c590cf, imp_0e2c0e38bd15, imp_c5138650f643
**Date**: 2026-07-16 07:39 CST
**Owner**: ainews agent (Ongoing)

## Current State

- Crontab exists with heartbeat guardian, network guardian, memory maintenance, task callback watcher, daily distill, and daily reports sync.
- No cron job specifically for paper digest (arXiv paper fetching & summarization).
- `scripts/arxiv_papers.py` exists but is not in crontab.
- RSS aggregation is handled manually via heartbeat scans, not by cron.

## Blocker Analysis

| ID | Root Cause | Next Action |
|---|---|---|
| imp_85efd6c590cf | No cron integration for arxiv_papers.py | Need to add a scheduled job (e.g., daily at 08:00/20:00) |
| imp_0e2c0e38bd15 | No cron-based feed/RSS polling for AI news | RSS aggregator exists (scripts/rss_aggregator.py) but not in crontab |
| imp_c5138650f643 | No standard directory structure for daily digest output | knowledge/daily has flat files with inconsistent naming |

## Recurrence Count

This is the 21st / 17th / 13th time these items have been flagged. They cannot be resolved in a heartbeat context because:

1. Adding cron jobs requires a separate subagent or manual edit to crontab
2. The paper-digest pipeline design needs scoping (which sources, output format, storage structure)
3. Requires explicit user approval for crontab changes

## Recommended Resolution Path

- Spawn a dedicated subagent to design and implement the paper-digest cron pipeline
- Define target directory: `knowledge/daily/digest/YYYY-MM-DD/`
- Add two cron entries: arXiv daily at 08:00 CST, RSS poll at 22:00 CST
- Rename old heartbeat flat files gradually to match new structure

**Next check**: Next heartbeat scan — verify if subagent has been spawned for this.
