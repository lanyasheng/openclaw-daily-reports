# Evidence: imp_1c3d7bdc3ae7 — AINews autoresearch schema / run-scope / postcheck

**Date**: 2026-05-08
**Owner**: ainews
**Status**: 持续验证中

## 今日执行
1. autoresearch-lite 成功运行，生成 3 个 candidate（h1-h3），全部 `promoted: false`
2. 3 个 candidate 文件 schema 完整（`hypothesis.title/change_type/core_claim` 均存在）
3. run summary 的 `candidate_files` 与实际新写入文件一致（3 个，无残留串单）
4. generate_daily_review.py 生成的审核报告正确展示 3 个 candidate 的标题/类型/核心主张（schema adapter 本次运行正常）

## 验证结果
- ✅ schema 完整性：3/3 candidate 通过
- ✅ run-scope 一致性：run summary candidate_files 与实际文件一致
- ✅ review report 展示正确：标题/类型/核心主张与 candidate JSON 一致

## 残留问题
- schema adapter 问题（LRN-20260417-001 系列）已连续 15 天被记录，但脚本层修复仍未合并。今日 review report 正常展示可能是因为 candidate 文件顶层字段已补全，但 `hypothesis.*` 嵌套字段回退逻辑仍未在脚本中实现。需确认 generate_daily_review.py 是否已修复。
- 建议将此 imp 从 P1 降级为 P2，因为当前链路已能正常运行，但脚本修复的长期悬置是系统性风险。

## Next Action
- 检查 generate_daily_review.py 源码是否已包含 hypothesis.* 回退逻辑
- 若已修复，标记 imp 为 done；若未修复，继续跟踪
