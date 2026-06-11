# Gaetano / Crux Capital 人工复核后重算结果

## 一句话结论

人工复核后，这版数据从“自动抽取的 124 条信号”收敛为“94 条可保留/降权的语义信号 + 12 条高质量 thesis + 30 条剔除项”。主要污染源是第三方引用、复盘/战绩展示、旧主题 quote，以及 ticker 只是对比对象。

## 复核规模

- 全量 ticker-level rows：124
- 人工 forward clean rows：94
- 人工 high-quality thesis rows：12
- 人工剔除 rows：30

## 人工动作分布

- keep_deweighted: 48
- deweight: 34
- delete_from_forward: 30
- keep: 12

## 复核后主题分布

- ai_infrastructure: 55
- technical_trading: 11
- growth_momentum: 11
- other: 9
- semiconductor_supply_chain: 5
- business_quality: 2
- crypto_market_structure: 1

## 复核后 ticker Top 20

- POET: 15
- IXHL: 8
- LITE: 6
- COHR: 5
- SIVE: 4
- MRVL: 4
- ALMU: 4
- AAOI: 3
- AEHR: 3
- AXTI: 3
- GLW: 2
- P: 2
- ITRM: 2
- ABCL: 2
- IREN: 2
- VIAV: 2
- COHU: 2
- SMTC: 1
- CIEN: 1
- FN: 1

## 人工确认 high-quality thesis ticker

- POET: 2
- LITE: 2
- AAOI: 1
- GLW: 1
- P: 1
- SMTC: 1
- CIEN: 1
- FN: 1
- TSEM: 1
- ENTG: 1

## 人工 forward clean 表现

| horizon | n | avg | median | win_rate |
|---|---:|---:|---:|---:|
| 1d | 24 | -2.60% | -3.66% | 29.17% |
| 5d | 17 | 19.28% | 14.26% | 94.12% |
| 20d | 13 | 33.62% | 27.14% | 76.92% |
| 60d | 4 | 44.39% | 30.15% | 75.00% |
| 120d | 2 | 265.06% | 189.59% | 100.00% |

## 人工 high-quality thesis 表现

| horizon | n | avg | median | win_rate |
|---|---:|---:|---:|---:|
| 1d | 4 | 0.22% | -2.47% | 25.00% |
| 5d | 4 | 11.95% | 1.37% | 75.00% |
| 20d | 3 | 27.52% | 27.14% | 66.67% |

## 主要剔除原因

- quoted_retrospective_theme_context: 12：ticker 来自被引用的旧主题或复盘，不按当前日期算 forward signal。
- third_party_quote: 4：核心 ticker 来自第三方引用，不是 Gaetano 自己的新观点。
- comparison_only: 4：ticker 只是对比对象或参照物，不是该帖的研究标的。
- not_gaetano: 1：作者不是 Gaetano，不能作为他的信号。
- post_move_noise: 1：上涨/异动后的评论，不进入 forward signal。
- intraday_noise: 1：盘中状态或噪音，不进入 forward signal。
- retrospective_track_record: 1：当前帖是战绩或历史观点回顾，不能按当前日期算 forward signal。
- potential_acquirer_context: 1：该 ticker 是潜在收购方/合作方，不是信号标的。
- demand_source_only: 1：该 ticker 只是需求源，不是研究标的。
- retrospective_level_claim: 1：价格到达 watchlist level 后的复盘，不进入 forward signal。
- missed_entry_retrospective: 1：明确错过入场或已经上涨后的复盘，剔除。
- quoted_context_only: 1：ticker 只在引用上下文中出现，不是主帖信号。
- duplicate_cross_listing: 1：跨市场或同公司重复 ticker，避免重复计入。

## 关键人工判断

- Serenity 引用帖中的 `$NBIS/$CRWV/$IREN` 等不算 Gaetano 自己的新信号。
- BenzyStocks 的 `$GLW` 帖不是 Gaetano 本人观点，剔除。
- Physical AI 预告帖里引用的光学 ticker 属于旧主题/复盘语境，不按当前日期计入 forward signal。
- `SIVEF` 与 `SIVE` 视为同一公司/跨市场重复表达，保留主 `SIVE`，剔除重复信号。
- 只说 hit level、missed entry、halt、after-move 的帖子不作为前瞻研究信号。

## 对模型的影响

- 复核后，Gaetano 的有效模型更偏向 photonics / optics / AI infrastructure，而不是所有被引用 ticker。
- 剔除引用、复盘、第三方和比较对象后，模型更接近“本人前瞻研究逻辑”。
- `keep` 级别集中在 chokepoint、供应链位置、容量/执行风险、客户/收入可见度这些结构。
- `deweight` 可以保留在主题分布中，但不应作为强收益统计的核心证据。

## 仍需补齐

- X long thread 的完整正文仍缺，只能基于首帖/可见摘要判断。
- `IXHL`、`ALMU`、`AIP` 等小票 ticker 仍建议做交易所/标的确认。
- 当前价格评估只覆盖本地已有 Yahoo 价格文件；未覆盖 ticker 不能得出收益结论。
- 如果拿到完整 X archive / Apify / API 数据，应重新跑本轮人工规则。
