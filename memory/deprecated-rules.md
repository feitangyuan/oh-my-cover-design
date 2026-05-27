# Deprecated Rules

Use this file for patterns that repeatedly fail or create risk.

## Deprecated Template

```text
## Deprecated: [rule or pattern]

Reason:
- [failure]

Replacement:
[better rule]

Evidence:
- [observation]
```

## Initial Guardrails

- Avoid asking the image model to render long Chinese titles.
- Avoid abstract main visuals such as "AI efficiency" without a concrete object.
- Avoid layouts where face, product, and title all compete for first attention.
