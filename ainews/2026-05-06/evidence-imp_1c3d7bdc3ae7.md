# Evidence: imp_1c3d7bdc3ae7 — AINews autoresearch schema / run-scope / postcheck

**imp_id**: imp_1c3d7bdc3ae7
**Date**: 2026-05-06
**Owner**: ainews
**Status**: done (evidence provided)

## 执行证据

### autoresearch-lite 运行（2026-05-06 21:30）
- ✅ 输入完整性：morning-digest.md (8736字符) + paper-digest.md (3231字符) + evening-report.md (4909字符)
- ✅ 生成 3 个 candidate hypotheses (h1-h3)
- ✅ 所有 candidate `promoted: false`
- ✅ run summary `candidate_files` 仅记录 h1-h3（无残留文件混入）
- ✅ review report 候选数 (3) 与 run summary 一致

### schema 验证
- ✅ 3 个 candidate 文件均包含完整 `hypothesis.title` / `hypothesis.change_type` / `hypothesis.core_claim`
- ✅ review report 正确读取并展示标题（h1: AI 新闻筛选优化, h2: 新闻摘要模板优化, h3: 信号标签系统优化）
- ✅ 无 "无标题/unknown/无核心主张" 退化

### postcheck 验证
- ✅ run summary candidate_files 数量 (3) == review report 候选数 (3)
- ✅ 无残留 h4 混入
- ✅ 所有文件 `promoted=false`

## 后续跟踪
- schema adapter 修复已验证生效（自 04-17 以来连续 20+ 天的 schema 失配问题已解决）
- run-scope 隔离干净（无残留 candidate 混入）
- 建议：后续每日反思继续验证 autoresearch-lite 运行质量，但 imp_1c3d7bdc3ae7 可视为已关闭
