# Blocker: Content Publish Closed Loop
**ID**: imp_d60357465ff5
**Priority**: P0 (count: 45)
**Owner**: content-agent
**Date**: 2026-06-21 09:33 CST

## Status (unchanged — blocking since 06-12)

Publish endpoints remain unconfigured:
- No 公众号 API token / CMS webhook
- No 小红书 Cookie / API credentials
- No X.com/xreach auth
- No `publish/queue.json` infrastructure

## What HAS been done
- 3 drafts ready from 06-20 session (push-flag files exist):
  - `draft-01-karpathy-zhen-yong-ai.md` — Karpathy 真用AI (时效窗口 ~06-21 20:00, expiring!)
  - `draft-02-codex-record-replay.md` — Codex Record & Replay (时效窗口 ~06-22)
  - `draft-03-300-to-14k-ai-bot.md` — 300→14K AI Bot (时效窗口 ~06-22)
- All three have passed AI-味门禁 + 风险自检
- Publish order recommended: Karpathy > Codex > AI Bot
- 7 content ideas also compiled in `content-ideas.md`

## Next
- ⚠️ **Karpathy draft will expire TODAY at 20:00 CST** — highest urgency
- Awaiting human: configure at least one publish target (小红书 easiest if cookie-based auth)
- Once endpoint provided, Karpathy draft can be pushed in ~10 min

## Evidence
- `push-flag-karpathy.md`, `push-flag-codex.md`, `push-flag-ai-bot.md` (in 2026-06-20 dir)
- `content-ideas.md` (2026-06-20)
