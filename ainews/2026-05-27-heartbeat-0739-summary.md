# AI 哨兵心跳摘要 — 2026-05-27 07:39 CST

数据源：RSS 聚合 101 源，成功 87 源，1 日窗口共 798 条；归档：`knowledge/daily/2026-05-27-heartbeat-0739-rss.json`、`2026-05-27-heartbeat-0739-github.txt`、`2026-05-27-heartbeat-0739-arxiv.txt`。

## 判断

- 本轮相对 07:11 摘要未发现新增重大 AI/技术动态；不重复紧急推送。
- 仍需关注的重大事项与上一轮一致：BadHost/Starlette 漏洞、OpenRouter B 轮、Qualcomm-ByteDance ASIC 传闻、ECB 对 AI 私募信贷风险提示、中国 AI 人才出境审批传闻。

## 本轮复核要点

1. **BadHost / Starlette 漏洞**
   - Ars Technica：Starlette < 1.0.1 / CVE-2026-48710，影响 FastAPI、vLLM、LiteLLM、TGI、MCP servers、agent harnesses 等。
   - 判断：安全类重大动态，但已在 07:11 归档。

2. **OpenRouter 融资**
   - TechCrunch：OpenRouter $113M Series B，CapitalG 领投，NYT 称估值约 $1.3B；披露约 8M 用户、100T tokens/月。
   - 判断：AI 基础设施/模型路由商业化信号，已在 07:11 归档。

3. **Qualcomm / ByteDance AI ASIC**
   - Reuters/Bloomberg：Qualcomm 据报将向 ByteDance 供应 AI 数据中心 ASIC，QCOM 消息后上涨约 5%。
   - 判断：投资与供应链信号，已在本轮尝试转发 trading，但当前无 `trading` label 会话。

4. **宏观/政策**
   - FT/RSS：ECB 警示 private-credit fueled AI boom 风险；The Decoder/Bloomberg：报道称中国扩大顶尖 AI 人才出境审批。
   - 判断：宏观/政策信号，已在本轮尝试转发 macro，但当前无 `macro` label 会话。

## 协作信号状态

- `sessions_send(label="trading")` → 失败：No session found with label: trading。
- `sessions_send(label="macro")` → 失败：No session found with label: macro。

## 数据源异常

部分源返回 404/308/500（如 Google AI Blog、HuggingFace Daily Papers、Meta AI Blog、Semafor AI、MCP Spec Releases、VentureBeat AI 等），不影响本轮主要判断。
