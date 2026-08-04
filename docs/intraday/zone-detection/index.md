# Zone Detection Overview

This section explains the detection settings as they appear to a trader on the chart. It does not require knowledge of Pine Script.

## Terms used in this section

- **Candle body** — the distance between the open and close.
- **Wicks** — the parts of the candle above and below its body.
- **Candle range** — the complete distance from the candle's low to its high.
- **ERC — Extended Range Candle** — a decisive expansion candle. It must have a meaningful body and be large enough compared with recent market movement.
- **ATR — Average True Range** — a measure of how much price has typically moved over recent candles.
- **Leg-In** — the move that approaches the area where price pauses.
- **Base** — the short pause or balance area between the approach and departure.
- **Leg-Out** — the strong move away from the base. A zone is not confirmed until this departure appears.
- **Demand zone** — an area created by a strong bullish departure.
- **Supply zone** — an area created by a strong bearish departure.
- **Flip Zone** — a zone created when price breaks an opposite zone and begins using that former area from the other side.
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

| Parameter | Applies to | Default | What the trader controls |
| --- | --- | ---: | --- |
| ERC Body % Threshold | **LEG-OUT + BASE** | `0.40` | Directly qualifies the departure. Indirectly prevents an Extended Range Candle from being used as a base candle. It does not qualify the Leg-In. |
| Base vs Leg-Out Ratio | **BASE** | `0.70` | Controls how small each base body must be compared with the Leg-Out body. |
| ERC Range ATR Multiplier | **LEG-OUT + BASE** | `0.70` | Directly checks whether the departure is large enough. Indirectly affects whether a candle can remain part of the base. It does not qualify the Leg-In. |
| ATR Lookback Period | **LEG-OUT + BASE** | `50` | Sets the recent-volatility reference used for Extended Range Candle classification. |
| Max Base Candles | **BASE** | `4` | Controls how long the pause may last. With the current behavior, the default accepts up to three actual base candles before the Leg-In must be found. |
| Leg-In Body vs Base | **LEG-IN** | `1.50` | Controls how distinct the Leg-In body must be from the largest base body. |
| Leg-In Body/Range Minimum | **LEG-IN** | `0.50` | Controls how directional the Leg-In candle must look. |
| Flip Clean-Check Skip Bars | **FLIP ZONE** | `0` | Controls the cleanliness check used only for Flip Zone classification. |
