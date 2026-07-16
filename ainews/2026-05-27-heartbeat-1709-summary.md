# Heartbeat AI/Tech Watch — 2026-05-27 17:09 CST

Source check: RSS aggregator `--category all --days 1 --limit 200 --json`; spot verification via Ars Technica / BadHost / TechCrunch pages.

## Alert decision

- **Urgent push: YES — security**
  - Starlette/FastAPI ecosystem issue **CVE-2026-48710 / BadHost**: host-header/auth-bypass class vulnerability affecting Starlette versions prior to 1.0.1; downstream exposure cited for FastAPI, vLLM, LiteLLM, MCP servers, model gateways, dashboards and agent harnesses. Severity is time-sensitive because affected services may hold third-party credentials and MCP/tool access.
  - Practical watch: any Python ASGI / FastAPI / Starlette-backed AI service should verify Starlette version and front-door host-header handling; upgrade to Starlette >= 1.0.1 where applicable.

## Notable items

- **Millions of AI agents imperiled by critical vulnerability in open source package** — Ars Technica - AI; Tue, 26 May 2026 19:50:33 +0000
  https://arstechnica.com/information-technology/2026/05/millions-of-ai-agents-imperiled-by-critical-vulnerability-in-open-source-package/
- **CVE-2026-48710 Starlette Host-Header Auth Bypass** — Lobsters; Wed, 27 May 2026 02:32:12 -0500
  https://badhost.org
- **OpenRouter more than doubles valuation to $1.3B in a year** — TechCrunch - AI; Tue, 26 May 2026 18:33:01 +0000
  https://techcrunch.com/2026/05/26/openrouter-more-than-doubles-valuation-to-1-3b-in-a-year/
- **ECB says private-credit fuelled AI boom poses risk to financial system** — Financial Times - AI; Tue, 26 May 2026 11:49:15 GMT
  https://www.ft.com/content/7ecdff9f-4f3a-40dd-b984-9860097dd083
- **China overhauls world’s biggest surveillance network with advanced AI** — Financial Times - AI; Wed, 27 May 2026 04:00:05 GMT
  https://www.ft.com/content/f8fa4739-4359-4720-af77-9be1e8370f82
- **What Pope Leo XIV’s First Encyclical Says About the Power of AI** — Wired - AI; Tue, 26 May 2026 20:17:47 +0000
  https://www.wired.com/story/what-pope-leo-xivs-first-encyclical-says-about-the-power-of-ai/
- **Why the Vatican Invited Anthropic to the Pope’s AI Encyclical Presentation** — Wired - AI; Tue, 26 May 2026 20:46:03 +0000
  https://www.wired.com/story/anthropic-christopher-olah-pope-ai-encyclical/
- **DuckDuckGo installs are up 30% as users reject being ‘force-fed’ Google’s AI Search** — TechCrunch - AI; Tue, 26 May 2026 22:32:56 +0000
  https://techcrunch.com/2026/05/26/duckduckgo-installs-are-up-30-as-users-reject-being-force-fed-googles-ai-search/
- **Claude Mythos reportedly solves OpenAI's landmark Erdős problem with a "cute, simple proof"** — The Decoder; Tue, 26 May 2026 18:31:07 +0000
  https://the-decoder.com/claude-mythos-reportedly-solves-openais-landmark-erdos-problem-with-a-cute-simple-proof/
- **RT by @paulg: Today we’re releasing DeepSWE, a new standard for agentic coding benchmarks.  On public leaderboards, top models often look relatively close in capability. DeepSWE shows where they actually diverge, reflecting the realistic experience of developers in their day-to-day work.** — Paul Graham (Twitter); Tue, 26 May 2026 16:18:34 GMT
  https://nitter.net/serenaa_ge/status/2059308218564890875#m

## Collaboration signals

- **Notify trading:** YES — OpenRouter Series B / 5x token-volume growth confirms AI gateway + multi-model inference infrastructure momentum; semiconductor/memory ETF signal also remains an AI-infra market datapoint, but not a standalone trade call.
- **Notify macro:** YES — ECB AI private-credit risk item + China AI surveillance modernization are macro/policy relevant AI signals; pass through for regime/risk monitoring.

## Archive

- RSS JSON: `knowledge/daily/2026-05-27-heartbeat-1709-rss.json`
- RSS log: `knowledge/daily/2026-05-27-heartbeat-1709-rss.log`
