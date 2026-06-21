---
id: flutter.layout_phase
type: concept
title: Layout Phase
description: The layout phase computes sizes and positions for render objects marked needsLayout.
tags: [flutter, pipeline, layout]
prerequisites:
  - flutter.build_phase
  - flutter.layout_passes
related:
  - flutter.layout_passes
  - flutter.paint_phase
  - flutter.build_phase
resource: https://docs.flutter.dev/
timestamp: 2026-01-01
---

## Summary

The **layout phase** calls `PipelineOwner.flushLayout`, processing render objects needing layout. Constraints propagate; sizes bubble. Explicit and separate from build.

## Mental model

After blueprints update, **surveyors measure**. Only subtrees with layout dirtiness pay cost. Parent relayout can invalidate children.

## Example

```dart
@override
void performLayout() {
  child!.layout(constraints.loosen(), parentUsesSize: true);
  size = child!.size;
}
```

## Common mistakes

- Reading size in build via context.size incorrectly.
- GlobalKey layout queries every frame.
- Assuming setState always triggers layout.

## Related concepts

- [Layout Passes](/concepts/layout_passes.md)
- [Paint Phase](/concepts/paint_phase.md)
- [Build Phase](/concepts/build_phase.md)

