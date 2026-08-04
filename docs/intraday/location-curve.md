# Location Curve

The Location Curve is a context and presentation feature. It does not create Supply or Demand zones.

The indicator selects the nearest active Demand zone below price and the nearest active Supply zone above price. The range between their boundaries is divided into three equal areas:

- **High (Expensive)**
- **Equilibrium**
- **Low (Cheap)**

## Inputs

| Parameter | Default | Purpose |
| --- | ---: | --- |
| Show Location Curve | `true` | Shows or hides the curve. |
| Max Location Gap (ATR x) | `20` | Hides the curve when the zone-to-zone range is too large relative to ATR. |
| Location Curve Width | `50` | Controls the horizontal display width in bars. |

## Planned visual

A Supply zone and Demand zone will anchor the three colored location bands, with the ATR gap filter and width control shown separately.

