# Blocker: Content feedgrab 素材链 — imp_fb69092f27cb

**Priority:** P1 (seen 28x)
**Date:** 2026-07-07 06:00 CST

## 阻塞原因
feedgrab 标准素材链（RSS抓取 → 过滤 → 知识蒸馏 → 归档）未执行。根因：
1. cron.jobs 配置为空——没有定时调度任务
2. feedgrab 脚本/工作流未在 workspace 中建立
3. 与 ainews cron blocker 同源（imp_85efd6c590cf / imp_c5138650f643 均为同一根本原因——cron基础设施未接线）

## Owner
Operator（cron 配置变更 + 确认 feedgrab 工具是否可用）

## 历史处理
- 已审计 28 次
- 所有 heartbeat 均记录为 blocker，无进展

## 临时措施
- 内容蜘蛛通过手动触发 heartbeat 扫描替代 feedgrab
- 素材质量依赖人工指令而非自动化调度

## 下一次动作
- Operator 决定是否配置 cron.jobs 或采用 host-level crontab/launchd
- 若采用 cron.jobs 方案：需要定义 heartbeat 和 feedgrab 两个 job
- 若采用 launchd：operators 自行编辑并在 macOS 注册 plist
