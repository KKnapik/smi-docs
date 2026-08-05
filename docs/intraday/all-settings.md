# All Settings at a Glance

This is the single reference page for the settings available in **v2.0.0 SMI — Smart Money Indicator — Intraday**.

## Key terms

- **Candle body** — the distance between open and close.
- **Candle range** — the complete distance from low to high, including wicks.
- **Leg-In** — the candle that approaches the pause.
- **Base** — the compact pause between approach and departure.
- **Leg-Out** — the expansion candle that confirms the departure.
- **ATR — Average True Range** — a reference for typical recent price movement.

## Read the impact label first

- **DETECTION** — changes which Intraday zones can be created.
- **CONTEXT / GRADING** — changes market context, trend, LoL handling, or trade grading. It does not qualify the Leg-In, Base, or Leg-Out unless the row explicitly says so.
- **DISPLAY** — changes only what is visible on the chart.
- **CURRENTLY INACTIVE** — the input is visible, but changing it has no visible effect in v2.0.0.

!!! tip "A reliable way to tune the indicator"
    Change one detection setting at a time, then compare the same chart section. Display settings cannot create or reject a zone.

## Candle Detection (LTF)

These are the settings that directly determine whether a chart-timeframe formation becomes an Intraday zone.

| Setting | Default | Applies to | What it does | If increased |
| --- | ---: | --- | --- | --- |
| [Min. Leg-Out Body Size (% of Range)](zone-detection/erc-body-threshold.md) | `40%` | **DETECTION — LEG-OUT + BASE** | Requires the Leg-Out body to occupy enough of its complete candle range. It also helps prevent an expansion candle from being accepted as Base. | Requires a more body-dominant Leg-Out, but fewer earlier candles are excluded from Base by the expansion-candle test. |
| [Max. Base Body Size (% of Leg-Out)](zone-detection/base-vs-legout-ratio.md) | `70%` | **DETECTION — BASE** | Limits each Base body relative to the Leg-Out body. | Allows larger Base bodies; more formations qualify. |
| [Min. Leg-Out Range (ATR ×)](zone-detection/erc-range-atr-multiplier.md) | `0.70` | **DETECTION — LEG-OUT + BASE** | Requires the complete Leg-Out range to be large enough compared with recent movement. It also affects which candles are treated as expansion candles and excluded from Base. | Requires a larger Leg-Out, but fewer earlier candles are excluded from Base by the expansion-candle test. |
| [Avg. Price Range Period (Bars)](zone-detection/atr-lookback-period.md) | `50` | **DETECTION — LEG-OUT + BASE reference** | Sets how many candles build the average movement reference used by the Leg-Out range test. | Produces a slower, smoother reference that reacts less to the newest candles. |
| [Max. Base Candles](zone-detection/max-base-candles.md) | `4` | **DETECTION — BASE** | Sets the backward scan available for Base candles and the preceding Leg-In. With the current scan behavior, `4` allows up to **three actual Base candles** before the Leg-In must appear. | Allows a longer pause before departure. |
| [Min. Leg-In Body Size (× Largest Base Body)](zone-detection/leg-in-body-vs-base.md) | `1.50` | **DETECTION — LEG-IN, using BASE as reference** | Requires the Leg-In body to stand out from the largest Base body. | Requires a more distinct Leg-In; fewer formations qualify. |
| [Min. Leg-In Body Size (% of Range)](zone-detection/leg-in-body-range-min.md) | `50%` | **DETECTION — LEG-IN** | Requires the Leg-In body to occupy enough of its own complete range. | Rejects more wick-heavy Leg-In candles. |

## Location Curve

| Setting | Default | Impact | What it does |
| --- | ---: | --- | --- |
| Show Location Curve | `On` | **DISPLAY** | Shows or hides the High, Equilibrium, and Low bands between the nearest active Demand and Supply zones. |
| Max. Location Gap (ATR ×) | `20` | **CONTEXT / DISPLAY** | Hides the curve when the distance between its Demand and Supply anchors is unusually large compared with recent movement. Lower values hide it more often. |
| Location Curve Width (Bars) | `50` | **DISPLAY** | Sets how far the curve extends horizontally. It does not change its price levels. |

[Read the full Location Curve guide](location-curve.md).

## HTF Coverage

**HTF** means Higher Timeframe. Coverage asks whether an Intraday zone overlaps a broader Demand or Supply area.

| Setting | Default | Impact | What it does |
| --- | ---: | --- | --- |
| Show HTF Coverage | `On` | **DISPLAY** | On displays `Yes`, `No`, or `N/A` in the dashboard `Coverage` column. Off leaves the column visible but reports `N/A`. HTF coverage is still calculated for trade grading. |
| Use Custom HTF Timeframe | `Off` | **CONTEXT / GRADING** | Off uses the automatic higher timeframe. On uses the interval selected in `Custom HTF`. |
| Custom HTF | `1D` | **CONTEXT / GRADING** | Selects the higher timeframe used for coverage and HTF trend when custom mode is On. |
| Show HTF Zones (Yellow Boxes) | `Off` | **DISPLAY** | Shows or hides the calculated HTF Demand and Supply boxes. In v2.0.0 they are displayed as semi-transparent green and red boxes despite the legacy input name. |

Automatic timeframe selection uses **Daily** on chart intervals up to 8 hours, **Monthly** on a Weekly chart, and **Weekly** on other chart intervals above 8 hours.

## Visual Settings

| Setting | Default | Impact | What it does |
| --- | ---: | --- | --- |
| Show Pending Zones | `Off` | **CURRENTLY INACTIVE** | v2.0.0 activates a valid zone immediately after confirmation, so there is no visible pending phase for this toggle to reveal. |
| Show Dashboard | `On` | **DISPLAY** | Shows or hides the main zone and market-context dashboard in the bottom-right corner. |
| Show RAW Data Table | `On` | **DISPLAY / DEBUG** | Shows or hides the measurement table for the nearest active Demand and Supply zones. |
| Show Trade Grade Labels | `On` | **DISPLAY** | Shows the A, B, or C grade when a zone is first tested. It does not change the score or zone behavior. |
| Show Grade Breakdown (Debug) | `Off` | **DISPLAY / DEBUG** | Expands grade labels with the individual LoL, coverage, Leg-Out, Leg-In, Base, freshness, originality, Flip, profit-margin, and trend scores. |
| Max. Zones per Side (0 = All) | `0` | **DISPLAY** | Limits visible zones to the nearest N Demand zones below price and N Supply zones above price. `0` shows all. Hidden zones still exist in the indicator. |

[Use the RAW Data Table to debug a zone](raw-data-table.md).

## LoL Settings

**LoL — Level on top of Level** describes two nearby zones of the same type that belong to one coherent price-action sequence.

| Setting | Default | Impact | What it does |
| --- | ---: | --- | --- |
| Show LoL Labels | `On` | **DISPLAY** | Shows or hides labels identifying the LoL zone and its partner. |
| Combine overlapping LoL | `Off` | **CONTEXT / ZONE LIFECYCLE** | When On, an overlapping pair becomes one combined zone with a shared test. When Off, the proximal partner can be removed while the distal LoL remains active. Non-overlapping pairs are not combined. |
| LoL Context — single price action | `On` | **CONTEXT / LOL SELECTION** | Requires both zones to belong to one continuous price-action sequence rather than a move away and later return. |
| LoL Context — band tolerance (× pair height) | `0.25` | **CONTEXT / LOL SELECTION** | Adds a search margin around the pair when looking for unrelated same-side structure. Higher values are more lenient. |
| LoL Context — max retrace ratio | `0.70` | **CONTEXT / LOL SELECTION** | Limits how deeply price may retrace between the two zones. Higher values are more lenient; `1.00` disables this retracement condition. |
| LoL Debug — rejection reason | `Off` | **DISPLAY / DEBUG** | Adds a `CTX` marker when two zones are close enough to be considered but fail the single-price-action context check. |

## ZigZag Config

ZigZag identifies confirmed swing highs and lows. It labels them as **HH** (Higher High), **HL** (Higher Low), **LH** (Lower High), or **LL** (Lower Low). Its pivots drive the trend shown in the dashboard and the trend component of trade grading. These settings do **not** create or reject Supply and Demand zones.

| Setting | Default | Impact | What it does |
| --- | ---: | --- | --- |
| Show ZigZag | `On` | **DISPLAY** | Shows or hides ZigZag lines and HH, HL, LH, and LL labels. Swing and trend calculations continue when it is Off. |
| Depth | `6` | **CONTEXT / GRADING** | Controls how much chart structure is considered when selecting swing pivots. Higher values generally ignore more minor movement. |
| Deviation | `5` | **CONTEXT / GRADING** | Controls the minimum price change needed for the ZigZag to recognize a new swing. Higher values generally require a larger move. |
| Backstep | `2` | **CONTEXT / GRADING** | Controls the minimum separation used when confirming neighboring pivots. Higher values generally reduce closely spaced pivots. |
| Repaint Levels | `On` | **DISPLAY** | On shows the developing ZigZag leg, which can move until the pivot is confirmed. Off draws only confirmed legs. It does not make an unconfirmed pivot final. |

!!! warning "ZigZag settings also change trend context"
    `Depth`, `Deviation`, and `Backstep` are shared by the chart-timeframe and higher-timeframe trend calculations. Changing them can change dashboard trend and the trend points in a trade grade even when `Show ZigZag` is Off.

## Lines

| Setting | Default | Impact | What it does |
| --- | ---: | --- | --- |
| Line Thickness | `1` | **DISPLAY** | Changes ZigZag line width. |
| Lines Transparency | `0` | **DISPLAY** | Changes ZigZag line transparency: `0` is opaque and `100` is invisible. |
| Extend ZigZag | `Off` | **DISPLAY** | Extends the currently drawn ZigZag leg to the right. |
| Max Pivots to Show | `6` | **DISPLAY** | Limits retained ZigZag pivot lines and labels. For example, `6` is approximately three highs and three lows. It does not limit trend calculation history. |

## Labels

| Setting | Default | Impact | What it does |
| --- | ---: | --- | --- |
| Labels Transparency | `0` | **DISPLAY** | Changes HH, HL, LH, and LL label background transparency. |
| Text Color | Black | **DISPLAY** | Changes ZigZag label text color. |
| Label SIze | `3` | **DISPLAY** | Changes ZigZag label size from `1` (tiny) to `5` (huge). The capitalization shown here matches the current indicator input. |

## Colors

| Setting | Default | Impact | What it does |
| --- | --- | --- | --- |
| Bull Color | Teal | **DISPLAY** | Sets bullish ZigZag line and pivot-label color. |
| Bear Color | Red | **DISPLAY** | Sets bearish ZigZag line and pivot-label color. |
| Background Transparency | `80` | **CURRENTLY INACTIVE** | v2.0.0 does not draw the former ZigZag direction background, so changing this input has no visible effect. |
| High (Expensive) Color | Gold, 88% transparent | **DISPLAY** | Sets the upper Location Curve band color. |
| Equilibrium Color | White, 88% transparent | **DISPLAY** | Sets the middle Location Curve band color. |
| Low (Cheap) Color | Blue, 88% transparent | **DISPLAY** | Sets the lower Location Curve band color. |
| Demand Zone Color | Teal, 80% transparent | **DISPLAY** | Sets Demand zone fill color and related Demand text accents. |
| Supply Zone Color | Red, 80% transparent | **DISPLAY** | Sets Supply zone fill color and related Supply text accents. |
| LoL Zone Color | Purple, 70% transparent | **DISPLAY** | Sets LoL zone and LoL dashboard color. |
| LoL Combined Border Color | Yellow, 60% transparent | **DISPLAY** | Sets the border color of a combined overlapping LoL zone. |

## What to open next

- To understand why a specific active zone passed its candle checks, use the [RAW Data Table debugging guide](raw-data-table.md).
- To study one detection threshold visually, open the linked parameter page in the Candle Detection table.
