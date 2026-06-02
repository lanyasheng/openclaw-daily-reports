# Macro Heartbeat 09:07 CST — Oil / FX / Rates Check

- 时间：2026-06-02 09:07 CST（用户心跳时间）
- 目的：按 `HEARTBEAT.md` 检查重大央行/经济数据、汇率/利率异常波动，并读取 Trading daily 市场上下文。

## 央行/经济日历

- BLS JOLTS：April 2026 JOLTS 定于 2026-06-02 10:00 ET（22:00 CST）发布，尚未到点。
- FOMC：下一次会议 2026-06-16/17。
- BOJ：下一次 MPM 2026-06-15/16。
- 本次心跳未发现 09:07 CST 前后已经落地的新增重大央行政策决定。

## 最新跨资产快照

Stooq 最新可得（页面时间约 2026-06-02 03:07 CEST，对应 09:07 CST 附近）：

- WTI `CL.F`：91.99；日内区间 91.65–92.64。
- DXY `DX.F`：99.142；日内区间 99.120–99.180。
- USDJPY：159.6635；日内区间 159.6165–159.7235。
- USDCNY：6.76276；日内区间 6.76250–6.76544。
- USDHKD：7.83789；日内区间 7.83685–7.83795。
- SPY：758.54（2026-06-01 美股收盘）。

美国财政部收益率曲线最新官方数据（2026-06-01）：

- 2Y 4.05%（较 5/29 的 3.98% 上行 7bp）
- 10Y 4.47%（较 5/29 的 4.45% 上行 2bp）
- 30Y 4.99%（与 5/29 持平）

## Trading daily 已读取

- `workspace-trading/knowledge/daily/2026-06-02/macro-handoff-oil-shock-0806.md`
- `workspace-trading/knowledge/daily/2026-06-02/preflight-macro-thresholds.md`

Trading 已将油价 >$90 / >$95 阈值、JOLTS 22:00、能源受益/油耗承压映射纳入晨报口径。

## 判定

- 原油仍处于事件冲击观察区间，但未突破 Trading/Macro 预设的 >$95/$96 升级阈值。
- FX 未见失序：USDCNY 仍低于 6.80；USDHKD 稳定。
- 利率有温和上行，但 10Y +2bp、30Y 持平，尚未形成新的利率冲击。
- 暂无需要重复通知 Trading 的新增宏观变化；保留 22:00 CST JOLTS 为下一关键触发。