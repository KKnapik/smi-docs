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

Passing this range rule is not sufficient on its own. Every Base candle must simultaneously satisfy:

```text
Base Body ÷ Leg-Out Body ≤ configured maximum
Base Body ÷ Base Range < configured maximum
Base Range ≤ Leg-Out Range
```

The first two rules use chart settings. The third rule is fixed and has no input.

## Scope

Version 2.3.0 applies this rule only to native LTF zones created by the Intraday indicator. Internal HTF reconstruction and Swing LTF Confirmation remain unchanged until synchronized separately.
