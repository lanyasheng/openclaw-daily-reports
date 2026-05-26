# Macro heartbeat check — 2026-05-26 11:10 CST

## Scope
Per `/Users/study/.openclaw/workspace-macro/HEARTBEAT.md`: central bank/economic data, FX/rates abnormal moves, and trading handoff if macro signals affect stocks.

## Findings
- PBOC: 2490亿元 7天期逆回购，利率1.40%；昨日为2580亿元，利率1.40%。政策利率未变。
- Fed: no FOMC today; next scheduled FOMC 2026-06-16/17. April meeting minutes released 2026-05-20.
- BLS: no core CPI/jobs/PPI release on 2026-05-26. BEA: GDP second estimate + Personal Income and Outlays scheduled 2026-05-28 08:30 ET / 20:30 CST.
- US rates: CNBC US10Y 4.51%, -6.2bp vs prev close 4.572%.
- FX: DXY 99.049 (-0.19%); Stooq USD/CNY 6.7866, day range 6.7835–6.7896. No synchronous RMB pressure.
- Oil: CNBC WTI Jul'26 91.56 (-5.22%), day low 89.41; CNBC Brent Jul'26 97.87 (+1.80%). Brent has crossed the earlier 97 reversal-watch threshold while WTI remains below the 94 threshold.
- Gold: CNBC Gold Jun'26 4533.60 (+0.23%), stable after prior volatility.

## Action
Sent cross-session update to `agent:trading:main:heartbeat` at ~11:10 CST recommending downgrading oil-chain signal from one-sided pressure to split/observation unless WTI recovers 94 or Brent holds >97.

## Trading feedback received (~11:10 CST)
Trading agrees with downgrading oil from “one-sided pressure” to “split/observation,” but A-share energy-chain flows have not confirmed reversal:
- 601857 中国石油: 10.83, +0.93%, vol ratio 1.12, OI -0.108, not accumulation.
- Oil services: 600871 -1.23% / OI -0.183 distribution; 600583 -1.03% / OI -0.138 distribution; 603619 -1.91% / OI -0.007 neutral but weak price.
- Chemical ETFs: 159870 -0.12%, OI +0.070 below +0.08 accumulation threshold; 516570 +0.20%, OI -0.034 neutral.

Joint working threshold:
- Keep energy-chain caution for now.
- Revoke the morning oil-pressure assumption only if WTI recovers 94 or Brent holds above 97, and after 14:00 CST 601857/oil services/chemical ETF OI turns positive above +0.08.
