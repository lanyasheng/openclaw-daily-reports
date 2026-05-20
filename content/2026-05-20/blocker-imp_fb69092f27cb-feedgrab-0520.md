# Blocker: imp_fb69092f27cb — Content feedgrab 标准素材链

**日期**: 2026-05-20 11:31
**Owner**: content agent
**阻塞原因**: `feedgrab` 命令未安装，标准 feeds 目录 `/Users/study/.openclaw/shared-context/content/feeds/` 不存在。web_search 工具返回 404 错误。
**连续提及次数**: 12 次 (首次: 2026-05-02)
**上一次动作**: 2026-05-19 写入 blocker，请求主会话执行 feedgrab 安装验证
**本次心跳状态**: 已识别但未解决，工具链配置超出 content agent 范围

**本次尝试**:
- 检查 web_search 工具状态: 返回 "Ollama web search failed (404): 404 page not found"
- 检查 feedgrab 技能文件: `~/.openclaw/skills/feedgrab/SKILL.md` 存在
- 检查 feeds 目录: `/Users/study/.openclaw/shared-context/content/feeds/` 不存在
- 确认需要主会话安装 feedgrab 并配置 feeds 目录
- 本次心跳无新进展

**下一步动作**: 请求主会话执行最小验证：`which feedgrab` 确认安装状态；如未安装，执行安装并抓 1 条公开 URL 验证链路。
**证据路径**: `/Users/study/.openclaw/workspace-content/knowledge/daily/2026-05-20/blocker-imp_fb69092f27cb-feedgrab-0520.md`
