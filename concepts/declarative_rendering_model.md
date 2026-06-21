---
id: flutter.declarative_rendering_model
type: concept
title: Declarative Rendering Model
description: Flutter describes UI as immutable widget configurations reconciled into pixels through an explicit multi-phase pipeline.
tags: [flutter, rendering, declarative]
prerequisites: []
related:
  - flutter.widget_tree
  - flutter.widget_immutability
  - flutter.build_phase
resource: https://docs.flutter.dev/
timestamp: 2026-01-01
---

## Summary

Flutter uses a **declarative** rendering model: you describe what the UI should look like for the current state, and the framework reconciles changes into pixels. You never mutate live UI nodes; you rebuild widget descriptions and let the engine diff them.

## Mental model

Think of UI as a pure function: `UI = f(state)`. Each state change re-runs `f` via `build`, producing a new widget tree. The framework compares descriptions and applies minimal updates to elements and render objects—never imperative locate-and-mutate.

## Example

```dart
class Greeting extends StatelessWidget {
  const Greeting({super.key, required this.name});
  final String name;

  @override
  Widget build(BuildContext context) {
    return Text('Hello, $name');
  }
}
```

## Common mistakes

- Treating build as one-time initialization instead of a repeatable pure function.
- Performing side effects (network, controllers) inside build.
- Assuming every change repaints the entire screen without reconciliation.

## Related concepts

- [Widget Tree](/concepts/widget_tree.md)
- [Widget Immutability](/concepts/widget_immutability.md)
- [Build Phase](/concepts/build_phase.md)

