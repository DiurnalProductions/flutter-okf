---
id: flutter.compositing_phase
type: concept
title: Compositing Phase
description: Compositing assembles layers and uploads them to the GPU for final scene display.
tags: [flutter, pipeline, compositing]
prerequisites:
  - flutter.paint_phase
related:
  - flutter.paint_phase
  - flutter.rendering_performance
  - flutter.stack_layout
resource: https://docs.flutter.dev/
timestamp: 2026-01-01
---

## Summary

The **compositing phase** flattens layer trees, applies transforms/opacity/clips, and composites to the screen. `CompositorContext` manages layer boundaries.

## Mental model

Photoshop layers merged for export. Explicit pipeline step after paint. Offscreen layers cost memory but enable effects and isolation.

## Example

```dart
Opacity(
  opacity: 0.5,
  child: child, // May promote a composited layer
)
```

## Common mistakes

- Opacity wrapping huge subtrees (full layer promotion).
- Ignoring checkerboard offscreen layers in devtools.
- Assuming ClipRRect is always cheap.

## Related concepts

- [Paint Phase](/concepts/paint_phase.md)
- [Rendering Performance](/concepts/rendering_performance.md)
- [Stack Layout](/concepts/stack_layout.md)

