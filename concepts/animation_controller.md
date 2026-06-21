---
id: flutter.animation_controller
type: concept
title: Animation Controller
description: AnimationController drives explicit animations with duration, value, and status listeners.
tags: [flutter, animation]
prerequisites:
  - flutter.vsync
related:
  - flutter.tween_system
  - flutter.explicit_animations
  - flutter.vsync
resource: https://docs.flutter.dev/
timestamp: 2026-01-01
---

## Summary

An **AnimationController** is a `Animation<double>` source you advance with `forward`, `reverse`, or `repeat`. It requires vsync and must be disposed.

## Mental model

A remote control for explicit animations: scrub time, listen to status, attach tweens. Rebuilds happen via listeners or `AnimatedBuilder`.

## Example

```dart
_controller = AnimationController(
  vsync: this,
  duration: const Duration(milliseconds: 300),
);
_controller.addListener(() => setState(() {}));
```

## Common mistakes

- setState on every tick on huge subtrees without AnimatedBuilder.
- Running controllers after dispose.
- Forgetting to call forward/reverse.

## Related concepts

- [Tween System](/concepts/tween_system.md)
- [Explicit Animations](/concepts/explicit_animations.md)
- [Vsync](/concepts/vsync.md)

