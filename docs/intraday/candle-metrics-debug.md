# Candle Metrics Debug

The optional Candle Metrics overlay annotates recent chart candles with the same measurements used when checking candle shape.

Enable it with **Debug → Show Candle Metrics**. The default window contains the latest `20` candles and can be configured from `1` to `100` with **Candle Metrics Bars**.

## Label format

```text
R: 161.25
B: 142.75
B%C: 88.5%
```

- **R** — complete candle range: `High − Low`.
- **B** — absolute candle body: `|Close − Open|`.
- **B%C** — body cover: `Body ÷ Range × 100`.

For this example, `142.75 ÷ 161.25 = 88.5%`.

## How to use it

- Compare a potential Leg-Out `B%C` with **Min. Leg-Out Body Size (% of Range)**.
- Compare every potential Base candle `B%C` with **Max. Base Body Size (% of Range)**.
- Compare a potential Leg-In `B%C` with **Min. Leg-In Body Size (% of Range)**.
- Use `R` to verify that every Base range is no larger than the Leg-Out range.

The label is diagnostic only. It does not create, reject, resize, or grade a zone. Hovering a label exposes that candle's complete Open, High, Low, and Close values.
