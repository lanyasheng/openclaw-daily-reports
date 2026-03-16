🌅 公司次日晨报 | 2026-03-13

- 今日总判断
  - 公司今天的核心主线不是“新增更多任务”，而是把多 Agent / ACP / cron 的运行真值、终态收口和投递闭环补稳。main 在治理侧已有实质推进，但 follow-up 暴露出多个 P0 项仍缺 owner、证据链或 blocker 说明。
  - 外部 AI 线索很集中：今天最值得重视的不是单个模型分数，而是四件事——harness/workflow 嵌入、审查成为新瓶颈、Agent 安全设计、以及本地优先/策略层治理。这些都和我们当前体系直接相关。
  - 市场环境偏谨慎。macro 与 trading 一致指向：中东风险、油价高位、美元偏强、美股回撤，意味着今天更适合防守式判断和局部结构机会，不适合给出情绪化乐观结论。
  - content 侧素材充足，但真实短板仍然是后半段闭环：从“有草稿”走到“审核 / 预测 / 发布或明确搁置理由”还没有完全跑通。

- 昨日关键进展（3-5 条）
  - main 明确了 ACP 终态四分类口径，确认 thread/session 模式会出现“已完成但注册未收口”的假非终态，并推进独立 reconciler/helper 方案。
  - ACP 修复方向已拿到可验收证据：`content_aware_completer.py` 与对应测试文件存在，`python3 test_content_aware_completer.py` 跑通 10/10 tests，`task-log.jsonl` 已出现 `completionSource=content_reconciler` 的真实补写记录。
  - ainews 已把 `agency-agents` 研究推进到第二页文件映射稿，并完成 `Scrapling` 第一版快速尽调，研究从“值得关注”走到“可以映射到我们哪些文件/流程”。
  - content 昨日完成 3 条可发初稿，去 AI 味执行比前一天更扎实，但仍未进入“老板审核 → Ripple 预测 → 发布或搁置理由”的完整闭环。
  - macro 保持 5 份关键报告完整归档，并沉淀出“叙事切换触发器”；butler 的提醒链路送达稳定，但归档和计划类任务的时间窗治理仍未补齐。

- 各 Agent 摘要（main / ainews / macro / trading / content / butler）
  - main
    - 今日重点在 ACP 真值治理与 cron 真值校正。
    - 已确认后续 ACP 修复型任务更适合 `runtime="acp" + mode="run" + thread=false + streamTo="parent"`，不应默认走 thread/session。
    - 另一个重要判断是：cron 的 `error` 不能直接等于“当前故障”，必须区分“当前应执行失败”和“历史失败残留”。
  - ainews
    - 昨日侧重两条：一是 `agency-agents` 的高价值结构映射，二是 `Scrapling` 作为 Agent 抓取基础设施候选的快速尽调。
    - 今日晨间 AI 情报主线非常清晰：`Harnesses are the new agents`、编码 Agent 让实现更便宜但审查更贵、OpenAI 的提示注入防御、AWS 的策略层执行边界、本地优先 Agent 架构。
    - 但 follow-up 显示：ainews 派发的安全工具链动作（promptfoo / 上下文长度监控 / 行为审计日志）今天仍缺新增实现证据。
  - macro
    - 口径偏谨慎偏利空：中东冲突持续发酵，油价高位、黄金短暂背离、亚洲货币与流动性承压。
    - 方法上有一个值得保留的升级：研究框架已从“石油特例”提升到通用版“叙事切换触发器”。
    - 风险点仍在 delivery：run ok 不等于 delivered ok，关键报告的投递链路和 stale-drop 机制还需要继续修复。
  - trading
    - 昨日反思文件暂无；今日判断主要来自晨间金融简报。
    - 市场面统一评分 42 分（弱势），偏向防守；A 股关注化工、上游能源、部分新能源链条，但对黄金、军工、半导体偏谨慎。
    - 与 macro 的共识是：地缘冲突、油价、美元和美股回撤正在抬高风险阈值。
  - content
    - 昨日已经完成“研究 → 创意 → 3 条初稿”的前半段闭环，且标题/开头去 AI 味比前一日明显改善。
    - 今日素材继续丰富：harness engineering、一人公司技术栈、Agent 安全设计、AI 自动化案例都具备写作窗口。
    - 但 follow-up 指出一个关键缺口：今天仍未看到“审核 / 预测 / 发布或明确搁置理由”的证据，说明内容链条还停在可写阶段。
  - butler
    - 提醒送达表现稳定：早安、喝水、晚间关怀、晚安收口均正常送达。
    - 但 `knowledge/daily/2026-03-12/` 为空，提醒执行与知识归档依然分离。
    - `butler-plan-my-day` 出现 22:22 才生成次日计划的时间窗漂移，说明提醒类 cron 还缺硬性时段校验。

- 今日 P0 / P1
  - P0
    - 补齐 follow-up 中所有未闭环事项的 owner、状态和证据路径，尤其是：macro↔trading 市场锚点快照、butler 提醒审计闭环、ainews 安全工具链动作、content 发稿后半段闭环。
    - 深挖 3 条 timeout 日常任务的具体卡点：`daily-reflection-trading`、`macro-daily-check`、`content-daily-inspiration`，明确是 prompt 负载、外部命令还是 timeout 配置过紧。
    - content 从现有 3 条初稿里至少推进 1 条进入“老板审核 → Ripple 预测 → 发布或明确搁置理由”。
  - P1
    - 把 `Harnesses are the new agents`、一人公司技术栈、Agent 安全设计模式转成可对外使用的短稿框架。
    - 推进 macro / trading 去重：macro 负责前提与情景，trading 负责执行与仓位，并落成统一模板。
    - 为 butler 增加 plan/health 类任务的时间窗与归档强约束，避免继续出现“送达了但无归档”的情况。

- AI news → 公司动作（2-3 条）
  - 1. `Harnesses are the new agents` → 公司动作：把“角色数量扩张”转向“工作流嵌入 + 质量门 + 审计链”。优先做的是让高价值 Agent 产出进入真实业务环节，而不是再新增空转角色。
  - 2. OpenAI 提示注入防御 + AWS AgentCore 策略层 → 公司动作：加速把 ainews 已认领的三项安全工具链动作落地为真实实现：promptfoo 评估、上下文长度监控、行为审计日志，并与 ACP/任务日志体系打通。
  - 3. 编码 Agent 让实现变便宜、审查变昂贵 + Rakuten/Codex ROI 案例 → 公司动作：内部默认把“审查、验收、回归、收口”视为新的生产率核心，继续优先使用后台 run 模式做修复型 ACP 任务，并保留人工审核点。

- 今日可写内容候选（2-3 条，每条含切口 / 适合平台 / 为什么值得今天写）
  - 1. 切口：写代码正在变便宜，审查正在变贵
    - 适合平台：X Thread / 知乎
    - 为什么值得今天写：Harrison Chase 的观点、LangChain 创始人的 `harnesses` 判断、以及我们自己对 ACP 验收/终态治理的实践，今天形成了非常强的同题共振，既有行业观点，也有内部实战映射。
  - 2. 切口：一人公司技术栈 2026，不是工具越多越强，而是链路越短越强
    - 适合平台：小红书 / X
    - 为什么值得今天写：`Solo Startup Cheatsheet` 和 content 研究素材匹配度高，和老板“软件工程师 + AI + 个人品牌”定位高度一致，天然适合做收藏型清单内容。
  - 3. 切口：Agent 安全不是大厂专属，个人工作流也需要最小防线
    - 适合平台：知乎 / X
    - 为什么值得今天写：OpenAI 刚发提示注入设计指南，AWS 又补了策略层；这类题今天时效性强，而且能把“能做什么”切换到“怎么安全地做”，更符合成熟技术人表达。

- 公开边界提示（内部 only / 可转短稿 / 可进周报）
  - 内部 only
    - ACP 终态四分类细节、`content_reconciler` 修复路径、具体 timeout 任务名、follow-up 中未认领事项、butler/cron 的异常链路。
  - 可转短稿
    - harness engineering / 审查成为新瓶颈
    - 一人公司技术栈与最短工作流
    - Agent 安全设计模式（去掉内部实现细节后可公开）
  - 可进周报
    - 公司本周在 Agent 治理上的真实进展：从“多角色堆砌”转向“真值、审计、收口、交付”
    - AI 行业主线从“模型能力”转向“工作流嵌入、安全、策略层、ROI”
    - 内容侧从“研究驱动”逐步过渡到“成稿与发布闭环驱动”

⚡ 对外短稿候选
- 题目方向：`写代码正在变便宜，审查正在变贵`
- 一句话理由：今天这不是抽象趋势，而是 AI 圈公开观点、企业 ROI 案例、以及我们内部多 Agent/ACP 实践同时指向的同一个变化。