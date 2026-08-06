# Min. Leg-In Body Size (% of Range)

**Default:** `50%`

!!! info "Applies to: LEG-IN only"
    **LEG-IN — direct effect:** this setting decides whether the approach candle is directional enough.

    **BASE and LEG-OUT — no effect:** neither component is qualified by this setting.

## Terms used on this page

- **Leg-In** — the move that approaches the future zone area.
- **Body** — the solid part between the candle's open and close.
- **Wicks** — the thin parts above and below the body.
- **Candle range** — the complete distance from low to high.

## What this setting controls

It controls how directional the **Leg-In** candle must look. At the default value of `50`, the body must occupy **more than** half of the candle's complete range. A candle at exactly `50%` is rejected.

## If you lower the value

- Leg-In candles with larger wicks can qualify.
- More formations may appear.
- Indecisive approaches are accepted more easily.

## If you raise the value

- The Leg-In must have a cleaner, larger body.
- Fewer formations qualify.
- Wick-heavy approaches are filtered out.

## Only Leg-In size qualifier

Since v2.1.0, the Leg-In body is not compared with the largest Base body. This body-to-range test is the only Leg-In size qualifier.

## Visual for this setting

![Minimum Leg-In Body Size as Percentage of Range: accepted and rejected Leg-In shape](../../assets/diagrams/leg-in-body-range-min.svg)

Both examples have the same complete range. Only the **Leg-In** body proportion changes; the Base and Leg-Out are not checked by this parameter.
