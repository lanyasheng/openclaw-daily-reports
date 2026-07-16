# Blocker: imp_fb69092f27cb — Content feedgrab 标准素材链

| Field | Value |
|-------|-------|
| **ID** | `imp_fb69092f27cb` |
| **Priority** | P1 |
| **Date** | 2026-07-16 01:31 CST |
| **Slot** | 凌晨安静时段 |

## 阻塞原因

feedgrab 标准素材链需要：
1. 定义标准化的素材 schema（标题/摘要/来源/热度指标/分类标签/可转化度评分）
2. 建立从各热点源（HN/小红书/知乎/微博/百度/36氪/arXiv）到统一素材池的 ETL pipeline
3. 实现素材去重与热度衰减
4. 对接内容生成引擎（social-media-agent / copywriting 等）的输出接口

这是**基础设施层改造**，与 publish queue 有依赖关系（素材链 → 生成 → 发布队列），建议与 imp_d60357465ff5 一并设计。

## Owner

- **Architecture**: self (blocked on publish queue design)

## 下次动作时间

06:00 凌晨复盘时评估是否将两个 imp 合并为一个统一的内容 pipeline 架构设计 session。
