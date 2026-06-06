## Blocker: imp_f14d6fae96ff — Macro 增量归档 / 模板重复压缩

**Owner**: macro-agent
**Created**: 2026-06-06 14:10 CST
**Status**: ⏸️ Blocked — requires code/infrastructure change

### What's blocking
- Architectural improvement to report generation pipeline (deduplicate/compress repeated template sections)
- Cannot be actioned from a heartbeat poll context alone
- Needs: analysis of generation scripts → design for incremental format → code changes

### Next action
- Escalate to dedicated improvement session
- Proposed: switch to "delta-only" format with persistent indicator viewport

**ID referenced**: imp_f14d6fae96ff
