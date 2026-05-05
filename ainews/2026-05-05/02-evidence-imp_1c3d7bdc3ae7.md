# Evidence: imp_1c3d7bdc3ae7 — AINews autoresearch schema / run-scope / postcheck

**Date**: 2026-05-05
**Agent**: ainews
**Status**: ✅ 本次执行完成（但仍需脚本层修复）

## 执行记录

### autoresearch-lite 运行（21:30）
- 输入完整性：morning-digest.md ✅ (9582字符) | paper-digest.md ✅ (3993字符) | evening-report.md ✅ (5098字符) | ops-summary.md 未找到（非阻塞）
- 生成 3 个 candidate hypotheses (h1-h3)
- 所有 candidate `promoted=false` ✅
- 候选文件：`lite-2026-05-05-h{1,2,3}-v1.json`
- Run summary：`runs/2026-05-05-lite-run.json`，`candidate_files` 仅记录 3 个（无残留 h4 混入）✅

### generate_daily_review.py 运行（21:30）
- 读取到 3 个 candidate，与 run summary 的 candidate_files 数量一致 ✅
- 审核报告正常展示标题/类型/核心主张：
  - h1: "AI 新闻筛选优化" (filter_rule)
  - h2: "新闻摘要模板优化" (summary_template)
  - h3: "信号标签系统优化" (signal_tag)
- 报告保存至：`reports/review-report-2026-05-05.md`

## 与 imp_1c3d7bdc3ae7 的关系

imp_1c3d7bdc3ae7 的核心诉求是：autoresearch 的 schema 适配、run-scope 隔离、postcheck 一致性。

**本次执行状态**：
- ✅ run-scope 隔离：本次 run summary 只记录了本次新生成的 3 个文件，无残留 h4 混入
- ✅ postcheck 一致性：review report 读取 3 个 candidate，与 run summary 一致
- ⚠️ schema 适配：本次 review report 能正确展示 candidate 标题（h1-h3 均有标题），说明 schema adapter 可能在某次更新后已修复，但需确认 generate_daily_review.py 是否已真正修复（此前连续 14 天显示"无标题/unknown"）

## 后续跟踪

- 需确认 generate_daily_review.py 是否已包含 schema adapter 修复（优先读 hypothesis.* 回退）
- 如已修复，可将 imp_1c3d7bdc3ae7 标记为 done
- 如未修复，本次能正确展示可能是候选文件同时包含顶层字段和 hypothesis.* 字段
