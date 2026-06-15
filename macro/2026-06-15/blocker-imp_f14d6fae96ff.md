# Blocker: imp_f14d6fae96ff — Macro 增量归档 / 模板重复压缩

**ID**: imp_f14d6fae96ff
**Date**: 2026-06-15 14:32 CST
**Owner**: macro heartbeat
**Priority**: P1
**Status**: ⏳ 等待收盘后执行

## 阻塞原因
- 当前为尾盘时段（14:30 CST），A股15:00收盘，欧洲盘/美盘尚未开启关键事件
- 归档/模板压缩是收盘后的整理工作（涉及 daily-check.md 的摘要压缩 + 历史归档）
- 本周超级央行周（BOJ周三/FOMC周三），收盘后需先处理 FOMC 前瞻
- 模板重复压缩需在今日全部内容写完后进行，不宜盘中干预

## 下一次动作
- 今日 A 股收盘后（15:00+ CST）+ 美盘开盘前评估时段（20:00 CST）
- 将今日 daily-check.md 和信号跟踪文件做增量归档
- 采样最近 3 天 daily-check.md 的"执行摘要"部分评估重复率
- 如有可压缩空间，启动模板精简
