# Max Base Candles

**Default:** `4`

This parameter sets the maximum number of consecutive valid base candles that the detector may collect between the leg-in and leg-out.

A lower value restricts detection to compact formations. A higher value allows longer consolidations to qualify.

The number of detected base candles is separate from the base quality grade. For example, a three-candle base may receive a stronger quality classification than a four-candle base while both remain detectable with the default setting.

## Planned visual

Accepted formations with one through four base candles will be compared with a rejected formation containing five base candles.

