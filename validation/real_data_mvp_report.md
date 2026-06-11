# Gaetano / Crux Capital Real-Data MVP Report

## Boundary

- This report analyzes public-post signals, not private P&L.
- Quote-only, retrospective, paid-only, and private-context rows must be removed or deweighted before model conclusions.

## Data Scale

- signal rows: 124
- unique tickers: 45
- evaluated rows: 32

## Semantic Review

- keep_deweighted: 107
- keep: 9
- deweight: 8

## Top Themes

- ai_infrastructure: 77
- technical_trading: 14
- growth_momentum: 14
- other: 11
- semiconductor_supply_chain: 5
- business_quality: 2
- crypto_market_structure: 1

## Top Tickers

- POET: 16
- IXHL: 10
- LITE: 9
- COHR: 8
- SIVE: 6
- AAOI: 5
- AEHR: 5
- AXTI: 5
- GLW: 4
- MRVL: 4
- ALMU: 4
- CIEN: 3
- IREN: 3
- NVDA: 3
- VIAV: 3
- P: 2
- ITRM: 2
- ABCL: 2
- CRWV: 2
- NBIS: 2
- COHU: 2
- SMTC: 1
- FN: 1
- TSEM: 1
- GOOGL: 1

## Forward Return Summary

- 1d: n=32, avg=-0.82%, median=-2.47%, win_rate=40.62%
- 5d: n=25, avg=15.48%, median=8.57%, win_rate=84.00%
- 20d: n=18, avg=29.85%, median=20.55%, win_rate=72.22%
- 60d: n=7, avg=33.28%, median=27.19%, win_rate=85.71%
- 120d: n=2, avg=265.06%, median=340.53%, win_rate=100.00%

## Serenity-Grade Gaps

- Confirm whether the dataset includes replies and quote context.
- Manually review the top 200 ambiguous or high-engagement rows.
- Verify fake tickers, sarcasm, retrospective language, and quote ownership.
- Re-run split, template, and evaluation after manual corrections.
