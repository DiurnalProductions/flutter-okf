---
id: flutter.design_tokens
type: concept
title: Design Tokens
description: Design tokens are named constants for colors, spacing, and typography used across widgets.
tags: [flutter, theming, design]
prerequisites:
  - flutter.theme_data
related:
  - flutter.theme_data
  - flutter.inherited_theming
  - flutter.widget_composition
resource: https://docs.flutter.dev/
timestamp: 2026-01-01
---

## Summary

**Design tokens** centralize visual constants—often mapped into `ThemeData` or custom `InheritedWidget` extensions. Prefer tokens over magic numbers.

## Mental model

Single source of truth for brand values. Widgets stay immutable; tokens feed `build` outputs. Works with inherited theming for dark/light modes.

## Example

```dart
abstract final class AppSpacing {
  static const double sm = 8;
  static const double md = 16;
  static const double lg = 24;
}

Padding(
  padding: const EdgeInsets.all(AppSpacing.md),
  child: child,
)
```

## Common mistakes

- Duplicating hex colors across files.
- Tokens that bypass ThemeData entirely for Material widgets.
- No dark mode token variants.

## Related concepts

- [Theme Data](/concepts/theme_data.md)
- [Inherited Theming](/concepts/inherited_theming.md)
- [Widget Composition](/concepts/widget_composition.md)

