# Higher-Timeframe Detection

The Intraday indicator maintains a separate, more permissive parameter set for detecting higher-timeframe Supply and Demand zones used by HTF coverage analysis.

## Current defaults

| Parameter | Default |
| --- | ---: |
| HTF ERC Body % | `0.30` |
| HTF Base/Leg-Out Ratio | `0.85` |
| HTF ERC ATR Multiplier | `0.50` |
| HTF Max Base Candles | `6` |
| HTF Leg-In Body vs Base | `1.30` |
| HTF Leg-In Body/Range Minimum | `0.40` |

These values make HTF detection more tolerant than chart-timeframe detection. The resulting zones provide context and coverage information; they are not the primary Intraday zones.

## Planned visual

The final page will compare the same formation under chart-timeframe and HTF thresholds.

