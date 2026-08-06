# Base Range vs Leg-Out Range

**Introduced:** `v2.3.0`

**Configurable:** No. This is a mandatory native LTF Base qualification rule.

## Rule

Every Base candle is checked independently using its complete High-to-Low range:

```text
Base Range ≤ Leg-Out Range
```

A Base candle equal in range to the Leg-Out is accepted. If any Base candle is larger than the Leg-Out, the complete zone candidate is rejected.

## Interaction with the other Base rules

Passing this range rule is not sufficient on its own. From v2.10.6, every Base candle must simultaneously satisfy:

```text
Base Body ÷ Base Range < configured maximum
Base Range ≤ Leg-Out Range
```

The body/range rule uses a chart setting. The range comparison is fixed and has no input. `Base Body ÷ Leg-Out Body` is no longer evaluated.

## Scope

Version 2.3.0 introduced this rule for native LTF zones created by the Intraday indicator. Version 2.10.6 removed the redundant Base-body-versus-Leg-Out-body condition. Intraday no longer performs internal HTF reconstruction; Swing LTF Confirmation remains separate until synchronized from the Intraday changelog.
