---
id: flutter.inherited_theming
type: concept
title: Inherited Theming
description: Theme and CupertinoTheme propagate design values through inherited widgets.
tags: [flutter, theming, inherited]
prerequisites:
  - flutter.theme_data
related:
  - flutter.theme_data
  - flutter.material_vs_cupertino
  - flutter.design_tokens
resource: https://docs.flutter.dev/
timestamp: 2026-01-01
---

## Summary

**Inherited theming** (`Theme`, `CupertinoTheme`) pushes tokens down the tree. `context.watch`/`Theme.of` rebuild when theme changes—same mechanics as other inherited models.

## Mental model

Ambient design atmosphere: descendants breathe the same colors and typography without prop drilling every TextStyle.

## Example

```dart
final theme = Theme.of(context);
Text('Headline', style: theme.textTheme.headlineSmall);
```

## Common mistakes

- Theme.of without caring about rebuild scope.
- Mixing Material and Cupertino themes inconsistently.
- Bypassing theme for one-off colors everywhere.

## Related concepts

- [Theme Data](/concepts/theme_data.md)
- [Material Vs Cupertino](/concepts/material_vs_cupertino.md)
- [Design Tokens](/concepts/design_tokens.md)

