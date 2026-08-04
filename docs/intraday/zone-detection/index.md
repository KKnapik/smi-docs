# Zone Detection Overview

The Intraday detector evaluates price action in the following order:

```text
Leg-Out → Base → Leg-In
```

The implementation scans backward from a confirmed leg-out candle, collects consecutive valid base candles, and then qualifies the preceding leg-in candle.

## Main detection stages

### 1. Leg-Out qualification

The leg-out must pass both ERC conditions:

```text
Body ≥ Range × ERC Body % Threshold
AND
Range ≥ ATR × ERC Range ATR Multiplier
```

### 2. Base qualification

Each base candle must be small relative to the leg-out and must not itself qualify as an ERC candle.

### 3. Leg-In qualification

The leg-in must be larger than the biggest base candle and must contain a sufficiently large body relative to its complete range.

### 4. Zone creation

A bullish leg-out produces a Demand candidate. A bearish leg-out produces a Supply candidate. The direction of the leg-in determines the final formation name, such as RBR, DBR, RBD, or DBD.

## Current Intraday defaults

| Parameter | Default |
| --- | ---: |
| ERC Body % Threshold | `0.40` |
| Base vs Leg-Out Ratio | `0.70` |
| ERC Range ATR Multiplier | `0.70` |
| ATR Lookback Period | `50` |
| Max Base Candles | `4` |
| Leg-In Body vs Base | `1.50` |
| Leg-In Body/Range Minimum | `0.50` |
| Flip Clean-Check Skip Bars | `0` |

