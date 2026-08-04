# ERC Range ATR Multiplier

**Default:** `0.70`

## Terms used on this page

- **ERC** — the indicator's name for a decisive expansion candle.
- **Candle range** — the complete distance from the candle's low to its high.
- **ATR** — a measure of how much price has typically moved over recent candles.
- **Leg-Out** — the departure candle that confirms price has left the base.

## What this setting controls

It controls how large a potential departure must be compared with recent market movement. At the default value of `0.70`, the complete candle must cover at least 70% of the current ATR reference.

This prevents an ordinary small candle from being treated as a meaningful departure simply because its body looks clean.

## If you lower the value

- Smaller departures can qualify.
- More zones may appear during quiet sessions.
- Ordinary market noise is more likely to be accepted.

## If you raise the value

- The departure must stand out more strongly from recent movement.
- Fewer zones qualify.
- Valid zones formed during low-volatility conditions may be missed.

## Important interaction

This setting checks candle size. **ERC Body % Threshold** separately checks whether the candle is directional rather than dominated by wicks. A valid expansion candle must pass both checks.

## Visual for this setting

The candle's full range will be placed next to the recent ATR reference. One example will clear the selected requirement and another will fall short.
