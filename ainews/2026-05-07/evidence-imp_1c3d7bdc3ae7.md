# 证据: imp_1c3d7bdc3ae7 — AINews autoresearch schema / run-scope / postcheck

**ID**: imp_1c3d7bdc3ae7
**日期**: 2026-05-07
**状态**: done (本次执行验证通过)

## 执行内容
1. 运行 `run_ainews_autoresearch_lite.py --date 2026-05-07`
2. 输入完整性: morning-digest.md ✓ / paper-digest.md ✓ / evening-report.md ✓ / ops-summary.md ✗ (degraded input, 3/4)
3. 生成 3 个 candidate: h1-h3, 全部 `promoted: false`
4. 所有 candidate 使用嵌套 `hypothesis.*` 结构, 字段完整 (title/change_type/core_claim)
5. run summary 只记录本次 3 个 candidate_files, 无陈旧候选混入
6. `generate_daily_review.py` 生成的审核报告 3 个 candidate 全部正确展示标题/核心主张, 无 schema 退化

## 验证结果
- Schema: 全部 candidate 字段完整 ✓
- Run-scope: run summary 3 个 = review report 3 个, 无串单 ✓
- Postcheck: 报告展示内容与 JSON 文件内容一致 ✓

## 后续
- 此问题自 04-17 起已持续 14 次提及, 本次执行链路完整验证通过
- 建议将此 item 标记为 done, 但需持续监控后续日期的 autoresearch 执行
- 证据路径: `/Users/study/.openclaw/shared-context/intel/autoresearch/ainews/candidate_versions/lite-2026-05-07-h{1,2,3}-v1.json`
- 运行日志: `/Users/study/.openclaw/shared-context/intel/autoresearch/ainews/runs/lite-2026-05-07-run.json`
- 审核报告: `/Users/study/.openclaw/shared-context/intel/autoresearch/ainews/reports/review-report-2026-05-07.md`
