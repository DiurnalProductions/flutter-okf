---
id: flutter.rendering_performance
type: concept
title: Rendering Performance
description: Performance tuning targets rebuild scope, layout frequency, paint damage, and layer count.
tags: [flutter, performance]
prerequisites:
  - flutter.compositing_phase
  - flutter.rebuild_behavior
related:
  - flutter.rebuild_behavior
  - flutter.lazy_rendering
  - flutter.slivers
resource: https://docs.flutter.dev/
timestamp: 2026-01-01
---

## Summary

**Rendering performance** balances cheap rebuilds against unnecessary layout, paint, and compositing. Profile with DevTools timeline and repaint rainbow.

## Mental model

Optimize the **explicit pipeline**: narrow state, const widgets, repaint boundaries, slivers for scroll lists, avoid intrinsic/layout thrash. Rebuilds are usually not the first bottleneck.

## Example

```dart
const Header(); // Skips rebuild work when parent rebuilds

ListView.builder(
  itemCount: 1000,
  itemBuilder: (_, i) => ListTile(title: Text('Item $i')),
);
```

## Common mistakes

- Premature micro-optimization before profiling.
- Saving state in widgets to avoid provider.
- Building thousands of children in Column instead of lazy lists.

## Related concepts

- [Rebuild Behavior](/concepts/rebuild_behavior.md)
- [Lazy Rendering](/concepts/lazy_rendering.md)
- [Slivers](/concepts/slivers.md)

