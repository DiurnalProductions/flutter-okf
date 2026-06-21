---
id: flutter.vsync
type: concept
title: Vsync
description: TickerProvider supplies vsync signals so animations advance one frame at a time.
tags: [flutter, animation]
prerequisites:
  - flutter.stateful_widget
related:
  - flutter.animation_controller
  - flutter.explicit_animations
  - flutter.stateful_widget
resource: https://docs.flutter.dev/
timestamp: 2026-01-01
---

## Summary

**Vsync** (vertical sync) ticks align animation updates to display frames. `SingleTickerProviderStateMixin` / `TickerProviderStateMixin` provide `createTicker` for controllers.

## Mental model

Metronome for animations—only tick when screen refreshes. Stateful widgets mix in ticker providers; dispose controllers with the State.

## Example

```dart
class _PulseState extends State<Pulse> with SingleTickerProviderStateMixin {
  late final AnimationController _controller;

  @override
  void initState() {
    super.initState();
    _controller = AnimationController(vsync: this, duration: const Duration(seconds: 1));
  }

  @override
  void dispose() {
    _controller.dispose();
    super.dispose();
  }
}
```

## Common mistakes

- AnimationController without vsync provider.
- Multiple controllers with SingleTickerProviderStateMixin.
- Not disposing controllers.

## Related concepts

- [Animation Controller](/concepts/animation_controller.md)
- [Explicit Animations](/concepts/explicit_animations.md)
- [Stateful Widget](/concepts/stateful_widget.md)

