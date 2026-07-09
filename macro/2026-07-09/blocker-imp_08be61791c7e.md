# Blocker: imp_08be61791c7e — Macro 归档逻辑 / 增量归档机制 / imp_f14d6fae96ff

- **Owner**: macro heartbeat system
- **Priority**: P1
- **Count**: 4
- **Blocking reason**: This item is a dependency of imp_f14d6fae96ff (heartbeat archive/compression). The archive rotation (30d daily → 90d archive → system cleanup) and content/report/ cleanup (14d) are not yet automated. Requires implementing a cron-based archive cleanup script. Cannot be implemented during live heartbeat polls.
- **Next action**: After imp_f14d6fae96ff template redesign is complete, implement a scheduled archive cleanup task for:
  1. knowledge/daily/YYYY-MM-DD/ → archive/ after 30 days
  2. archive/ cleanup after 90 days
  3. content/report/ cleanup after 14 days
- **Next action time**: Dependent on imp_f14d6fae96ff resolution; next available off-peak window.
