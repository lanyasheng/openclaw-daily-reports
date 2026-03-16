# MediaCrawler / x-reader 安装与可用性记录

## 时间
2026-03-13 11:16 CST

## 当前状态

### 1. x-reader
- 状态：已安装，可直接使用
- 路径：`/Users/study/.local/bin/x-reader`
- 验证：已成功读取 X 链接 `https://x.com/servasyy_ai/status/2031594244339876192?s=12`
- 适用场景：单条 URL 快速读取、临时总结、跨平台内容消费

### 2. MediaCrawler
- 状态：已安装到本地，可启动
- 路径：`/Users/study/.openclaw/workspace-content/tools/MediaCrawler`
- 环境：使用 `uv` 创建 `.venv` 并完成依赖安装
- 浏览器：已完成 `playwright install chromium`
- 验证：`uv run python main.py --help` 可正常启动

## 最小用法

### x-reader
```bash
x-reader "https://x.com/servasyy_ai/status/2031594244339876192?s=12"
x-reader "https://www.xiaohongshu.com/explore/xxxx"
x-reader list
```

### MediaCrawler（首次使用通常需要登录）
```bash
cd /Users/study/.openclaw/workspace-content/tools/MediaCrawler
uv run python main.py --platform xhs --lt qrcode --type search --keywords "AI工具,小红书运营"
```

常见平台：
- `xhs` = 小红书
- `dy` = 抖音
- `bili` = B站
- `wb` = 微博
- `zhihu` = 知乎

## 能力定位

### x-reader 适合
- 读单条链接
- 做快速总结
- 给 agent 喂内容

### MediaCrawler 适合
- 国内平台批量抓取
- 搜索/详情/创作者主页采集
- 评论抓取
- 竞品监控、热点监控

## 替代关系判断
- 可以弱化一部分“只负责读内容”的轻量 skill / 临时抓取流程
- 不能替代：
  - 发布类 skill（如 one-click-posting）
  - 去 AI 味 skill（content-deai-engine）
  - 预检/回调/归档类工作流
  - X 专项搜索能力（xreach 仍然有价值）

## 建议的后续统一栈
- 单条内容读取：`x-reader`
- X 搜索/时间线：`xreach`
- 中文平台批量抓取：`MediaCrawler`
- 内容改写：`content-deai-engine`
- 发布：`one-click-posting`

## 下一步建议
1. 用小红书二维码登录一次 MediaCrawler
2. 跑一轮 xhs 搜索测试
3. 再决定哪些旧的研究型 skill 可以收缩
