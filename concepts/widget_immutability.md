---
id: flutter.widget_immutability
type: concept
title: Widget Immutability
description: Widgets are immutable configuration objects; mutating them breaks reconciliation and Flutter's rendering contract.
tags: [flutter, widgets, immutability]
prerequisites:
  - flutter.declarative_rendering_model
related:
  - flutter.stateful_widget
  - flutter.rebuild_behavior
  - flutter.widget_identity
resource: https://docs.flutter.dev/
timestamp: 2026-01-01
---

## Summary

Every `Widget` is **immutable** after construction. Fields are `final`; mutable state lives in `State`, stores, or models—not in widget instances. Immutability makes rebuilds cheap and comparison safe.

## Mental model

A widget is a **recipe card**, not the meal. Print a new card when ingredients change; the framework keeps the kitchen (elements, render objects) and swaps recipes. Cheap rebuilds depend on this contract.

## Example

```dart
class Counter extends StatefulWidget {
  const Counter({super.key});
  @override
  State<Counter> createState() => _CounterState();
}

class _CounterState extends State<Counter> {
  int _count = 0;

  @override
  Widget build(BuildContext context) {
    return Text('$_count');
  }
}
```

## Common mistakes

- Adding non-final fields to Widget and mutating them.
- Storing mutable collections on StatelessWidget.
- Expecting the same widget instance to persist across rebuilds.

## Related concepts

- [Stateful Widget](/concepts/stateful_widget.md)
- [Rebuild Behavior](/concepts/rebuild_behavior.md)
- [Widget Identity](/concepts/widget_identity.md)

