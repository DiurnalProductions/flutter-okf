---
id: flutter.implicit_animations
type: concept
title: Implicit Animations
description: Implicit animation widgets animate when configuration changes without a manual controller.
tags: [flutter, animation, reactive]
prerequisites:
  - flutter.reactive_updates
related:
  - flutter.explicit_animations
  - flutter.reactive_updates
  - flutter.tween_system
resource: https://docs.flutter.dev/
timestamp: 2026-01-01
---

## Summary

**Implicit animations** (`AnimatedContainer`, `AnimatedOpacity`, `AnimatedSwitcher`) tween when properties change—reactive updates drive animation automatically.

## Mental model

Set target state; widget animates the delta. Great when state drives rebuilds and transitions are simple. Less control than explicit controllers.

## Example

```dart
AnimatedContainer(
  duration: const Duration(milliseconds: 200),
  width: expanded ? 200 : 100,
  color: expanded ? Colors.blue : Colors.grey,
)
```

## Common mistakes

- Very long durations on large subtrees.
- Using implicit widgets inside thousands of list items.
- Expecting staggered complex choreography without explicit control.

## Related concepts

- [Explicit Animations](/concepts/explicit_animations.md)
- [Reactive Updates](/concepts/reactive_updates.md)
- [Tween System](/concepts/tween_system.md)

