# Gaetano / Crux Capital 真实数据 MVP 状态

运行目录：`real_runs/gaetano_crux_capital_mvp_20260611`

## 当前结论

这已经不是最早的 seed 版，而是“登录态 X 浏览器采集增强版 MVP”。

它使用了真实公开/登录态可见数据：

- 公开 Substack seed 页面
- logged-out X public seed
- 用户登录 X 后，通过本地 Edge CDP 控制采集的 X 搜索/月度切片数据

但它仍然不是完整 Serenity A 级全量版，因为它还不是官方 X API / Apify / 用户 X archive 的完整导出。

## 当前数据规模

- 合并后的 source rows：94
- ticker-level signals：124
- `signals_forward_clean.csv`：124
- `signals_high_quality_thesis.csv`：9
- `manual_review_queue.csv`：124
- `manual_review_priority_top200.csv`：124
- forward-clean 可评估样本：32
- high-quality thesis 可评估样本：4

## 新增的真实 X 数据

本轮用户已在浏览器登录 X。采集器：

`x-trader-skill-builder/collectors/browser_scroll_cdp.mjs`

实际可用路线：

```text
from:crux_capital_ -filter:replies since:YYYY-MM-DD until:YYYY-MM-DD
```

按月切片后得到：

- 月度 X browser rows：58
- 合并增强源文件：`sources/posts_browser_augmented.csv`
- 合并增强后 source rows：94

说明：

- 这是真实登录态 X 页面渲染数据。
- 采集器会尝试自动点击“显示原文 / Show original”。
- profile 页本身只返回了顶部少量帖子，所以主要采用 X search 月度切片。
- 这仍可能漏掉 replies、quotes、被 X 排序隐藏的帖子、删除帖、深层对话关系。

## 当前主题结构

自动复核后，Gaetano 的高频主题仍集中在：

1. Photonics / optics
2. AI infrastructure
3. Physical AI
4. data-center interconnect
5. optical networking / CPO / NPO
6. semiconductor supplier read-through
7. capacity、margin、execution risk

## 当前 ticker 分布

新增 X 数据后，top ticker 包括：

- `POET`
- `IXHL`
- `LITE`
- `COHR`
- `SIVE`
- `AAOI`
- `AEHR`
- `AXTI`
- `MRVL`
- `ALMU`
- `GLW`
- `NVDA`
- `VIAV`
- `IREN`
- `CIEN`

## 价格评估状态

Yahoo 现场下载仍然被限流：

```text
YFRateLimitError: Too Many Requests
```

所以本轮 forward return 使用已有本地真实 Yahoo 价格文件覆盖的 ticker：

- `AAOI`
- `POET`
- `LITE`
- `COHR`
- `AEHR`
- `MRVL`
- `GOOGL`
- `AVGO`

forward-clean 可评估结果：

| horizon | n | avg | median | win_rate |
|---|---:|---:|---:|---:|
| 1d | 32 | -0.82% | -2.91% | 40.62% |
| 5d | 25 | 15.48% | 8.57% | 84.00% |
| 20d | 18 | 29.85% | 11.11% | 72.22% |
| 60d | 7 | 33.28% | 27.19% | 85.71% |
| 120d | 2 | 265.06% | 189.59% | 100.00% |

high-quality thesis 可评估结果：

| horizon | n | avg | median | win_rate |
|---|---:|---:|---:|---:|
| 1d | 4 | 0.22% | -2.47% | 25.00% |
| 5d | 4 | 11.95% | 1.37% | 75.00% |
| 20d | 3 | 27.52% | 27.14% | 66.67% |

注意：由于价格覆盖不足、样本仍小，以上只能说明管线跑通和方向性表现，不能当作稳定收益结论。

## 已验证的 ticker 边界

- `$P`：当前 2026 语境下应作为 `NYSE:P` 处理，不应自动映射为 `$PSTG`。
- `$SIVE`：应映射为 Sivers Semiconductors，价格评估建议使用 `SIVE.ST` 或明确的本地映射。

仍需人工确认的典型问题：

- `IXHL`、`ALMU`、`AIP`、`SIVEF` 等是否为真实目标 ticker，还是引用/对比/误抽取。
- 引用帖里的 ticker 是否代表 Gaetano 自己的观点。
- watchlist / basket / article teaser 是否应该降权。
- 复盘、诈骗提醒、转发提醒等是否应从 forward signal 中删除。

## 当前评级

当前 Gaetano 状态：

`B++：真实数据增强 MVP。已接入登录态 X 浏览器采集并重跑完整信号管线，但仍缺官方完整 X/Substack archive、quote/reply 关系和完整价格覆盖。`

下一步最值得做：

1. 人工复核 `manual_review_queue.csv`。
2. 修正 ticker 映射和 quote/reply 语义。
3. 补更稳定的价格源或本地价格库。
4. 若有 X API / Apify / 用户 archive，再替换当前浏览器切片数据，升级到 Serenity A 级全量版。
