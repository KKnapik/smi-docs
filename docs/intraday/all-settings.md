# Zone Detection Settings at a Glance

This page brings together only the **Intraday zone-detection settings** from **v2.0.0 SMI — Smart Money Indicator — Intraday**.

## Terms used on this page

- **Candle body** — the distance between open and close.
- **Candle range** — the complete distance from low to high, including wicks.
- **Leg-In** — the candle that approaches the pause.
- **Base** — the compact pause between approach and departure.
- **Leg-Out** — the expansion candle that confirms the departure.
- **ATR — Average True Range** — a reference for typical recent price movement.

## All zone-detection settings

| Setting | Default | Applies to | What it does | If increased |
| --- | ---: | --- | --- | --- |
| [Min. Leg-Out Body Size (% of Range)](zone-detection/erc-body-threshold.md) | `40%` | **LEG-OUT + BASE** | Requires the Leg-Out body to occupy enough of its complete range. It also helps prevent an expansion candle from being accepted as Base. | Requires a more body-dominant Leg-Out, but fewer earlier candles are excluded from Base by the expansion-candle test. |
| [Max. Base Body Size (% of Leg-Out)](zone-detection/base-vs-legout-ratio.md) | `70%` | **BASE** | Limits each Base body relative to the Leg-Out body. | Allows larger Base bodies, so more formations may qualify. |
| [Min. Leg-Out Range (ATR ×)](zone-detection/erc-range-atr-multiplier.md) | `0.70` | **LEG-OUT + BASE** | Requires the complete Leg-Out range to be large enough compared with recent movement. It also affects which expansion candles are excluded from Base. | Requires a larger Leg-Out, but fewer earlier candles are excluded from Base by the expansion-candle test. |
| [Avg. Price Range Period (Bars)](zone-detection/atr-lookback-period.md) | `50` | **LEG-OUT + BASE reference** | Sets how many candles build the average movement reference used by the Leg-Out range and expansion-candle tests. | Produces a slower, smoother reference that reacts less to the newest candles. |
| [Max. Base Candles](zone-detection/max-base-candles.md) | `4` | **BASE** | Sets the backward scan available for Base candles and the preceding Leg-In. With the current scan behavior, `4` allows up to **three actual Base candles** before the Leg-In must appear. | Allows a longer pause before departure. |
| [Min. Leg-In Body Size (× Largest Base Body)](zone-detection/leg-in-body-vs-base.md) | `1.50` | **LEG-IN, using BASE as reference** | Requires the Leg-In body to stand out from the largest Base body. | Requires a more distinct Leg-In, so fewer formations may qualify. |
| [Min. Leg-In Body Size (% of Range)](zone-detection/leg-in-body-range-min.md) | `50%` | **LEG-IN** | Requires the Leg-In body to occupy enough of its own complete range. | Rejects more wick-heavy Leg-In candles. |

!!! tip "How to tune detection"
    Change one setting at a time and compare the same chart section. Start with the Leg-Out checks, then Base, then Leg-In.

## Debug a detected zone

Use the [RAW Data Table debugging guide](raw-data-table.md) to verify the stored Leg-In, Base, and Leg-Out measurements of the nearest active Demand and Supply zones.
