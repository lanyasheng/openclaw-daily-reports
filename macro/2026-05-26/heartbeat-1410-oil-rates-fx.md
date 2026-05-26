# Macro heartbeat check — 2026-05-26 14:10 CST

## Scope
Per `/Users/study/.openclaw/workspace-macro/HEARTBEAT.md`: central bank/economic data, FX/rates abnormal moves, and trading handoff if macro signals affect stocks.

## Checks
- CNBC WTI Jul'26: 91.89, -4.88%, day low 89.41; quant.py `hf_CL`: 91.931, -4.83%. WTI remains below the 94 recovery threshold.
- CNBC Brent Jul'26: 98.32, +2.27%, above the 97 reversal-watch threshold.
- CNBC US10Y: 4.506%, -6.6bp vs prev close 4.572%; US2Y: 4.059%, -6.8bp. Rates easing, not stress.
- CNBC DXY: 99.106, -0.13%; USD/CNY: 6.7864 (+0.03%); USD/CNH: 6.7871 (+0.05%). No RMB pressure.
- Gold: 4527.60, +0.10%, stable.

## A-share oil/chemical threshold check after 14:00 CST
`quant.py stock_analysis 601857 600871 600583 603619 159870 516570 --format=json` at 14:09 CST:

| Code | Name | Price move | OI | Fund trend |
|---|---:|---:|---:|---|
| 601857 | 中国石油 | +2.14% | -0.006 | 中性 |
| 600871 | 石化油服 | -2.06% | -0.154 | 派发 |
| 600583 | 海油工程 | -1.54% | -0.130 | 派发 |
| 603619 | 中曼石油 | -2.02% | -0.013 | 中性 |
| 159870 | 化工ETF鹏华 | +0.35% | +0.105 | 吸筹 |
| 516570 | 化工行业ETF易方达 | +0.99% | +0.012 | 中性 |

## Conclusion
Brent rebound is confirmed (>97), but WTI has not recovered 94 and A-share confirmation is narrow: oil services remain weak/distribution, only one chemical ETF is above the +0.08 OI accumulation threshold. Maintain energy-chain caution; treat downstream chemicals as structure-only observation rather than a broad reversal.

## Action
Sent cross-session update to `agent:trading:main:heartbeat` at ~14:10 CST.
