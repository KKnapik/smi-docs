# ATR Lookback Period

**Default:** `50`

!!! info "Applies to: LEG-OUT + BASE (including HTF detection)"
    **LEG-OUT — direct effect:** the lookback creates the volatility reference used to judge departure size.

    **BASE — indirect effect:** it also influences whether a possible base candle is classified as an Extended Range Candle and therefore rejected from the base.

    **LEG-IN — no effect:** Leg-In qualification does not use ATR.

## Terms used on this page

- **ATR** — a measure of the market's typical candle movement.
- **Lookback period** — the number of previous candles used to calculate that typical movement.
- **ERC — Extended Range Candle** — a decisive expansion candle with enough body and size compared with recent movement.

## What this setting controls

It controls how much recent price history the indicator uses when deciding whether a **Leg-Out** is unusually large and whether a possible **Base** candle should instead be treated as an Extended Range Candle. At the default value of `50`, the volatility reference is based on the previous 50 candles.

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
