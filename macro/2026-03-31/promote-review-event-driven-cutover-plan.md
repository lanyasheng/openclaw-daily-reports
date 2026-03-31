# Promote-Review 事件驱动改造执行清单

**日期**: 2026-03-31 21:38 CST  
**作者**: macro  
**目标**: 退役 `macro-promote-review` / `ainews-promote-review` 的固定轮询模式，改为“写入 pending 时触发 one-shot review”的事件驱动闭环。  
**当前状态**: 两条轮询 cron 已停用（disabled），噪音已止血；事件驱动版尚未接通。

---

## 一、问题定义

当前 promote-review 机制存在 3 个问题：
1. **空轮询**：`pending_promote.json` 长期为空，但 cron 每 2 小时固定运行，持续输出 `0/0/0`。
2. **状态机脱节**：review 并不是独立业务，而是上游 `lite/weekly -> pending` 的后处理动作，却被错误建模为常驻巡检。
3. **用户感知噪音**：频道持续收到无效状态消息，无法反映真实 candidate 生命周期。

---

## 二、目标状态（事件驱动）

### 核心原则
- **无 pending，不运行 review**
- **有 pending，立即记录并创建 T+24h 的 one-shot review**
- **review 只在 veto window 到点时触发**

### 目标闭环
1. 上游 weekly/lite 选出 candidate
2. 将 candidate 写入 `pending_promote.json`，写入 `added_at` / `review_at`
3. 同步创建一个 **one-shot cron**（T+24h）
4. 到点触发 review：
   - macro：无 veto 且窗口已过 → auto promote
   - ainews：无 veto 且窗口已过 → recommend only（人工 gate）
5. review 完成后：
   - 清理 pending 条目
   - 清理 one-shot review job
   - 生成 receipt

---

## 三、职责分工

### 1) 上游负责谁写 `pending`
**Owner: main / autoresearch 实现方**

建议由以下上游承担：
- `run_macro_autoresearch_weekly.py`
- `run_ainews_autoresearch_weekly.py`（若实际脚本仍在 `repos/autoresearch-macro/` 内，则按该位置）

**动作**:
- weekly ranking 产出 Top candidate 后，不再只写 ranking/summary
- 满足 guardrail 的候选，显式写入：
  - `state/pending_promote.json`

**写入字段建议**:
```json
{
  "pending": [
    {
      "version_id": "lite-2026-03-31-h1-v1",
      "adapter": "macro",
      "title": "...",
      "score": 0.84,
      "source_run": "2026-W14-weekly-run",
      "added_at": "2026-03-31T21:40:00+08:00",
      "review_at": "2026-04-01T21:40:00+08:00",
      "manual_review_required": false,
      "status": "pending"
    }
  ]
}
```

### 2) 谁负责创建 one-shot review
**Owner: ops / main（控制面）**

最小可行方案：
- weekly 脚本在成功写入 pending 后，直接调用 OpenClaw cron API / CLI 创建 one-shot job
- job 类型为：`schedule.kind = at`
- 触发时间 = `added_at + 24h`

**Job naming 建议**:
- `macro-promote-review-once-<version_id>`
- `ainews-promote-review-once-<version_id>`

### 3) macro / ainews 分别怎么触发
#### macro
- 触发脚本：`run_macro_promote_review.py`
- 触发条件：pending 非空 + 当前 one-shot 到点
- 行为：
  - 检查 `veto.json`
  - 检查 24h window
  - 若无 veto → 更新 `current_version.json`
  - 写 `receipts/promote-*.json`
  - 清理 pending 条目
  - 结束并删除 one-shot cron

#### ainews
- 触发脚本：`run_ainews_promote_review.py`
- 触发条件：pending 非空 + 当前 one-shot 到点
- 行为：
  - 检查 `veto.json`
  - 检查 24h window
  - 仅生成 `receipts/review-*.json`
  - 输出 recommended list
  - 保持人工 gate，不自动改 `current_version.json`
  - 清理 pending 或转入 `awaiting_manual_promote`
  - 结束并删除 one-shot cron

---

## 四、最小改造步骤（建议执行顺序）

### Phase 0 — 已完成
- [x] 停用旧轮询 cron：
  - `macro-promote-review-20260330`
  - `ainews-promote-review-20260330`

### Phase 1 — 上游写 pending
- [ ] 修改 macro weekly 脚本：当选出合格 Top candidate 时写 `pending_promote.json`
- [ ] 修改 ainews weekly 脚本：当选出合格 Top candidate 时写 `pending_promote.json`
- [ ] 在写入时一并计算 `review_at = added_at + 24h`
- [ ] 保持 `promoted=false` / `manual_review_required` 语义不变

### Phase 2 — 创建 one-shot review
- [ ] weekly 写 pending 后，立即创建 one-shot cron
- [ ] cron payload 仅执行对应 review 脚本
- [ ] cron delivery 改为：
  - 只有真实 pending/review 结果时才 announce
  - pending 为空时静默

### Phase 3 — review 收口
- [ ] macro review 完成后自动清 pending + 写 receipt + 删除 one-shot job
- [ ] ainews review 完成后写 recommended receipt + 删除 one-shot job
- [ ] 如有 veto，写 veto receipt 并清理 pending/one-shot

### Phase 4 — 观测与回退
- [ ] 加一个最小状态检查：pending_count / active_one_shot_jobs / stale_pending
- [ ] 若事件驱动链路异常，可临时恢复低频静默版 review（每天 1 次，不 announce 0 值）

---

## 五、验收标准

### 功能验收
- [ ] 没有 pending 时，不再产生 review 消息
- [ ] 有 candidate 写入 pending 时，能自动创建 T+24h one-shot review
- [ ] 到点后能正确执行 macro promote / ainews recommend
- [ ] review 结束后能清理 pending 和 one-shot cron

### 体验验收
- [ ] 频道内不再出现 `Promoted: 0 / Vetoed: 0 / Waiting: 0` 的空跑噪音
- [ ] 每一条 review 消息都能指向具体 `version_id`
- [ ] 每条 review 都有 receipt，可追溯到 source run 和 review_at

### 安全验收
- [ ] macro 仍保留 24h veto window
- [ ] ainews 仍保留人工 gate
- [ ] current_version 只在 macro 的无 veto promote 时更新

---

## 六、建议的最小技术实现方式

### 方案 A（推荐，最小改动）
- 保留现有 review 脚本不动
- 只改 weekly 脚本写 pending + 创 one-shot cron
- 复用现有 review 逻辑

### 方案 B（次选）
- 新增一个统一的 `schedule_promote_review.py`
- weekly 调它来写 pending 并创建 one-shot cron
- 逻辑更清楚，但多一个控制脚本

**推荐选择**: 方案 A。因为能最快落地，且不会重写 review 核心逻辑。

---

## 七、给 main / ops 的直接动作

### 发给 main
- 负责：weekly 脚本改造（写 pending）
- 交付：真正的 candidate → pending 接线

### 发给 ops
- 负责：one-shot cron 创建/清理机制
- 交付：pending 写入后自动调度 T+24h review

---

## 八、一句话结论

> promote-review 不该再是常驻轮询任务，而应该是：**weekly 选中 candidate → 写 pending → 自动创建 T+24h one-shot review → 到点审查并收口。**

这能同时解决：空轮询、刷屏、状态机脱节三类问题。
