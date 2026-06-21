---
id: flutter.viewport_management
type: concept
title: Viewport Management
description: Scrollables manage a viewport that clips and positions sliver/list children during layout.
tags: [flutter, lists, viewport]
prerequisites:
  - flutter.layout_passes
related:
  - flutter.slivers
  - flutter.layout_passes
  - flutter.list_view
resource: https://docs.flutter.dev/
timestamp: 2026-01-01
---

## Summary

The **viewport** defines visible scroll extent, `cacheExtent`, and offset. `ScrollController` reads/writes position; layout passes place children relative to scroll offset.

## Mental model

A camera viewport panning over content. Only visible region matters for paint; cacheExtent pre-builds nearby items for smooth flings.

## Example

```dart
final controller = ScrollController();

ListView.builder(
  controller: controller,
  itemCount: 100,
  itemBuilder: (_, i) => ListTile(title: Text('$i')),
);
```

## Common mistakes

- Multiple ScrollControllers on one scrollable.
- Not disposing ScrollController.
- jumpTo in build causing layout loops.

## Related concepts

- [Slivers](/concepts/slivers.md)
- [Layout Passes](/concepts/layout_passes.md)
- [List View](/concepts/list_view.md)

