# ERC Body % Threshold

**Default:** `0.40`

This parameter defines the minimum share of a candle's full range that must be occupied by its body before the candle can pass the body-strength condition for ERC classification.

```text
Body % = abs(Close - Open) / (High - Low)
```

A lower value accepts more candles. A higher value requires cleaner candles with larger bodies and smaller combined wicks.

The parameter affects both sides of detection:

- an ERC candle may become a leg-out candidate;
- an ERC candle cannot be accepted as a base candle.

!!! note
    Passing the body-percentage condition is not enough. The candle must also pass the ATR-based range condition.

## Planned visual

The same candle will be compared against two threshold values. Its measured body-to-range ratio will pass the lower threshold and fail the higher threshold.

