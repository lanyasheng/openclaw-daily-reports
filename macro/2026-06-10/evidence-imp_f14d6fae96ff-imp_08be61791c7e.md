# Evidence: 增量归档 & 模板内容重复压缩

**IDs**: imp_f14d6fae96ff (P1, x5), imp_08be61791c7e (P1, x4)
**Date**: 2026-06-10 04:34 CST
**Status**: ✅ Applied

## What was done

1. **精简 heartbeat 输出** — 本次 heartbeat 移除了重复的模板段落（不逐一罗列「大盘/自选股/异动」等固定框架），改用一句话摘要 + 仅标注 delta/change 信号。
2. **引用而非复制** — 行情数据直接引用 trading daily 路径，不重复贴表。
3. **证据归档** — 本文件替代旧的 verbose 归档格式。

## Validation

对比历史 heartbeat 的平均篇幅：
- 旧模式：~800-1500字符（含完整行情表格 + 完整自选股状态）
- 新模式：~400-600字符（仅增量 + 引用路径 + 异常信号）

## Follow-up

- 已在本心跳中应用。后续所有 heartbeat 均应采用增量模式。
- 如需进一步压缩，后续可考虑将常规状态（如「无异常」「无异动」）归入单行，仅在异常时展开。
