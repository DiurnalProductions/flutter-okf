---
id: flutter.reactive_updates
type: concept
title: Reactive Updates
description: UI updates reactively when state or inherited dependencies change, triggering targeted rebuilds.
tags: [flutter, state, reactive]
prerequisites:
  - flutter.rebuild_behavior
  - flutter.set_state
related:
  - flutter.set_state
  - flutter.provider_concept
  - flutter.implicit_animations
resource: https://docs.flutter.dev/
timestamp: 2026-01-01
---

## Summary

**Reactive updates** connect data changes to rebuilds: `setState`, inherited notifications, `Listenable`, streams. State drives rebuilds; the pipeline then runs build → layout → paint as needed.

## Mental model

Think pub/sub on the element tree. Subscribe via `dependOn`, `ListenableBuilder`, or state management packages. Reactivity is **granular** when dependencies are narrow.

## Example

```dart
ListenableBuilder(
  listenable: controller,
  builder: (context, child) => Text('${controller.value}'),
);
```

## Common mistakes

- Rebuilding entire app on every keystroke.
- Mixing imperative setState with global streams without boundaries.
- Assuming reactive == repaints everything.

## Related concepts

- [Set State](/concepts/set_state.md)
- [Provider Concept](/concepts/provider_concept.md)
- [Implicit Animations](/concepts/implicit_animations.md)

