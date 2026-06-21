---
id: flutter.routes
type: concept
title: Routes
description: A Route represents a screen with entrance/exit transitions and overlay entries.
tags: [flutter, navigation]
prerequisites:
  - flutter.navigator_stack
related:
  - flutter.named_vs_dynamic_navigation
  - flutter.navigator_stack
  - flutter.navigation_lifecycle
resource: https://docs.flutter.dev/
timestamp: 2026-01-01
---

## Summary

**Routes** (`MaterialPageRoute`, `CupertinoPageRoute`, custom `PageRoute`) produce pages and drive transition animations. `RouteSettings` carries name and arguments.

## Mental model

Each route is a **stage set**: widget subtree plus transition choreography. Navigator stack is a list of these stages.

## Example

```dart
final route = MaterialPageRoute<void>(
  settings: const RouteSettings(name: '/details', arguments: 42),
  builder: (context) => const DetailsPage(),
);
```

## Common mistakes

- Passing non-serializable objects without deep link plan.
- Forgetting to set RouteSettings.name for analytics.
- Huge widget trees constructed before push animation.

## Related concepts

- [Named Vs Dynamic Navigation](/concepts/named_vs_dynamic_navigation.md)
- [Navigator Stack](/concepts/navigator_stack.md)
- [Navigation Lifecycle](/concepts/navigation_lifecycle.md)

