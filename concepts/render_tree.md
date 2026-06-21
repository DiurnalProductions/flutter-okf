---
id: flutter.render_tree
type: concept
title: Render Tree
description: The render tree contains RenderObject nodes responsible for layout constraints, painting, and compositing.
tags: [flutter, rendering, layout]
prerequisites:
  - flutter.element_tree
related:
  - flutter.constraints_model
  - flutter.layout_phase
  - flutter.paint_phase
resource: https://docs.flutter.dev/
timestamp: 2026-01-01
---

## Summary

The **render tree** holds `RenderObject` nodes that layout, paint, and composite—the closest structure to pixels. Widgets delegate layout and paint to render objects via elements.

## Mental model

Render objects are the **physical stage**: size, position, paint, layer boundaries. Layout travels down constraints and up sizes; paint records display lists.

## Example

```dart
Container(
  width: 100,
  height: 100,
  color: Colors.blue,
)
```

## Common mistakes

- Expecting setState alone to relayout without a layout pass.
- Using RenderObject APIs from widget code without lifecycle ownership.
- Assuming every widget rebuild repaints everything.

## Related concepts

- [Constraints Model](/concepts/constraints_model.md)
- [Layout Phase](/concepts/layout_phase.md)
- [Paint Phase](/concepts/paint_phase.md)

