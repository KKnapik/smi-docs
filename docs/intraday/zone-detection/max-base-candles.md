# Max. Base Candles

**Default:** `4`

!!! info "Applies to: BASE"
    **BASE — direct effect:** this setting controls how much room is available for consecutive base candles.

    **LEG-IN — position effect:** the detector must still find the Leg-In immediately before the base, which is why the current default value of `4` results in at most three visible base candles.

    **LEG-OUT — no strength effect:** this setting does not make the departure easier or harder to qualify.

## Terms used on this page

- **Base** — the compact pause between the approach and departure.
- **Leg-In** — the move into the base.
- **Leg-Out** — the move away from the base.
- **Base quality** — a separate rating that describes how compact and clear the detected base is.

## What this setting controls

It controls the amount of space available for recognizing the base and the preceding Leg-In. The current detector needs one position for the Leg-In. As a result, the default input value of `4` accepts bases containing one, two, or three actual base candles.

!!! important "Displayed value versus current behavior"
    `Max. Base Candles = 4` currently means a maximum of three base candles on the chart. A four-candle base is not completed because the detector still needs to find the Leg-In immediately before it.

## If you lower the value

- Only shorter and more compact pauses qualify.
- Fewer zones are detected.
- Extended consolidations are rejected sooner.

## If you raise the value

- Longer pauses can still become zones because more space is available before the Leg-In must be found.
- More formations qualify.
- The indicator may include broader consolidations that are less precise as trading areas.

## Detection versus quality

The number of candles accepted by detection is separate from the quality grade. With the current default, a base may contain up to three candles. Its quality still depends on how compact those candles are compared with the departure.

## Visual for this setting

![Maximum Base Candles: current accepted and rejected candle counts](../../assets/diagrams/max-base-candles.svg)

With the current detector, input value `4` leaves four scan positions for the Base and preceding Leg-In. Bases containing one, two, or three candles can qualify; a four-candle Base leaves no position for the Leg-In and is rejected.
