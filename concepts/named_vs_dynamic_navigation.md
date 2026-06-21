---
id: flutter.named_vs_dynamic_navigation
type: concept
title: Named vs Dynamic Navigation
description: Named routes centralize path-to-widget maps; dynamic routes build widgets at navigation time.
tags: [flutter, navigation]
prerequisites:
  - flutter.routes
related:
  - flutter.routes
  - flutter.navigator_stack
  - flutter.navigation_lifecycle
resource: https://docs.flutter.dev/
timestamp: 2026-01-01
---

## Summary

**Named routes** (`routes` table, `onGenerateRoute`, `go_router`) aid deep links and consistency. **Dynamic** `MaterialPageRoute(builder:)` suits one-off flows with local closures.

## Mental model

Named = phone book of destinations. Dynamic = ad-hoc taxi ride. Modern apps often use declarative routers (go_router) atop the same Navigator stack model.

## Example

```dart
MaterialApp(
  routes: {
    '/': (_) => const HomePage(),
    '/settings': (_) => const SettingsPage(),
  },
);
```

## Common mistakes

- Giant routes map without feature modularization.
- Named routes without argument typing.
- Mixing imperative push with declarative router state.

## Related concepts

- [Routes](/concepts/routes.md)
- [Navigator Stack](/concepts/navigator_stack.md)
- [Navigation Lifecycle](/concepts/navigation_lifecycle.md)

