# Blocker: imp_df587e127123 — Ripple 传播预测引擎

| Field | Value |
|-------|-------|
| **ID** | `imp_df587e127123` |
| **Priority** | P1 |
| **Date** | 2026-07-16 11:32 CST |
| **Slot** | 午间脉冲后 |

## 阻塞原因

Ripple 传播预测引擎需要：
1. 定义传播预测的 schema（平台权重/话题衰退曲线/情绪极性/用户画像匹配度）
2. 接入历史发布数据作为训练/校准样本（目前尚无发布记录）
3. 依赖 Content 发布闭环（imp_d60357465ff5）完成后才能有实际数据
4. 与 content-ideas 的传播预测字段对齐

核心阻塞：Ripple 需要**发布历史回执数据**来校准预测，而发布闭环还未实现。

## 取消建议

由于 Ripple 预测引擎在不具备发布-回执闭环的情况下没有实际校准数据，建议将此改进项标记为 **depends on imp_d60357465ff5**，且仅在发布闭环上线后才重新激活。

## Owner

- **Architecture**: self (but blocked on P0 publish queue)

## 下次动作时间

跟随 imp_d60357465ff5 发布闭环完成后再评估。
