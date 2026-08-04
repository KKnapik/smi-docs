# Intraday Indicator

The SMI Intraday indicator looks for price areas where a clear departure suggests that buying or selling pressure was stronger than the opposing side. It then evaluates whether those areas remain relevant when price returns.

**Current chart name:** `v2.0.0 SMI — Smart Money Indicator — Intraday`

## Main areas

1. **Zone detection** — finds the approach, pause, and departure that form a zone.
2. **Zone boundaries** — marks the price area where the pause occurred.
3. **Zone lifecycle** — tracks whether the zone is fresh, tested, consumed, or broken.
4. **Higher-timeframe context** — checks whether the Intraday zone sits inside a broader zone.
5. **Location curve** — shows whether price is relatively expensive, balanced, or cheap between nearby zones.
6. **Zone grading** — summarizes the quality and context of a potential trading area.

The initial documentation focuses on the input parameters that directly influence zone detection.
