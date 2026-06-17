# Blocker — imp_fb69092f27cb: Content feedgrab 标准素材链未执行

**ID**: imp_fb69092f27cb
**Priority**: P1
**Blocked count**: 27
**Owner**: content agent (via heartbeat)
**Status**: ❌ BLOCKED

## 阻塞原因

1. **feedgrab CLI/Node 依赖未就绪** — feedgrab 技能 (`~/.openclaw/skills/feedgrab/`) 存在，但未在 $PATH 中检测到 `feedgrab` 可执行文件或 npm 包
2. **目标平台间接不可用** — 当前扫描发现多个平台被墙/限流：
   - X (Twitter): 401 blocked
   - Xiaohongshu: blocked
   - AINews: JS paywall timeout
   - Web search: Ollama 404
3. **无 feedgrab 自动化调度** — 未配置 cron/trigger 驱动 feedgrab 作为标准素材链入口

## 当前替代方案

heartbeat 已 fallback 到：
- ✅ HN Front Page + 手动过滤（主要可用源）
- ✅ X 五篮子雷达（限速但仍可读取）
- ✅ 知乎/微博/百度/抖音/头条热榜（正常可用）
- ✅ 36氪/虎嗅/澎湃行业新闻（正常可用）

## 下一次动作

- 部署 feedgrab CLI (`npm install -g feedgrab` 或 `npx feedgrab`)
- 配置标准素材链 trigger（如每天 06:00/18:00 cron）
- 或等待平台接入状态恢复后自动切换

## 被引用的扫描文件

- 本日所有 heartbeat check 正常运行
- 素材库: `knowledge/daily/2026-06-17/research-materials.md`
