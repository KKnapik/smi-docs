# Higher-Timeframe Detection

## Terms used on this page

- **HTF — Higher Timeframe** — a broader chart interval used to provide market context.
- **Coverage** — confirmation that an Intraday zone overlaps a relevant higher-timeframe zone.
- **ERC** — the indicator's name for a decisive expansion candle.
- **Base** — the compact pause before price departs.
- **Leg-In** — the approach into the base.
- **Leg-Out** — the departure away from the base.

## What this group controls

The Intraday indicator also searches for Supply and Demand zones on a broader timeframe. These zones do not replace the primary Intraday zones. They provide context and help show whether an Intraday setup is supported by a larger market structure.

The default HTF settings are deliberately more permissive because higher-timeframe candles often contain more internal price movement.

## Current defaults

| Parameter | Default | Trader-facing meaning |
| --- | ---: | --- |
| HTF ERC Body % | `0.30` | The departure body must cover at least 30% of the full HTF candle. Raising it requires cleaner departures. |
| HTF Base/Leg-Out Ratio | `0.85` | Base bodies may be relatively large compared with the HTF departure. Lowering it requires tighter bases. |
| HTF ERC ATR Multiplier | `0.50` | The departure must reach at least half of the recent HTF volatility reference. Raising it requires a larger expansion. |
| HTF Max Base Candles | `6` | Under the current behavior, this leaves room for up to five actual HTF base candles and the preceding Leg-In. Lowering it restricts detection to shorter pauses. |
| HTF Leg-In Body vs Base | `1.30` | The approach must be at least 1.3 times the largest base body. Raising it requires a more distinct approach. |
| HTF Leg-In Body/Range Minimum | `0.40` | At least 40% of the approach candle must be body. Raising it filters out more wick-heavy approaches. |

## What traders will notice

- More permissive HTF settings produce more potential coverage zones.
- Stricter settings produce fewer but visually cleaner HTF zones.
- Changing HTF detection may alter coverage and zone grading without changing the boundaries of the primary Intraday zone.

## Visual for this group

The same formation will be evaluated once with Intraday thresholds and once with HTF thresholds. The comparison will show why a formation may qualify as higher-timeframe context even when it would not pass the stricter Intraday settings.
