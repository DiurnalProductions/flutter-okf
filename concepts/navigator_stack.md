---
id: flutter.navigator_stack
type: concept
title: Navigator Stack
description: Navigator manages a stack of Route objects; push and pop change the visible screen.
tags: [flutter, navigation]
prerequisites:
  - flutter.widget_composition
related:
  - flutter.routes
  - flutter.navigation_lifecycle
  - flutter.named_vs_dynamic_navigation
resource: https://docs.flutter.dev/
timestamp: 2026-01-01
---

## Summary

The **Navigator** holds a **stack** of routes. `push` adds, `pop` removes. Only the top route is typically visible (modals/overlays complicate).

## Mental model

A stack of playing cards—top card is current screen. Composition builds route widgets; Navigator handles transitions and history.

## Example

```dart
Navigator.of(context).push(
  MaterialPageRoute(builder: (_) => const DetailsPage()),
);
```

## Common mistakes

- Multiple Navigators without keys (wrong navigator).
- Popping the last route unexpectedly.
- Deep linking without named routes structure.

## Related concepts

- [Routes](/concepts/routes.md)
- [Navigation Lifecycle](/concepts/navigation_lifecycle.md)
- [Named Vs Dynamic Navigation](/concepts/named_vs_dynamic_navigation.md)

