---
id: flutter.stateful_widget
type: concept
title: Stateful Widget
description: StatefulWidget pairs immutable configuration with a long-lived State object that holds mutable data.
tags: [flutter, widgets, state]
prerequisites:
  - flutter.stateless_widget
related:
  - flutter.set_state
  - flutter.stateless_widget
  - flutter.widget_lifecycle_async
resource: https://docs.flutter.dev/
timestamp: 2026-01-01
---

## Summary

`StatefulWidget` is immutable configuration; **`State` is mutable** and survives rebuilds. `createState` runs once; `State` owns controllers, animations, and local UI state.

## Mental model

The widget is the envelope; **State is the letter inside** that can be rewritten. `setState` schedules rebuilds after mutating state fields.

## Example

```dart
class Expandable extends StatefulWidget {
  const Expandable({super.key, required this.child});
  final Widget child;

  @override
  State<Expandable> createState() => _ExpandableState();
}

class _ExpandableState extends State<Expandable> {
  bool _open = false;

  @override
  Widget build(BuildContext context) {
    return Column(
      children: [
        IconButton(
          onPressed: () => setState(() => _open = !_open),
          icon: Icon(_open ? Icons.expand_less : Icons.expand_more),
        ),
        if (_open) widget.child,
      ],
    );
  }
}
```

## Common mistakes

- Putting mutable fields on the StatefulWidget class.
- Creating State in build instead of createState.
- Forgetting to call setState after mutating state.

## Related concepts

- [Set State](/concepts/set_state.md)
- [Stateless Widget](/concepts/stateless_widget.md)
- [Widget Lifecycle Async](/concepts/widget_lifecycle_async.md)

