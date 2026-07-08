# Follow-up Evidence: imp_c5138650f643 — 标准目录结构缺失

**检查时间**: 2026-07-08 08:40 CST
**检查 Agent**: ainews (heartbeat)
**状态**: ⚠️ 部分修复

---

## 检查项

### ✅ 已就位

| 目录/文件 | 状态 | 说明 |
|:---|:---:|:---|
| `knowledge/daily/YYYY-MM-DD/` | ✅ | 每日子目录按日期创建 |
| `knowledge/daily/YYYY-MM-DD/morning-digest.md` | ✅ | 今日已生成 |
| `knowledge/weekly/` | ✅ | 存在（有历史周报） |
| `knowledge/sources.md` | ✅ | 存在 |
| `knowledge/data_sources.md` | ✅ | 存在 |

### ❌ 缺失/待完善

| 目录/文件 | 状态 | 说明 |
|:---|:---:|:---|
| `knowledge/paper-digest/` (独立目录) | ❌ | 仅有 `daily/*/paper-digest.md` 文件，无聚合目录 |
| 统一输出目录规范 | ❌ | morning-digest → `daily/`，但 paper-digest 没有独立归档 |
| 通过 cron 自动生成的目录结构定义 | ❌ | 缺少 `structure.yaml` 或 `expected-files.yaml` 规范文件 |
| `cron/jobs-state.json` 的追踪完整性 | ❌ | _recentRuns 数组始终为空 |

---

## 建议的标准目录结构

```
knowledge/
├── daily/YYYY-MM-DD/
│   ├── morning-digest.md      ← 08:30 cron
│   ├── paper-digest.md        ← 12:00 cron
│   ├── evening-report.md      ← 20:00 cron
│   ├── daily-ops-summary.md   ← 21:50 cron
│   ├── evidence-*.md          ← 反思闭环证据
│   └── injected-improvements.md  ← 自动注入
├── weekly/YYYY-WW/
│   └── weekly-review.md
├── sources.md
├── data_sources.md
└── expected-contents.yaml     ← 新增：目录结构规范定义
```

---

## 结论

标准目录结构的基础部分（每日子目录 + morning-digest）已经正常工作。主要缺失的是：
1. 一个明确的目录结构规范文件（`expected-contents.yaml`），用于自动校验
2. `paper-digest.md` 的输出一致性依赖于中午 cron 的执行结果

**建议**: 创建一个 `knowledge/expected-contents.yaml` 文件定义每日产出规范，并集成到 `ainews-archive-consistency-check` cron 中进行每日校验。

## 补充验证 (2026-07-08 21:30 CST — daily reflection)

**状态**: ⚠️ **blocked** — 根因不变，ainews 无法自行修复

### 今日验证结果

今日标准目录结构完整性：

| 文件 | 状态 | 大小 |
|:---|:---:|:---:|
| morning-digest.md | ✅ | 18341 bytes |
| paper-digest.md | ✅ | 7091 bytes |
| evening-report.md | ✅ | 8801 bytes |
| 01-followup-open-items.md | ✅ | 1093 bytes |
| 00-injected-improvements.md | ✅ | 1790 bytes |
| evidence-imp_*.md x3 | ✅ | ~6.3K total |

### 结论

今日标准目录结构完整，但根因（openclaw.json 中 cron.jobs 为空）尚未修复。

| 维度 | 状态 |
|:---|:---:|
| 今日目录结构 | ✅ 完整 (3/3 + 证据文件) |
| 长期可靠性 | ⚠️ blocked (requires operator) |
| expected-contents.yaml | ❌ 未创建 |
