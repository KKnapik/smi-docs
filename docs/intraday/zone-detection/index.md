# Zone Detection Overview

This section explains the detection settings as they appear to a trader on the chart. It does not require knowledge of Pine Script.

When a formation looks valid but no zone appears, follow the illustrated [Zone Detection Debugging Workflow](debugging-workflow.md). It maps the `R`, `B`, and `B%C` labels to every detector decision in the exact order used by Intraday.

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

The Leg-In brings price into the future zone area. Its body must dominate its own candle range, but it is not compared with the size of the Base candles.

### 2. Price pauses

One or more compact candles form the Base. These candles represent a temporary balance before price leaves the area. By default, every Base candle's complete range must be no larger than the Leg-Out range; this comparison can be disabled with [Require Base Range ≤ Leg-Out Range](base-range-vs-legout-range.md).

### 3. Price departs

A strong bullish or bearish Leg-Out confirms that price left the base with enough force. The indicator then draws a Demand or Supply zone around the base.

On LTF, strength alone is not sufficient. The Leg-Out must also leave the complete Base zone cleanly. If its opposite wick reaches or passes the Base distal boundary, the candidate is rejected because the departure candle has already traversed the full imbalance. See the [LTF Leg-Out Engulf Rule](leg-out-engulf-rule.md).

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
| Min. Leg-Out Body Size (% of Range) | **LEG-OUT** | `70%` | Qualifies the body shape of the departure. It does not qualify Base or Leg-In candles. |
| Max. Base Body Size (% of Range) | **BASE** | `50%` | Requires every Base candle body to occupy strictly less than half of that candle's own range. |
| Require Base Range ≤ Leg-Out Range | **BASE** | **On** | Controls whether every Base candle's complete range must fit within the Leg-Out range. |
| Min. Leg-Out Range (ATR ×) | **LEG-OUT** | `1.20` | Checks whether the departure is large enough compared with recent movement. |
| Avg. Price Range Period (Bars) | **LEG-OUT** | `50` | Sets how many bars are used for the recent-movement reference behind the Leg-Out range requirement. |
| Max. Base Candles | **BASE** | `4` | Controls how long the pause may last. With the current behavior, the default accepts up to three actual base candles before the Leg-In must be found. |
| Min. Leg-In Body Size (% of Range) | **LEG-IN** | `50%` | Requires the Leg-In body to occupy strictly more than half of its range. It is the only Leg-In size qualifier. |

Every Base candle is checked independently against its own shape. At the defaults, each one must satisfy `Base Body ÷ Base Range < 50%` and, because the range checkbox is on, `Base Range ≤ Leg-Out Range`. Turning the checkbox off removes only the second condition. Base body size is never compared with Leg-Out body size.
