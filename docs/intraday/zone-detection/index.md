# Zone Detection Overview

This section explains the detection settings as they appear to a trader on the chart. It does not require knowledge of Pine Script.

## Terms used in this section

- **Candle body** — the distance between the open and close.
- **Wicks** — the parts of the candle above and below its body.
- **Candle range** — the complete distance from the candle's low to its high.
- **ERC** — the indicator's name for a decisive expansion candle. It must have a meaningful body and be large enough compared with recent market movement.
- **Leg-In** — the move that approaches the area where price pauses.
- **Base** — the short pause or balance area between the approach and departure.
- **Leg-Out** — the strong move away from the base. A zone is not confirmed until this departure appears.
- **Demand zone** — an area created by a strong bullish departure.
- **Supply zone** — an area created by a strong bearish departure.
- **HTF** — a higher timeframe used to provide broader market context.

## How a zone forms on the chart

### 1. Price approaches

The Leg-In brings price into the future zone area. It should be clearly larger than the candles that will form the base, but it does not need to be as strong as the final departure.

### 2. Price pauses

One or more compact candles form the Base. These candles represent a temporary balance before price leaves the area.

### 3. Price departs

A strong bullish or bearish Leg-Out confirms that price left the base with enough force. The indicator then draws a Demand or Supply zone around the base.

!!! note "Why a zone may appear after the move has started"
    The indicator must wait for the departure candle to close before it can confirm the formation. This prevents an unfinished candle from being treated as a completed departure.

## Formation names

- **RBR — Rally-Base-Rally:** bullish approach, pause, bullish departure.
- **DBR — Drop-Base-Rally:** bearish approach, pause, bullish departure.
- **RBD — Rally-Base-Drop:** bullish approach, pause, bearish departure.
- **DBD — Drop-Base-Drop:** bearish approach, pause, bearish departure.

## Current Intraday defaults

| Parameter | Default | What the trader controls |
| --- | ---: | --- |
| ERC Body % Threshold | `0.40` | How much of the departure candle should be solid body rather than wicks. |
| Base vs Leg-Out Ratio | `0.70` | How small base candles must be compared with the departure. |
| ERC Range ATR Multiplier | `0.70` | How large the departure must be compared with recent movement. |
| ATR Lookback Period | `50` | How much price history is used to judge recent movement. |
| Max Base Candles | `4` | How long the pause may last. With the current detection behavior, the default accepts up to three actual base candles. |
| Leg-In Body vs Base | `1.50` | How distinct the approach must be from the base. |
| Leg-In Body/Range Minimum | `0.50` | How directional the approach candle must look. |
| Flip Clean-Check Skip Bars | `0` | How the indicator checks clean price action when classifying a Flip Zone. |
