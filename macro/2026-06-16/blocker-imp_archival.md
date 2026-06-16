# Blocker — Macro Archival / Template Compression Improvements

## IDs
- imp_f14d6fae96ff — Macro heartbeat incremental archiving / template content deduplication
- imp_08be61791c7e — Macro archive logic / incremental archive mechanism

## Owner
macr

## Status
🚧 **Blocked — Requires Dedicated Improvement Session**

## Issue
These items (appearing 5x and 4x respectively) call for refactoring the heartbeat archival system to:
1. Incrementally archive rather than full-dump each heartbeat
2. Compress/deduplicate repeated template content (header/footer/table structures)
3. Establish a consistent archive-rotation strategy

## Why Blocked Now
This heartbeat (06:34 CST) falls into a **super-macro-event window** (China data pending, BOJ decision within hours, FOMC Day 1 starting, US Retail Sales tonight). Running an architectural refactor during active monitoring conflicts with the primary HEARTBEAT.md mandate of monitoring macro events.

## Next Action
- **Timing:** Run a dedicated `sessions_spawn` improvement session during the next quiet window (e.g., after BOJ/RBA decisions clear but before FOMC decision tomorrow, or during Fri-Sat weekend calm).
- **Scope:** The improvement session should analyze all heartbeat files in the workspace-macro/knowledge/ tree, identify repeated sections, design a template-based incremental logging format, and implement a rotation/compression script.
- **Verification:** After implementation, run a 24-hour test cycle to confirm incremental logging works without data loss.

## Evidence Links
- `/Users/study/.openclaw/workspace-macro/knowledge/daily/2026-06-16/01-followup-open-items.md` — source of the follow-up items
- `/Users/study/.openclaw/workspace-macro/knowledge/daily/` — all heartbeat files showing template repetition pattern
