---
id: flutter.paint_phase
type: concept
title: Paint Phase
description: The paint phase records display lists for render objects that need repainting.
tags: [flutter, pipeline, paint]
prerequisites:
  - flutter.layout_phase
related:
  - flutter.compositing_phase
  - flutter.layout_phase
  - flutter.rendering_performance
resource: https://docs.flutter.dev/
timestamp: 2026-01-01
---

## Summary

**Paint** records drawing commands into layers/display lists. `markNeedsPaint` schedules repainting. `RepaintBoundary` isolates repaint damage.

## Mental model

Artists paint only dirty canvases. Rebuild without visual change may skip paint. **Compositing** consumes paint output.

## Example

```dart
RepaintBoundary(
  child: ExpensiveChart(data: data),
)
```

## Common mistakes

- Huge repaint boundaries everywhere (memory cost).
- Animating without repaint boundaries on heavy subtrees.
- Confusing rebuild with repaint.

## Related concepts

- [Compositing Phase](/concepts/compositing_phase.md)
- [Layout Phase](/concepts/layout_phase.md)
- [Rendering Performance](/concepts/rendering_performance.md)

