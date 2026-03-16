# content 浏览器策略调整说明

日期：2026-03-15

## 结论
content 侧浏览器执行策略调整为：
- **默认优先：agent-browser**
- **兜底回退：现有 OpenClaw browser**

## 适合 agent-browser 的任务
- 网页素材采集
- 搜索结果抓取
- 列表页抽取
- 竞品文章/标题/链接整理
- 规则明确、批处理优先的公开页面任务

## 必须回退到现有 browser 的任务
- 需要复用登录态
- 需要接管老板当前 Chrome 标签页
- 多标签 / iframe / 复杂交互
- 首次探索型任务
- agent-browser 抽取结果不稳定

## 口径
content 不把 agent-browser 视为唯一浏览器底座，而是把它视为默认优先执行器；现有 browser 继续作为公司级兜底能力。
