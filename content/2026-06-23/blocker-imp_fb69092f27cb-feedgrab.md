# Blocker — imp_fb69092f27cb

**ID**: imp_fb69092f27cb
**Priority**: P1
**Count**: 28
**Task**: Content feedgrab 标准素材链未执行
**Owner**: content agent (heartbeat)

## 阻塞原因
1. **web_search 工具故障**：Ollama web search 返回 404，无法通过搜索引擎抓取小红书/百度/微博热榜数据
2. **中文站点JS渲染依赖**：36氪、知乎需要JavaScript渲染，web_fetch只能拿到框架（知乎403、36氪"Please wait..."）
3. **可用替代方案未配置**：tophub.today 只能获取部分数据，小红书/微博/百度热搜无独立API接入

## 当前降级方案
- HN Front Page 直接抓取 ✓ （成功）
- tophub.today 获取少量知乎内容 ✓ （有噪音较多）
- 中文AI新闻：依靠已抓取的HN+机器之心Newsletter ✓

## 下一次动作
- 监控 web_search 是否恢复（本日余下4次扫描均会尝试）
- 如搜索持续不可用，建议配置 feedgrab 的 RSS/Atom 直连源替代搜索依赖
- 考虑接入 v2ex/知乎专栏 RSS 作为静态备选

## 证据路径
- 本次扫描报告：`knowledge/daily/2026-06-23-0912-早间全扫描.md`
- 降级抓取：HN数据有效覆盖国际AI/科技动向

## 备注
计数器28次说明feedgrab素材链长期未建立标准流程。建议在下一轮系统优化中解决此功能的搜索依赖问题。
