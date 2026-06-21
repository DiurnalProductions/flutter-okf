---
id: flutter.lazy_rendering
type: concept
title: Lazy Rendering
description: Lazy builders instantiate children on demand as they approach the viewport.
tags: [flutter, lists, performance]
prerequisites:
  - flutter.list_view
related:
  - flutter.list_view
  - flutter.slivers
  - flutter.rendering_performance
resource: https://docs.flutter.dev/
timestamp: 2026-01-01
---

## Summary

**Lazy rendering** defers building off-screen children. `ListView.builder`, `GridView.builder`, and sliver builders only call `itemBuilder` for visible indices (plus cache).

## Mental model

Demand-driven UI: don't cook every dish for a buffet line—prepare plates as guests arrive. Keeps rebuild and layout scope small for long lists.

## Example

```dart
ListView.builder(
  itemCount: 10000,
  itemBuilder: (context, index) => Text('Row $index'),
);
```

## Common mistakes

- Using Column for hundreds of rows.
- Heavy work in itemBuilder without memoization.
- Assuming builder keeps state for off-screen cells (it doesn't).

## Related concepts

- [List View](/concepts/list_view.md)
- [Slivers](/concepts/slivers.md)
- [Rendering Performance](/concepts/rendering_performance.md)

