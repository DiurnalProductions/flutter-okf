---
id: flutter.theme_data
type: concept
title: Theme Data
description: ThemeData bundles colors, typography, and component themes for Material apps.
tags: [flutter, theming]
prerequisites:
  - flutter.inherited_widget_model
related:
  - flutter.inherited_theming
  - flutter.design_tokens
  - flutter.inherited_widget_model
resource: https://docs.flutter.dev/
timestamp: 2026-01-01
---

## Summary

**ThemeData** defines `colorScheme`, `textTheme`, and component themes. `Theme` inherited widget exposes it; `Theme.of(context)` registers rebuild dependencies.

## Mental model

Design system in a suitcase—widgets read tokens via context. State/theme changes drive reactive rebuilds of dependents only.

## Example

```dart
MaterialApp(
  theme: ThemeData(
    colorScheme: ColorScheme.fromSeed(seedColor: Colors.indigo),
    useMaterial3: true,
  ),
  home: const HomePage(),
);
```

## Common mistakes

- Hard-coded Colors in every widget.
- Not using colorScheme roles (primary, surface).
- Huge ThemeData copy in every MaterialApp rebuild.

## Related concepts

- [Inherited Theming](/concepts/inherited_theming.md)
- [Design Tokens](/concepts/design_tokens.md)
- [Inherited Widget Model](/concepts/inherited_widget_model.md)

