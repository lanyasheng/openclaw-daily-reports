# 内容蜘蛛心跳｜2026-06-03 08:31 CST

执行范围：严格按 `/Users/study/.openclaw/workspace-content/HEARTBEAT.md`：扫描 X 热门话题（AI/LLM/科技相关）、检查小红书热搜趋势、读取 ainews 最新情报、读取 trading 市场分析；有可转化素材则整理到 `knowledge/daily/`。

原始采集目录：`/Users/study/.openclaw/workspace-content/tmp/heartbeat-2026-06-03-0831`

## 1) X 热门话题｜AI / LLM / 科技

本轮抓取：`x_ai_recent.json`、`x_ai_llm.json`、`x_ai_zh.json`；合并去重后约 54 条。

高信号样本（按 bookmarks / likes / views 粗排）：
- Remotion now has Agent Skills - make videos just with Claude Code! $ npx skills add remotion-dev/skills This animation was created just by prompting 👇 https://t.co/hadnkHlG6E — views 17,914,461, likes 21,153, bookmarks 36,956
- Anthropic engineer: "You're not supposed to watch Claude Code work. You're supposed to wake up and review what it shipped." In 22 minutes she builds the entire workflow live on camera.… — views 1,554,760, likes 7,890, bookmarks 23,641
- We built our launch video in Claude Code using HyperFrames. Now it's yours. Open source, agent-native framework. HTML to MP4. $ npx skills add heygen-com/hyperframes RT + Comment "Hype… — views 2,944,273, likes 8,346, bookmarks 13,718
- People think learning Claude takes days. It doesn't. I wrote 17 free guides that teach it in hours: Claude 101: https://t.co/7NLEAbsCuq Claude Code: https://t.co/IJdryPBjZ3 Claude Skil… — views 863,012, likes 6,623, bookmarks 13,123
- Stop telling Claude, "do this." Stop telling Claude, "write code." Stop telling Claude, "fix this error." You're actually treating a senior AI like a junior intern. Here are 8 prompts … — views 1,636,768, likes 4,377, bookmarks 12,865
- New in Claude Code: agent view. One list of all your sessions, available today as a research preview. https://t.co/NnbsAQjSPW — views 6,107,718, likes 28,810, bookmarks 11,089
- Anthropic's CEO: "coding is going away first. then all of software engineering." the 5% that survives? systems thinking. 3 months ago I published 5 projects for this exact moment. 21K … — views 2,016,080, likes 5,525, bookmarks 10,764
- Today, we’re releasing a feature that allows Claude to control your computer: Mouse, keyboard, and screen, giving it the ability to use any app. I believe this is especially useful if … — views 4,780,950, likes 18,608, bookmarks 10,689

趋势判断：
- **Claude Code workflow / dynamic workflows** 是本轮最强信号：高收藏说明读者想要“可复用流程”，不是单个提示词。
- **Claude Code 额度、/fork、后台 agent、subagent 编排** 同时出现，适合转成“如何设计不会失控的多代理工作流”。
- **AI 工程学习路线** 仍热，但容易沦为清单复述；更适合聚焦“哪些技能 6 个月后仍有效”。
- **Agent 接金融账户/交易** 有话题性，但风险高；如果转内容，应做成“AI agent 权限边界与风控清单”，避免任何投资建议。

## 2) 小红书热搜趋势

数据链路：TopHub 今日热榜「小红书热榜」；页面显示：2分钟前更新。

前十热点：
1. 用万能旅行拍照姿势美美出片 — 942.2w
2. 耗时三年拍下古诗词里的中国 — 930.5w
3. 我拍到了海鸥雨 — 911.4w
4. 超日常美食教程速来get — 887.7w
5. 定格这一刻的日照金山 — 877w
6. 你可以永远相信赛里木湖的美景 — 867.2w
7. 拼豆上也可以作画了 — 856w
8. 我的家庭旅行更像是打副本 — 835.3w
9. 原来古诗词里的河南真的存在 — 820.9w
10. 蒸出了奶香爆米花馒头 — 804.7w

趋势判断：旅行拍照、古诗词/地域文化、生活美食、手作仍是主线；AI/科技没有进入前十。更适合把 AI 包装成“生活任务助手/审美辅助”，而不是工具新闻。

## 3) ainews 最新情报

最新条目：`not much happened today`  
发布时间：`Mon, 01 Jun 2026 05:44:39 GMT`  
链接：https://news.smol.ai/issues/26-06-01-not-much/

摘要：**NVIDIA** led open-source AI model releases with **Cosmos 3**, a comprehensive omnimodal world model unifying language, image, video, audio, and action using a Mixture-of-Transformers design, and **Nemotron 3 Ultra**, a **550B** parameter open-weight model noted for high serving speed and strong evaluation performance. The **Cosmos Coalition** was launched to foster an open ecosystem for physical AI world models. Meanwhile, **MiniMax M3** debuted as a multimodal agent/coding model with **1M context** and strong benchmark scores, gaining rapid ecosystem support from vendors like **Novita** and **Vercel AI Gateway**. However, MiniMax M3 showed some inefficiencies such as high token consumption and verbose self-check loops. These developments highlight advances in open physical AI, multimodality, and agent models with significant community and infrastructure engagement.

可复用重点：开放物理 AI / 世界模型、MiniMax M3 的 1M context + agent/coding 叙事，适合与“Agent 工作流”和“长上下文成本治理”合并成一篇。

## 4) trading 市场分析

数据链路：Stooq CSV。

- SPY.US: 2026-06-02 22:00:21, open 757.03, close 759.57, intraday +0.34%
- QQQ.US: 2026-06-02 22:00:19, open 742.4, close 746.16, intraday +0.51%
- NVDA.US: 2026-06-02 22:00:19, open 227.18, close 222.8, intraday -1.93%
- AMD.US: 2026-06-02 22:00:19, open 506.3, close 521.4199, intraday +2.99%
- META.US: 2026-06-02 22:00:19, open 603.24, close 597.64, intraday -0.93%
- BTCUSD: 2026-06-03 02:34:12, open 67485, close 66917.3, intraday -0.84%
- ETHUSD: N/D N/D, open N/D, close N/D, intraday N/D
- XAUUSD: 2026-06-03 02:34:16, open 4491.18, close 4484.5, intraday -0.15%

判断：科技指数温和偏强，AI 大票分化；BTC 仍偏弱但较前一轮略修复。市场只适合作为背景，不宜从单日价格推出 AI 赛道结论。

## 5) 本轮可推进内容选题

1. **《别再收藏提示词：Claude Code 真正升级的是 workflow》**
   - 角度：任务说明 → 编排脚本 → subagent 分工 → 自检 → 返工 → 验收。
   - 适合平台：公众号/知识帖；可拆成小红书卡片版。

2. **《多代理工作流会失控？先写 5 条权限边界》**
   - 角度：后台 agent、/fork、动态 workflow 的风险：并发、费用、权限、审计、回滚。
   - 适合平台：X/小红书技术向卡片。

3. **《小红书生活热点里的 AI 入口：旅行姿势、诗词路线、家庭副本》**
   - 角度：把 AI 从“工具新闻”翻译成旅行拍摄清单、路线讲解脚本、家庭成员任务卡。

4. **《AI 编程账单太高？先省上下文，再谈本地算力》**
   - 角度：上下文裁剪、缓存、模型分层、本地/云端混合；承接 Claude Code 高使用量与额度讨论。
