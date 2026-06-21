---
id: flutter.tween_system
type: concept
title: Tween System
description: Tweens map controller values (0–1) to typed ranges (color, offset, rect).
tags: [flutter, animation]
prerequisites:
  - flutter.animation_controller
related:
  - flutter.animation_controller
  - flutter.explicit_animations
  - flutter.implicit_animations
resource: https://docs.flutter.dev/
timestamp: 2026-01-01
---

## Summary

**Tween<T>** defines `begin` and `end`; `animate(controller)` produces `Animation<T>`. `CurvedAnimation` applies easing curves.

## Mental model

Controller is time; **tween is meaning**. `ColorTween`, `Tween<Offset>`, and `IntTween` translate normalized progress into domain values.

## Example

```dart
final animation = CurvedAnimation(parent: _controller, curve: Curves.easeInOut);
final offsetTween = Tween<Offset>(begin: Offset.zero, end: const Offset(0, 1));
final offset = offsetTween.animate(animation);
```

## Common mistakes

- Animating without curves on UI that feels linear/robotic.
- Creating new Tween every build (attach in initState).
- Mixing implicit and explicit for the same property.

## Related concepts

- [Animation Controller](/concepts/animation_controller.md)
- [Explicit Animations](/concepts/explicit_animations.md)
- [Implicit Animations](/concepts/implicit_animations.md)

