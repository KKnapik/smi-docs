# Base Range vs Leg-Out Range

**Introduced:** `v2.3.0`

**Configurable since:** `v2.10.7`

**Setting:** `Require Base Range ≤ Leg-Out Range`

**Default:** **On**

## Rule

When the checkbox is enabled, every Base candle is checked independently using its complete High-to-Low range:

```text
Base Range ≤ Leg-Out Range
```

A Base candle equal in range to the Leg-Out is accepted. If any Base candle is larger than the Leg-Out, the complete zone candidate is rejected. When the checkbox is disabled, this range comparison is skipped; Base Body/Range qualification still applies.

## Interaction with the other Base rules

Passing this range rule is not sufficient on its own. From v2.10.6, every Base candle must simultaneously satisfy:

```text
Base Body ÷ Base Range < configured maximum
Base Range ≤ Leg-Out Range
```

Both current Base rules are trader-facing settings: Body/Range uses a percentage input, while the range comparison uses this checkbox. `Base Body ÷ Leg-Out Body` is no longer evaluated.

## Scope

Version 2.3.0 introduced this rule as mandatory for native LTF zones. Version 2.10.6 removed the redundant Base-body-versus-Leg-Out-body condition, and v2.10.7 exposed the range rule as an enabled-by-default checkbox. Intraday no longer performs internal HTF reconstruction; Swing LTF Confirmation remains separate until synchronized from the Intraday changelog.
