# LTF Leg-Out Engulf Rule

**Introduced:** `v2.2.0`

**Configurable:** No. This is a mandatory native LTF clean-departure rule.

## Why the candidate is rejected

A valid LTF Leg-Out must leave the complete Base zone cleanly. A strong body is not sufficient when the opposite Leg-Out wick trades through the entire original Base imbalance.

The detector first builds the Base boundaries from Base candles only. It then compares the closed Leg-Out extreme with the original Base distal.

## Demand

```text
Leg-Out Low ≤ lowest Base wick
```

When this condition is true, the bullish departure has reached or passed the Demand distal boundary and the complete LTF candidate is rejected.

## Supply

```text
Leg-Out High ≥ highest Base wick
```

When this condition is true, the bearish departure has reached or passed the Supply distal boundary and the complete LTF candidate is rejected.

Equality is rejected on both sides. Reaching the distal means the Leg-Out has traversed the complete original Base zone.

## Partial wick overlap

A partial wick entry that does not reach the Base distal does not trigger this rule. The candidate must still pass every other Leg-In, Base, Leg-Out, validation, and lifecycle condition.

## Scope

Version 2.2.0 introduced this rule for native LTF zones created by the Intraday indicator. From v2.10.0, Intraday no longer performs any internal HTF reconstruction. Swing LTF Confirmation must be synchronized separately before it can be expected to reject the same candidate.
