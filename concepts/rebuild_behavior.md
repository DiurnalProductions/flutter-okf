---
id: flutter.rebuild_behavior
type: concept
title: Rebuild Behavior
description: Rebuilds recreate widget descriptions for dirty subtrees; reconciliation limits work to changed branches.
tags: [flutter, rendering, performance]
prerequisites:
  - flutter.build_lifecycle
  - flutter.widget_immutability
related:
  - flutter.set_state
  - flutter.build_phase
  - flutter.rendering_performance
resource: https://docs.flutter.dev/
timestamp: 2026-01-01
---

## Summary

A **rebuild** re-invokes `build` for a dirty subtree. Rebuilds are normal and cheap at description level. Only marked elements rebuild; rebuild ≠ relayout ≠ repaint.

## Mental model

Rebuild is **cheap description refresh**, not expensive redraw. State drives rebuilds; the framework diffs configurations. Performance issues come from rebuilding too much or heavy work in `build`.

## Example

```dart
void _increment() {
  setState(() => _count++);
}
```

## Common mistakes

- Splitting widgets solely to prevent rebuilds without profiling.
- Assuming const children never participate in parent rebuild logic incorrectly.
- Confusing rebuild scope with repaint scope.

## Related concepts

- [Set State](/concepts/set_state.md)
- [Build Phase](/concepts/build_phase.md)
- [Rendering Performance](/concepts/rendering_performance.md)

