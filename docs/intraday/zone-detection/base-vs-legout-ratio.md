# Base vs Leg-Out Ratio

**Default:** `0.70`

## Terms used on this page

- **Base** — the compact pause before price departs.
- **Leg-Out** — the strong departure away from the base.
- **Body** — the solid part of a candle between its open and close.

## What this setting controls

It controls how small the candles inside the base must be when compared with the departure candle. At the default value of `0.70`, a base candle may have a body up to 70% of the Leg-Out body.

The purpose is to preserve a visible contrast between a quiet pause and a stronger departure.

## If you lower the value

- Bases must be tighter and calmer.
- Fewer formations qualify.
- The visual difference between the base and departure becomes clearer.

## If you raise the value

- Larger base candles are accepted.
- More zones may appear.
- Broad or noisy pauses can be classified as bases more easily.

## Visual for this setting

One Leg-Out will be compared with two possible base candles. The accepted base will remain below the selected size limit, while the rejected base will be too large.
