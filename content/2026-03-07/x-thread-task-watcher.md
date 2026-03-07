# task-watcher X Thread

## Meta
- Date: 2026-03-07
- Platform: X / Twitter
- Topic: task-watcher Skill 推广
- GitHub: https://github.com/lanyasheng/task-watcher
- ClawHub: `clawhub install task-watcher`

## Tweet 1
刚把 `task-watcher` 发到 GitHub + ClawHub。

它解决的是一个很具体但很烦的问题：长任务已经提交了，但你还得一直手动盯状态。

比如：小红书审核、PR 合并、部署完成、定时任务跑完。

`task-watcher` 的思路是：注册任务 -> 定时检查状态 -> 状态变化时主动回调通知你。

GitHub: https://github.com/lanyasheng/task-watcher
ClawHub: clawhub install task-watcher

## Tweet 2
这个 Skill 适合一切“先提交、后等待”的异步场景。

我目前最看重 3 个用法：
1. 发完内容后盯审核状态
2. 盯 GitHub PR / CI 结果
3. 盯 cron / 部署任务有没有真正跑完

你不用每隔几分钟自己去刷新页面，等状态变了再收到提醒就行。

## Tweet 3
实现上也尽量做得朴素稳定：

- JSONL 持久化 + 文件锁
- Adapter / Notifier / Policy 可插拔
- 默认支持 XHS / GitHub PR / Cron Job 这类场景
- 可设过期时间，避免任务永远挂着
- 通知失败会自动升级处理

没有重依赖，Python stdlib 就能跑。

## Tweet 4
如果你也在做一人公司、自动化运营或者多 Agent 工作流，这种“任务提交后自动盯结果”的小组件会越来越有用。

少一点手动刷新，多一点异步回调。

GitHub: https://github.com/lanyasheng/task-watcher
ClawHub: clawhub install task-watcher

想看我下一条拆它的实现结构，可以留言，我继续写。
