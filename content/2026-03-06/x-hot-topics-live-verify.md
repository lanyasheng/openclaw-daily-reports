# X 热点抓取验收（即时）

- 时间：2026-03-06 14:08 (Asia/Shanghai)
- 链路：`xreach --proxy http://127.0.0.1:1087`
- 结论：可抓取（无 proxy 仍会超时）

## 验收命令

```bash
xreach --proxy http://127.0.0.1:1087 search "GPT-5.4 since:2026-03-05" --type top -n 5 --json
```

## 样例结果（节选）

1. GPT-5.4 is launching（OpenAI）
- 时间：Thu Mar 05 18:19:02 +0000 2026
- 互动：like 11,504 / view 1,000,527

2. GPT-5.4 Thinking and Pro are rolling out now
- 时间：Thu Mar 05 18:10:38 +0000 2026
- 互动：like 20,638 / view 4,558,947

3. US issued a general license for some Russian oil sales to India
- 时间：Fri Mar 06 00:57:58 +0000 2026
- 互动：like 489 / view 45,139

## 当前限制

- `xreach` 直连 `x.com` 超时；必须显式带 `--proxy`。
- 社会热点查询噪音偏高，需要做关键词白名单和低互动过滤。
