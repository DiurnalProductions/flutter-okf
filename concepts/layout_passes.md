---
id: flutter.layout_passes
type: concept
title: Layout Passes
description: Layout runs in passes: constraints down, sizes up, possibly relayout when intrinsics or flex require it.
tags: [flutter, layout, pipeline]
prerequisites:
  - flutter.constraints_model
  - flutter.flex_layout
related:
  - flutter.constraints_model
  - flutter.layout_phase
  - flutter.viewport_management
resource: https://docs.flutter.dev/
timestamp: 2026-01-01
---

## Summary

**Layout passes** walk the render tree: parent sets child constraints, children return sizes, parent positions children. `markNeedsLayout` schedules relayout separate from rebuild.

## Mental model

Measure rooms before placing furniture. Build describes structure; **layout assigns geometry**. Changing only paint may skip layout; changing constraints triggers layout.

## Example

```dart
// After setState changes only color, layout may be skipped.
// Changing child count or flex usually triggers layout.
```

## Common mistakes

- Calling renderObject.layout from widgets.
- Assuming every rebuild relayouts.
- Debug painting without checking layout bounds.

## Related concepts

- [Constraints Model](/concepts/constraints_model.md)
- [Layout Phase](/concepts/layout_phase.md)
- [Viewport Management](/concepts/viewport_management.md)

