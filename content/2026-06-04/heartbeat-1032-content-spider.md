# 内容蜘蛛心跳｜2026-06-04 10:32 CST

## 本轮结论
发现一个可转化增量：**“AI 工作流”主线可以从泛泛的 Claude Code loops，收窄到「把历史会话挖成个人规则/记忆层」**。这比单纯讲 prompt 或 agent 更贴近日常痛点：AI 总忘记你的偏好、重复犯错、每次新会话都从零开始。

## X / AI-LLM 热点
数据源：`xreach --proxy http://127.0.0.1:1087`，窗口 `since:2026-06-03`。

重点信号：
1. **Claude Code session mining → CLAUDE.md rules**
   - 原帖核心：`Claude Code can mine ur last 50 sessions into CLAUDE.md rules`。
   - 样本：2,681 views / 53 likes / 18 bookmarks（2026-06-03 18:40 UTC）。
   - 判断：高潜力。这个角度能把“AI 工作流”讲成具体方法：从反复纠正 AI，到自动提炼个人 SOP / 偏好 / 禁忌清单。

2. **Claude Code 架构讨论：模型外的 harness 才是差异**
   - 原帖核心：`AI coding tools do not compete only on the model. They compete on the harness around the model.`
   - 当前样本互动低，但作为观点素材有价值。
   - 判断：可作为上面选题的理论补强：真正的护城河不是模型本身，而是记忆、工具边界、权限流水线、上下文压缩、验证循环。

3. **Netlify Agent runners 多工具工作流**
   - 原帖核心：用 Netlify Agent runners 串起 Claude Code、Codex、Gemini，生成项目 feature ideas 并汇总下一步。
   - 样本较小：103 views / 1 like / 1 repost。
   - 判断：不是热点，但可作为“多模型协作不是换模型，而是编排任务流”的例子。

噪音过滤：10:32 这轮 X 搜索结果里，`Claude prompts / 9 prompts / awesome list` 类内容不少，但大多偏工具清单或模板搬运，暂不作为主线。

## 小红书趋势
数据源：`https://hot.baiwumm.com/api/xiaohongshu`。

前排仍偏视觉生活方式：
1. 用万能旅行拍照姿势美美出片（905.1w）
2. 耗时三年拍下古诗词里的中国（894w）
3. 我拍到了海鸥雨（874.7w）
4. 超日常美食教程速来get（852.9w）
5. 定格这一刻的日照金山（843w）
6. 你可以永远相信赛里木湖的美景（833.5w）
7. 拼豆上也可以作画了（822.4w）
8. 我的家庭旅行更像是打副本（802.9w）

可转化判断：小红书仍没有 AI/LLM 自然上榜，但“万能姿势 / 古诗词中国 / 打副本”都适合套进 AI 工作流表达。

## ainews / AI 情报
- smol.ai RSS 最新可读 issue 仍是 2026-06-02：Microsoft Build / MAI family / Surface RTX Spark / OpenClaw in Windows。
- Artificial Intelligence News 最新条目仍集中在 2026-06-03：
  - E.ON + SAP S/4HANA：电网现代化与 AI。
  - Walmart AI workflows：AI 工作流碰到账本/ROI。
  - Microsoft Majorana 2：量子芯片作为 agentic AI in R&D 案例。
  - Anthropic IPO filing：AI 企业公用事业化。
  - GitHub Copilot token-based price hikes：开发者工具定价压力。

转化判断：企业 AI 与开发者工具都在进入“审计期”：不仅问能不能做，还问成本、权限、可追溯、ROI。

## trading / 市场快照
数据源：`knowledge/daily/2026-06-04/raw/trading_snapshot-1003.csv`，非投资建议。

| 标的 | Close | vs Open |
|---|---:|---:|
| SPY.US | 754.20 | -0.52% |
| QQQ.US | 744.32 | -0.40% |
| NVDA.US | 214.82 | -3.11% |
| MSFT.US | 427.61 | -2.47% |
| META.US | 623.01 | +3.44% |
| AMD.US | 542.32 | +1.61% |
| GOOGL.US | 358.99 | -0.84% |
| TSLA.US | 423.76 | +1.21% |
| BTCUSD | 62003.50 | -5.58% |
| XAUUSD | 4460.18 | +0.47% |

内容判断：AI 股分化 + BTC 回撤，可以配合“审计期”叙事：市场不是不买 AI，而是开始区分谁能把 AI 转成利润、效率、或确定性。

## 可执行选题
1. 《别再重复纠正 AI 了：把最近 50 次会话挖成你的个人规则库》
2. 《Claude Code 真正厉害的不是模型，是模型外面的 harness》
3. 《从万能拍照姿势到 AI 工作流：爆款都是“可复用动作模板”》
4. 《AI 进入审计期：企业问 ROI，开发者问权限和记忆》

## 原始素材路径
- X AI/LLM：`tmp/heartbeat-2026-06-04-1032/x_ai_llm.json`
- X Claude Code：`tmp/heartbeat-2026-06-04-1032/x_claude_code.json`
- X agent workflow：`tmp/heartbeat-2026-06-04-1032/x_agent_workflow.json`
- X 原帖缓存：`tmp/heartbeat-2026-06-04-1032/tweet_*.json`
- 小红书：`tmp/heartbeat-2026-06-04-1032/xhs_hot.json`
- smol.ai RSS：`tmp/heartbeat-2026-06-04-1032/smol_ai_rss.xml`
- Artificial Intelligence News RSS：`tmp/heartbeat-2026-06-04-1032/artificialintelligence_news_rss.xml`
- Trading：`knowledge/daily/2026-06-04/raw/trading_snapshot-1003.csv`
