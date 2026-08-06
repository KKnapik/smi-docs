# Intraday Indicator

The SMI Intraday indicator looks for price areas where a clear departure suggests that buying or selling pressure was stronger than the opposing side. It then evaluates whether those areas remain relevant when price returns.

**Current chart name:** `v2.10.6 SMI — Smart Money Indicator — Intraday`

## Main areas

1. **Zone detection** — finds the approach, pause, and departure that form a zone.
2. **Zone boundaries** — marks the price area where the pause occurred.
3. **Zone lifecycle** — tracks whether the zone is fresh, tested, consumed, or broken.
4. **LTF qualifiers** — reports Formation, Leg-In, Base, Leg-Out, Originality, Flip, and LoL facts without deriving HTF state.
5. **Local context** — displays local trend and visual risk-to-reward information.
6. **Diagnostics** — exposes RAW zone measurements and optional candle metrics for chart-level verification.

The Intraday indicator does not request or reconstruct higher-timeframe zones. Swing owns HTF Trend and HTF Location; the platform owns HTF-to-LTF Coverage, final grading, and setup notifications.

The initial documentation focuses on the input parameters that directly influence zone detection.

## Quick access

- [Zone Detection Settings at a Glance](all-settings.md) — all six Intraday detection inputs on one page, with their defaults, scope, and practical effect.
- [LTF Leg-Out Engulf Rule](zone-detection/leg-out-engulf-rule.md) — the non-configurable clean-departure rule that rejects a Leg-Out wick traversing the complete Base zone.
- [RAW Data Table — Zone Debugging Guide](raw-data-table.md) — identify the selected zone and verify its Leg-In, Base, and Leg-Out measurements.
- [Candle Metrics Debug](candle-metrics-debug.md) — read the compact `R`, `B`, and `B%C` labels on recent candles.
