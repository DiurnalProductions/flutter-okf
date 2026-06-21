---
id: flutter.grid_view
type: concept
title: Grid View
description: GridView arranges children in a two-dimensional scrollable grid, lazily with builders.
tags: [flutter, lists, grid]
prerequisites:
  - flutter.list_view
related:
  - flutter.list_view
  - flutter.lazy_rendering
  - flutter.slivers
resource: https://docs.flutter.dev/
timestamp: 2026-01-01
---

## Summary

**GridView** extends list scrolling to two dimensions via `SliverGridDelegate` (`count`, `maxCrossAxisExtent`). `GridView.builder` lazy-builds cells like ListView.

## Mental model

Same lazy window as ListView, but cells tile in rows and columns. Cross-axis count comes from constraints and delegate math.

## Example

```dart
GridView.builder(
  gridDelegate: const SliverGridDelegateWithFixedCrossAxisCount(
    crossAxisCount: 2,
    mainAxisSpacing: 8,
    crossAxisSpacing: 8,
  ),
  itemCount: items.length,
  itemBuilder: (_, i) => ItemCard(item: items[i]),
)
```

## Common mistakes

- GridView with huge child list instead of builder.
- Wrong aspect ratio causing layout overflow.
- Nested scrollables without primary/shrinkWrap care.

## Related concepts

- [List View](/concepts/list_view.md)
- [Lazy Rendering](/concepts/lazy_rendering.md)
- [Slivers](/concepts/slivers.md)

