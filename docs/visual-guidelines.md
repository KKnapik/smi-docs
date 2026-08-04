# Visual Guidelines

Every parameter graphic should answer one trader question: **what changes on the chart when I change this setting?** All unrelated conditions should remain constant.

Every page and graphic must identify the affected formation component before explaining the setting:

- **LEG-OUT**
- **BASE**
- **LEG-IN**
- **DISPLAY / CONTEXT**

When a parameter has both a direct and indirect effect, both must be stated explicitly. For example, ERC settings directly qualify the Leg-Out and indirectly determine whether a candle is excluded from the Base.

## Standard format

- SVG output embedded directly in Markdown.
- Use a wide chart format close to 16:9. A taller SVG is allowed for grouped settings when it materially improves label readability.
- Dark chart background consistent with TradingView.
- Exact candle counts and visually correct proportions.
- Use green and red for PASS/FAIL status labels or panel borders, never to change candle direction between comparison panels.
- Plain-language labels placed directly next to the relevant candle or zone.
- A short practical takeaway beneath the visual.
- No decorative candles that could be mistaken for part of a formation.
- No Pine Script expressions, variable names, or source-code fragments.
- Include accessible SVG title/description text and meaningful Markdown alt text.

## Comparison principle

When explaining a threshold, change exactly one tested property at a time. Keep candle direction, color, unaffected ratios, surrounding formation, and all secondary conditions constant. If body heights are compared, align them to a shared measurement baseline and draw the requirement as a vertical bracket rather than a floating price level.

PASS and FAIL may be illustrated either by changing the documented input against one fixed formation or by changing only the tested candle property against one fixed input. Never change both at once. Each unfamiliar term must be explained in the page legend before it appears in the graphic.

## Validation

Visual examples must use verified chart values and must match the indicator's trading logic. Screenshots may provide market context, but explanatory lines and zone boundaries must be based on confirmed data rather than visual estimation.
