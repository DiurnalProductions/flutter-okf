---
id: flutter.explicit_animations
type: concept
title: Explicit Animations
description: Explicit animations use controllers, tweens, and builders for full timing control.
tags: [flutter, animation]
prerequisites:
  - flutter.animation_controller
  - flutter.tween_system
  - flutter.rebuild_behavior
related:
  - flutter.animation_controller
  - flutter.tween_system
  - flutter.vsync
resource: https://docs.flutter.dev/
timestamp: 2026-01-01
---

## Summary

**Explicit animations** combine `AnimationController`, tweens, and `AnimatedBuilder`/`FadeTransition` for precise choreography. Rebuild behavior ties to listeners or animated widgets.

## Mental model

You own the timeline—start, pause, stagger, repeat. State drives when animations run; controller drives intermediate frames.

## Example

```dart
AnimatedBuilder(
  animation: _controller,
  builder: (context, child) {
    return Transform.scale(scale: _scale.value, child: child);
  },
  child: const Icon(Icons.star, size: 48),
);
```

## Common mistakes

- Listener + setState rebuilding entire page each frame.
- Not using child parameter of AnimatedBuilder for static parts.
- Explicit animation for every color change (use implicit).

## Related concepts

- [Animation Controller](/concepts/animation_controller.md)
- [Tween System](/concepts/tween_system.md)
- [Vsync](/concepts/vsync.md)

