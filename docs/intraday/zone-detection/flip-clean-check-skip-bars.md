# Flip Clean-Check Skip Bars

**Default:** `0`

!!! info "Applies to: FLIP ZONE classification only"
    This setting does not qualify the **LEG-IN**, **BASE**, or **LEG-OUT** of an ordinary Supply or Demand formation. It is used only after zones already exist and the indicator evaluates a possible Flip Zone.

## Terms used on this page

- **Broken zone** — a former Supply or Demand zone that price has moved through.
- **Flip Zone** — a new zone that forms after price breaks an opposite zone and begins using that former area from the other side.
- **Clean price action** — movement that does not repeatedly trade through the area being evaluated.
- **Skip bars** — the most recent candles intentionally excluded from the cleanliness check.

## What this setting controls

This setting does not control the creation of ordinary Supply or Demand zones. It only affects the later decision to label a setup as a Flip Zone.

At the default value of `0`, every candle in the relevant inspection window is considered. Increasing the setting tells the indicator to ignore a selected number of candles nearest the new formation.

## If you lower the value

- More nearby price action is checked.
- Flip classification becomes stricter.
- A recent touch or overlap is more likely to invalidate a clean flip.

## If you raise the value

- More recent candles are ignored during the check.
- Flip classification becomes more permissive.
- Price interaction close to the new formation has less influence.

## Visual for this setting

A broken zone and a new opposite zone will be connected by a highlighted inspection window. A second panel will show which candles disappear from that window when skip bars are added.
