# 心跳素材扫描｜2026-05-24 15:02 CST

> 只扫描，不创作。用于后续选题与素材转化。

## 执行摘要

本轮外部实时搜索链路不稳定：`web_search` 全部 404，`ainews.cn` web_fetch 失败，小红书/X 的 feedgrab 检索因登录态或依赖缺失失败。已使用可访问兜底源：The Verge AI、news.smol.ai、本地 ainews 今日情报、TopHub 知乎/微博、trading 午间快报。

已同步记录高潜力线索到：`knowledge/ideas/2026-05-24.md`。

## 来源与采集结果

### 1. X/Twitter AI/LLM/科技趋势

- `web_search` 查询 X/Twitter AI/LLM/科技近 24 小时热点：失败（404）。
- `feedgrab x-so "AI LLM OpenAI Anthropic Claude" --days 1 --min-faves 50 --limit 10`：失败，缺 Twitter Cookie。
- 兜底采用 The Verge AI 与 ainews 中引用的 X/Nitter 信号：
  - Greg Brockman 展示 Codex Computer Use 驱动 iPhone 模拟器。
  - Harrison Chase 提醒 Agent 不应直接暴露环境变量和凭据。
  - CapCut editing 即将接入 Gemini。
  - Aleksander Madry 离开 OpenAI，转向 AI 经济影响方向。

### 2. 小红书趋势

- `web_search` 查询小红书热搜/趋势：失败（404）。
- `feedgrab xhs-so "AI Agent" --sort popular --limit 5`：失败，提示 XHS API 不可用，需 `xhshow` 与登录态。
- 本轮不声称已获取小红书站内热搜；仅保留可后续验证关键词：AI Agent、DeepSeek、Claude Code、AI 做 PPT、具身智能。

### 3. AI 情报

#### 本地 ainews 今日重点

- DeepSeek 将 75% 折扣永久化，低价模型竞争加剧。
- TencentDB Agent Memory 开源：四级本地 Agent 记忆管道。
- SuperClaude Framework：Commands / Agents / Modes / Session Memory 工作流。
- Codex Computer Use 驱动 iPhone 模拟器，移动端自动化边界扩展。
- Science 论文：谄媚型 AI 降低亲社会意图并促进依赖。
- GitHub 热点聚焦 Skill / Plugin / MCP：Karpathy skills、Claude plugins、Chrome DevTools MCP、codegraph、Understand-Anything。

#### news.smol.ai 兜底

- 最近 30 天 AI 线索集中在：NVIDIA Gated DeltaNet-2、OpenAI AI-assisted 数学突破、tokenization、linear attention、agent infrastructure。
- 适合保留为研究背景，不作为今天单独热点。

#### The Verge AI 兜底

- AI 伪造引用进入图书出版争议。
- Anthropic Project Glasswing 安全工具向合格客户开放。
- ChatGPT for PowerPoint beta 已可用。
- Trump 推迟 AI executive order，理由涉及就业与中美 AI 竞争。
- Anthropic 洽谈使用 Microsoft Maia 200 芯片。
- Nvidia 数据中心收入继续由 AI 数据中心需求驱动。

### 4. 中文平台热榜兜底

#### 知乎热榜（TopHub）

- 微信读书上线 AI Skill：约 123 万热度。
- DeepSeek 引入 API 并发限制：约 105 万热度。
- 俄银行采购中国芯片，为大模型提供算力：约 59 万热度。
- 比亚迪 5 月 28 日智能化战略发布会：约 51 万热度。

#### 微博热搜（TopHub）

- 神舟二十三号出征：约 112 万。
- 当 AI 有一副人的身体：约 57 万。
- 其余前排以社会事件/娱乐为主，与 AI/科技/投资内容方向相关性较弱。

### 5. Trading 相关素材

来源：`/Users/study/.openclaw/workspace-trading/knowledge/daily/2026-05-24/midday-news.md`

可转化但需避免投资建议：
- 美伊协议进展影响原油、航运、化工情绪。
- 下周 PCE、中国 PMI、长鑫科技上会、拼多多/小米财报是市场关键节点。
- AI 算力链：CPO、光模块、超级电容被提示为下周潜在主线。
- AI 数据中心功耗上升推动电源/电容/能源基础设施叙事。

## 可转化素材池

1. **DeepSeek 成本战**：从“模型便宜了”讲到“Agent 应用商业模型重算”。
2. **Skill/MCP 生态**：从 Karpathy skills 到 Claude plugins，AI 编程竞争转向工作流生态。
3. **Codex iPhone Computer Use**：移动端 QA/测试/自动操作可能成为新场景。
4. **Agent 记忆与可观测性**：TencentDB Agent Memory + SmithDB + GraphFlow/IdleSpec 论文形成基础设施主线。
5. **AI 产品风险**：伪造引用、谄媚型 AI、凭据隔离，适合做 AI 使用安全内容。
6. **AI 算力投资科普**：CPO、超级电容、AI 电力链，可做“AI 产业链不只有模型”观察。

## 待补全 / 阻塞

- 小红书：需补齐 `xhshow` 与小红书登录态。
- X/Twitter：需补齐 Twitter Cookie。
- `web_search`：当前 404，影响实时趋势覆盖。
- `ainews.cn`：web_fetch 失败，本轮用本地 ainews 与 news.smol.ai 兜底。
