# RAW Data Table — Zone Debugging Guide

The RAW Data Table helps you verify the candle measurements behind the **nearest active Demand zone below price** and the **nearest active Supply zone above price**.

It answers a focused question:

> What body, range, and comparison values were stored for the Leg-In, Base, and Leg-Out of the zone currently selected by the dashboard?

Enable it with **Visual Settings → Show RAW Data Table**. The table appears in the top-right corner.

## Terms used in this guide

- **Body** — the distance between a candle's open and close.
- **Range** — the complete distance from low to high, including wicks.
- **Leg-In** — the candle that approaches the Base.
- **Base** — the compact pause between approach and departure.
- **Leg-Out** — the expansion candle that confirms the departure.
- **ATR — Average True Range** — the indicator's reference for typical recent movement.
- **D** — Demand; **S** — Supply.
- **Active zone** — a zone that still exists and has not yet been removed by a price test.
- **Proximal line** — the edge of a zone that returning price is expected to reach first.
- **LoL — Level on top of Level** — two nearby same-side zones treated as one related setup.

## First: know which zone the table is showing

The table is not a zone selector. On the latest chart bar it automatically shows:

- the active Demand zone with the closest proximal line below current price;
- the active Supply zone with the closest proximal line above current price.

Pending, broken, mitigated, and rejected zones are not selectable in this table. When an active LoL pair exists, the LoL side represents the setup and its ordinary partner is skipped.

!!! important "Scrolling does not select a historical zone"
    Moving the chart left or placing the cursor over another box does not change the table. The selection is always based on the latest bar. Use **Bar Replay** to move the chart's latest bar back to the moment you want to inspect.

## What every field means

### Reference rows

| Field | Meaning |
| --- | --- |
| Pure ATR | The current average movement reference calculated from `Avg. Price Range Period (Bars)`. |
| Min. Range (ATR*Mult) | The current minimum complete Leg-Out range: **Pure ATR × Min. Leg-Out Range (ATR ×)**. |

These two values belong to the **current latest bar**, not necessarily to the historical bar where the displayed zone formed.

!!! warning "Use the formation-time reference for an old zone"
    The percentage ratios stored in the zone do not change, but ATR changes over time. Compare an old Leg-Out range with the `Min. Range` recorded when that Leg-Out was the latest replay bar—not with today's value.

### Demand and Supply rows

| Row | BODY | RANGE | OPEN | RATIO (%) |
| --- | --- | --- | --- | --- |
| D/S: Leg-In | Leg-In body | Complete Leg-In range | Leg-In open price | Leg-In body ÷ Leg-In range |
| D/S: Leg-Out | Leg-Out body | Complete Leg-Out range | Leg-Out open price | Leg-Out body ÷ Leg-Out range |
| D/S: Base Max | Largest Base body | Largest complete range among the Base candles | Open of the Base candle with the largest body | Largest Base body ÷ Leg-Out body |

`OPEN` helps you match a row to a candle on the chart. It is not a pass/fail threshold.

If no active zone is available on one side of price, that side's body and range values appear as zero and its open values are unavailable.

!!! note "Base Max can summarize two different Base candles"
    `Base Max BODY` is the largest Base body, while `Base Max RANGE` is the largest complete range found anywhere in the Base. They do not have to come from the same candle. `Base Max OPEN` belongs to the candle with the largest body.

Do not divide `Base Max BODY` by `Base Max RANGE`: that can accidentally combine measurements from two different candles. The Base row's displayed ratio correctly compares the largest Base body with the Leg-Out body.

## The five checks you can verify

Use the Demand rows for a Demand zone or the Supply rows for a Supply zone.

| Formation part | Read or calculate | Compare with the setting | Pass rule |
| --- | --- | --- | --- |
| **LEG-OUT** | Leg-Out `RATIO (%)` | Min. Leg-Out Body Size (% of Range) | Ratio is equal to or above the minimum. |
| **LEG-OUT** | Leg-Out `RANGE` | Min. Range (ATR*Mult) | Range is equal to or above the minimum. |
| **BASE** | Base Max `RATIO (%)` | Max. Base Body Size (% of Leg-Out) | Ratio is equal to or below the maximum. |
| **LEG-IN** | Leg-In `RATIO (%)` | Min. Leg-In Body Size (% of Range) | Ratio is equal to or above the minimum. |
| **LEG-IN vs BASE** | Leg-In `BODY` ÷ Base Max `BODY` | Min. Leg-In Body Size (× Largest Base Body) | Result is equal to or above the minimum. |

The table does not show the Base candle count. Count the Base candles on the chart and check them against `Max. Base Candles`. With the current scan behavior, the default value `4` allows up to three actual Base candles before the Leg-In must appear.

## Worked example

Assume these settings and table values:

| Item | Value |
| --- | ---: |
| Pure ATR | `10.00` |
| Min. Leg-Out Range (ATR ×) | `0.70` |
| Min. Range (ATR*Mult) | `7.00` |
| Leg-Out BODY / RANGE | `8.00 / 10.00` |
| Base Max BODY | `5.00` |
| Leg-In BODY / RANGE | `9.00 / 12.00` |

Now verify the formation:

| Check | Calculation | Threshold | Result |
| --- | ---: | ---: | --- |
| Leg-Out body share | `8 ÷ 10 = 80%` | minimum `40%` | **PASS** |
| Leg-Out range | `10.00` | minimum `7.00` | **PASS** |
| Base vs Leg-Out | `5 ÷ 8 = 62.5%` | maximum `70%` | **PASS** |
| Leg-In body share | `9 ÷ 12 = 75%` | minimum `50%` | **PASS** |
| Leg-In vs largest Base body | `9 ÷ 5 = 1.80×` | minimum `1.50×` | **PASS** |

All five measurable candle checks pass. You must still confirm the Base count and the correct Leg-In → Base → Leg-Out sequence on the chart.

## Best workflow for an existing zone

1. Decide whether you are debugging Demand (`D`) or Supply (`S`).
2. Confirm that the target is the nearest active zone on that side of price. Compare its formation and quality fields with the bottom-right dashboard.
3. Use the `OPEN` values to match the Leg-In, Leg-Out, and largest-body Base candle.
4. Check the two Leg-Out rules: body share and minimum range.
5. Check Base Max ratio against the maximum Base-to-Leg-Out setting.
6. Check the Leg-In body share, then calculate Leg-In BODY ÷ Base Max BODY.
7. Count the Base candles directly on the chart.
8. Change only one input if you want to test why the result changes.

## Best workflow for a missing or rejected zone

The RAW table stores measurements only for zones that were created and remain eligible for selection. It cannot directly show a rejected candidate.

Use this workflow instead:

1. Start **Bar Replay** before the suspected formation.
2. Advance until the Leg-Out candle is the replay endpoint. Record `Pure ATR` and `Min. Range (ATR*Mult)` at that moment.
3. Record the Leg-In, Base, and Leg-Out OHLC values from the chart or Data Window.
4. Calculate body as the distance from open to close and range as the distance from low to high.
5. Apply the five checks above and count the Base candles.
6. Advance one bar and check whether the zone appears and becomes the nearest active zone in the RAW table.

Bar Replay matters because `Pure ATR` and `Min. Range (ATR*Mult)` are live reference values. Recording them while the Leg-Out is the replay endpoint gives you the historical range threshold for that candle; today's latest-bar value does not.

## What the RAW table cannot prove

- It cannot select any arbitrary box by clicking it.
- It cannot display a zone that was rejected before creation.
- It does not show broken or already mitigated zones.
- It does not show the number of Base candles.
- Its summarized Base values cannot prove the body-to-range shape of every individual Base candle.
- It does not explain LoL context rejection, Flip classification, HTF coverage, or trade-grade points.
- Current `Pure ATR` does not prove the ATR value used when an old zone formed; use Bar Replay for that.

For the complete detection-input reference, open [Zone Detection Settings at a Glance](all-settings.md).
