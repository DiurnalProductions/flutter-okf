---
id: flutter.stateless_widget
type: concept
title: Stateless Widget
description: StatelessWidget describes UI that depends only on constructor configuration and inherited dependencies.
tags: [flutter, widgets]
prerequisites:
  - flutter.widget_tree
  - flutter.widget_immutability
related:
  - flutter.stateful_widget
  - flutter.widget_composition
  - flutter.widget_immutability
resource: https://docs.flutter.dev/
timestamp: 2026-01-01
---

## Summary

`StatelessWidget` has no mutable `State`. Its `build` is a pure function of configuration and `BuildContext` dependencies (theme, media query, inherited widgets).

## Mental model

Stateless widgets are **snapshots**: given the same inputs and context, they describe the same subtree. Prefer them when local mutable state is unnecessary—composition over inheritance.

## Example

```dart
class StatusBadge extends StatelessWidget {
  const StatusBadge({super.key, required this.label});
  final String label;

  @override
  Widget build(BuildContext context) {
    return Chip(label: Text(label));
  }
}
```

## Common mistakes

- Using StatefulWidget when no local state exists.
- Caching mutable data in static or top-level variables tied to UI.
- Omitting const constructors when all fields are compile-time constant.

## Related concepts

- [Stateful Widget](/concepts/stateful_widget.md)
- [Widget Composition](/concepts/widget_composition.md)
- [Widget Immutability](/concepts/widget_immutability.md)

