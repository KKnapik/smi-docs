# ERC Range ATR Multiplier

**Default:** `0.70`

This parameter defines the minimum full candle range required for ERC classification relative to ATR.

```text
High - Low ≥ ATR × ERC Range ATR Multiplier
```

A lower multiplier accepts smaller expansion candles. A higher multiplier requires a more significant volatility expansion.

## Planned visual

The candle's High-to-Low range will be compared with a measured ATR reference line and the required ATR multiple.

