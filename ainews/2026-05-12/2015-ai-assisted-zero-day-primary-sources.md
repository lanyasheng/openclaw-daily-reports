# AI-assisted zero-day / 2FA bypass — primary source update

## Primary source
- Google Cloud / Google Threat Intelligence Group: "Adversaries Leverage AI for Vulnerability Exploitation, Augmented Operations, and Initial Access"
- URL: https://cloud.google.com/blog/topics/threat-intelligence/ai-vulnerability-exploitation-initial-access
- Key excerpt: GTIG says it identified, for the first time, a threat actor using a zero-day exploit believed to have been developed with AI; the criminal actor planned a mass exploitation event, but Google’s proactive counter-discovery may have prevented use.
- Key excerpt: The zero-day was implemented in a Python script enabling 2FA bypass on a popular open-source web-based system administration tool; exploitation still required valid user credentials.
- Key excerpt: Google assesses with high confidence that an AI model likely supported discovery/weaponization based on LLM-style code hallmarks, including educational docstrings and a hallucinated CVSS score.

## Secondary source
- The Hacker News: "Hackers Used AI to Develop First Known Zero-Day 2FA Bypass for Mass Exploitation"
- URL: https://thehackernews.com/2026/05/hackers-used-ai-to-develop-first-known.html
- Key excerpt: Google disclosed an unknown threat actor using a zero-day exploit likely developed with AI, described as the first observed malicious in-the-wild AI-assisted vulnerability discovery/exploit generation case.

## Caveats
- Google did not disclose the affected open-source administration tool.
- Google says it does not believe Gemini was used.
- NYT/Politico coverage was confirmed via Google News RSS titles, but direct article extraction was not independently completed here (Politico returned 403; NYT tech RSS did not expose the item in the fetched excerpt).

## AINews assessment
- Confidence upgraded from medium-low to medium-high for event existence because primary GTIG source is accessible.
- Policy/risk confidence remains medium-low until official CISA/White House/SEC/FTC/Congress or market reaction appears.
