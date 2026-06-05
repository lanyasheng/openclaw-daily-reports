# Blocker: imp_fb69092f27cb — feedgrab 标准素材链

**Owner**: content agent  
**Blocking status**: ⚠️ 部分可用，核心功能受阻  
**Current count**: 20 次记录

## 现状

### ✅ 可用功能
- `feedgrab` CLI 已安装（`/opt/homebrew/bin/feedgrab`）
- RSS 抓取、通用网页 Jina Reader 可用
- 已成功用于多轮心跳数据采集（web_fetch 降级方案正常）

### ⛔ 受阻功能
- **X/Twitter 搜索（`feedgrab x-so`）**：❌ 无 Twitter Cookie，需执行 `feedgrab login twitter`
- **小红书搜索（`feedgrab xhs-so`）**：❌ 需要登录 + 安装浏览器引擎
- **微信公众号搜索**：❌ 需要 Cookie

### 降级方案已生效
当前心跳通过以下方式替代：
- `web_fetch` 直接拉取 AI News RSS / 小红书热榜页面
- Yahoo Finance 拉取市场数据
- 每次心跳仍有合理的热点覆盖

## 需要的操作

```bash
# 一次性解决：
feedgrab login twitter    # 弹出浏览器窗口完成 X 授权
# 或手动设置 Cookie：
export X_COOKIE="..."
```

## 建议
1. **P0**：完成 X Twitter 登录（哪怕一次），feedgrab 即可做 X 关键词实时搜索
2. **P1**：考虑 `pip install "feedgrab[stealth]"` 提升反检测能力
3. 当前降级方案（web_fetch）对心跳覆盖足够，不影响热点发现质量
