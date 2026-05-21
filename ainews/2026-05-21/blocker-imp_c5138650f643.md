# Blocker: imp_c5138650f643 - AINews cron 调度链路中断 / 标准目录结构缺失

**ID**: imp_c5138650f643
**日期**: 2026-05-21
**状态**: 阻塞中（第 8 天）
**Owner**: ainews agent
**阻塞原因**: cron 调度链路部分恢复迹象（晚报回归），但晨报/午报仍缺失，需老板介入确认 cron/jobs.json 调度状态

## 当前状态

### 05-21 产出情况（部分恢复）
- ✅ `evening-report.md` 存在（8290 bytes，6条新增+3条重大更新+4条趋势分析）— 晚报正常归档
- ❌ `morning-digest.md` 缺失
- ❌ `paper-digest.md` 缺失
- 归档覆盖率：1/3（33%）

### 与近期对比
| 日期 | 晨报 | 午报 | 晚报 | 备注 |
|------|------|------|------|------|
| 05-15 | ✅ ai-news-summary | ✅ paper-digest | ✅ evening-report | 完整 |
| 05-16 | ❌ | ❌ | ❌ | 仅 ops-summary |
| 05-17 | ✅ morning-digest | ❌ | ❌ | 仅晨报 |
| 05-18 | ❌ | ❌ | ❌ | 仅扁平文件 |
| 05-19 | ❌ | ❌ | ✅ evening-report | 仅晚报 |
| 05-20 | ❌ | ❌ | ✅ evening-report | 仅晚报 |
| 05-21 | ❌ | ❌ | ✅ evening-report | 仅晚报 |

### cron/jobs.json 状态
- ainews-morning-digest / ainews-paper-digest / ainews-evening-report 三个核心任务 lastRunStatus/lastExecutionTime 均为 "?"，调度状态追踪持续失效。

## 下一步行动

1. **老板决策**：确认 cron 调度链路是否需要修复，或接受当前降级模式（仅晚报）。
2. 若 cron 恢复，优先补产晨报（18+条）和论文速递（6-8篇）。
3. 若 cron 不可恢复，确认降级策略并更新 SOUL.md 配额口径。

## 证据
- 产出文件: `/Users/study/.openclaw/workspace-ainews/knowledge/daily/2026-05-21/evening-report.md`
- 运行日志: 当日 evening-report.md 内容完整，6条新增+3条重大更新+4条趋势分析
- autoresearch-lite: 3 candidates 生成成功，全部 promoted=false

---
*此 blocker 由每日反思更新*
