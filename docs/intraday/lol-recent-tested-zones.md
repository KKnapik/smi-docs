# LoL Fallback Correlation

Intraday v2.12.0 extends Level-on-Level (LoL) correlation without changing how normal zones become active or broken.

For a simple explanation of all LoL rules and settings, start with the [LoL Detection user guide](lol-detection.md).

## Why this path exists

A valid lower formation can be tested at its proximal boundary before the next stacked formation finishes. Normal lifecycle rules correctly reject or mitigate that lower zone, but the later formation may still prove that both levels belong to one LoL price-action sequence.

The LoL engine therefore has an additional fallback when no active same-side partner qualifies:

1. search recently tested zones already present in broken history;
2. search the latest same-side formation rejected by immediate validation;
3. apply the existing gap, context, and Base-overlap conditions;
4. promote the pair only when every LoL condition passes.

Active-zone LoL pairing always has priority.

## Shared-candle LoL

A directly stacked pair can share one impulse candle:

```text
Distal Leg-In -> Distal Base -> Shared candle -> Proximal Base -> Proximal Leg-Out
                                      |
                                      +-- Distal Leg-Out
                                      +-- Proximal Leg-In
```

The shared candle may be clean enough to act as the proximal Leg-In while its Body/Range remains below the stricter normal Leg-Out threshold. In that case the distal formation is not a normal zone and is not retained as a candidate.

After the proximal zone validates and no active or recent partner qualifies, the LoL engine performs one bounded historical reconstruction. The shared candle must be the exact proximal Leg-In bar and must:

- have the correct Rally/Drop direction;
- pass the configured strict Leg-In Body/Range threshold;
- miss only the normal Leg-Out Body/Range threshold;
- pass the normal Leg-Out minimum Range/ATR requirement;
- leave a valid Base without engulfing its complete imbalance.

The earlier Leg-In, every distal Base candle, distal integrity, gap, context, and Base-overlap rules remain mandatory. The reconstructed formation can exist only as part of the confirmed LoL pair; it can never become a standalone zone, Flip fact, or alert.

## Bounded reject memory

The immediate-reject fallback retains at most:

- one Demand candidate;
- one Supply candidate.

Each candidate expires after `Max. Base Candles + 2` bars or immediately when price breaches its distal boundary. It is an internal LoL fact only: it has no active box, dashboard row, alert, notification, or Flip meaning.

This fixed two-slot design prevents a growing parallel zone history.

## Normal zones remain unchanged

The feature does not relax zone validation or mitigation:

- a proximal test still rejects or mitigates the normal zone;
- the candidate does not return as a normal zone;
- `broken_zones_array` remains the Flip history source;
- a candidate becomes visible again only after a valid later zone confirms the LoL pair.

## Combine overlapping LoL

When `Combine overlapping LoL` is enabled and the two Base footprints overlap, the valid new zone absorbs the recent partner into one combined LoL box.

When it is disabled, the recent partner is restored only as the distal LoL level and the valid new zone remains its proximal partner.

In both modes the dashboard reports LoL only after correlation is confirmed.
