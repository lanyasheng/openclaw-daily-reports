# Blocker: imp_f14d6fae96ff — Macro heartbeat 增量归档 / 模板内容重复压缩

- **Owner**: macro heartbeat system
- **Priority**: P1
- **Count**: 7
- **Blocking reason**: This is a fundamental structural improvement to the heartbeat delta template format and archive logic (compressing redundant content). Cannot be addressed during live heartbeat polls — requires dedicated development session to redesign templates, implement diff-based delta generation, and update the archive rotation logic. Requires coordination between heartbeat, daily-check, and evening-review templates.
- **Next action**: Schedule a dedicated improvement session (non-peak hours) to redesign the heartbeat delta template for diff-only output, consolidate/remove redundant reference tables, and implement automatic archive of content/report/ directory per HEARTBEAT.md rules.
- **Next action time**: Next available off-peak window (e.g., during weekend or low-volatility period)
