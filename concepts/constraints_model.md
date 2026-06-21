---
id: flutter.constraints_model
type: concept
title: Constraints Model
description: Layout is driven by constraints passed parent-to-child; children report sizes back up the render tree.
tags: [flutter, layout, constraints]
prerequisites:
  - flutter.render_tree
related:
  - flutter.box_constraints
  - flutter.layout_passes
  - flutter.flex_layout
resource: https://docs.flutter.dev/
timestamp: 2026-01-01
---

## Summary

The **constraints model** is Flutter's core layout rule: parents pass `BoxConstraints` down, children choose a size within them and report up. Widgets do not pick arbitrary screen positions.

## Mental model

Constraints are **negotiation envelopes**: min/max width and height. 'Tight' constraints force an exact size; 'loose' allow flexibility. Layout passes are explicit—not magic CSS.

## Example

```dart
Center(
  child: Container(
    width: 200,
    height: 100,
    color: Colors.teal,
  ),
)
```

## Common mistakes

- Assuming parent gives unbounded constraints in scrollables.
- Ignoring overflow errors instead of fixing constraint conflicts.
- Setting size on child without understanding parent constraints.

## Related concepts

- [Box Constraints](/concepts/box_constraints.md)
- [Layout Passes](/concepts/layout_passes.md)
- [Flex Layout](/concepts/flex_layout.md)

