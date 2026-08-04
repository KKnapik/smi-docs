# ATR Lookback Period

**Default:** `50`

## Terms used on this page

- **ATR** — a measure of the market's typical candle movement.
- **Lookback period** — the number of previous candles used to calculate that typical movement.
- **ERC** — the indicator's name for a decisive expansion candle.

## What this setting controls

It controls how much recent price history the indicator uses when deciding whether a departure candle is unusually large. At the default value of `50`, the volatility reference is based on the previous 50 candles.

## If you lower the value

- The volatility reference reacts faster to recent changes.
- A sudden quiet or active period affects detection more quickly.
- The required departure size can change more sharply from bar to bar.

## If you raise the value

- The volatility reference becomes smoother and more stable.
- Short-lived volatility changes have less influence.
- The reference may adapt slowly after the market changes character.

## What traders should consider

The same numerical value represents different amounts of time on different chart intervals. Fifty candles on a 5-minute chart cover a very different trading window from fifty candles on a 1-hour chart.

## Visual for this setting

The same price sequence will show a short lookback reacting quickly and a long lookback remaining smoother, followed by the difference in the required departure size.
