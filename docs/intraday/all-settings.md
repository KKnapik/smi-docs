# Zone Detection Settings at a Glance

This page brings together only the **Intraday zone-detection settings** from **v2.10.6 SMI — Smart Money Indicator — Intraday**.

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
| [Min. Leg-Out Body Size (% of Range)](zone-detection/erc-body-threshold.md) | `70%` | **LEG-OUT** | Requires the Leg-Out body to occupy enough of its complete range. | Requires a more body-dominant Leg-Out, so fewer departures qualify. |
| [Max. Base Body Size (% of Range)](zone-detection/base-body-range-max.md) | `50%` | **BASE** | Requires every Base body to occupy strictly less than half of its own complete range. | Allows more body-dominant Base candles, so more formations may qualify. |
| [Min. Leg-Out Range (ATR ×)](zone-detection/erc-range-atr-multiplier.md) | `1.20` | **LEG-OUT** | Requires the complete Leg-Out range to be large enough compared with recent movement. | Requires a larger Leg-Out, so fewer departures qualify. |
| [Avg. Price Range Period (Bars)](zone-detection/atr-lookback-period.md) | `50` | **LEG-OUT reference** | Sets how many candles build the average movement reference used by the Leg-Out range test. | Produces a slower, smoother reference that reacts less to the newest candles. |
| [Max. Base Candles](zone-detection/max-base-candles.md) | `4` | **BASE** | Sets the backward scan available for Base candles and the preceding Leg-In. With the current scan behavior, `4` allows up to **three actual Base candles** before the Leg-In must appear. | Allows a longer pause before departure. |
| [Min. Leg-In Body Size (% of Range)](zone-detection/leg-in-body-range-min.md) | `50%` | **LEG-IN** | Requires the Leg-In body to occupy strictly more than half of its own complete range. This is the only Leg-In size qualifier. | Rejects more wick-heavy Leg-In candles. |

!!! tip "How to tune detection"
    Change one setting at a time and compare the same chart section. Start with the Leg-Out checks, then Base, then Leg-In.

## Debug a detected zone

Use the [RAW Data Table debugging guide](raw-data-table.md) to verify the stored Leg-In, Base, and Leg-Out measurements of the nearest active Demand and Supply zones.
