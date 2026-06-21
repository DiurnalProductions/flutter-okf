---
id: flutter.list_view
type: concept
title: List View
description: ListView builds scrollable linear lists, lazily when using builder constructors.
tags: [flutter, lists, scroll]
prerequisites:
  - flutter.layout_passes
  - flutter.reactive_updates
related:
  - flutter.lazy_rendering
  - flutter.slivers
  - flutter.viewport_management
resource: https://docs.flutter.dev/
timestamp: 2026-01-01
---

## Summary

**ListView** scrolls children along one axis. Prefer `ListView.builder` for long lists—**lazy rendering** creates children only near the viewport.

## Mental model

A window sliding over a long shelf. Only items in view (+ cache) exist as elements. State drives which items rebuild; layout passes position children in the scrollable.

## Example

```dart
ListView.builder(
  itemCount: products.length,
  itemBuilder: (context, index) {
    final p = products[index];
    return ListTile(title: Text(p.name), subtitle: Text(p.price));
  },
)
```

## Common mistakes

- ListView(children: thousand widgets) — builds all at once.
- Missing itemExtent when items are fixed height (perf).
- No keys when list items reorder.

## Related concepts

- [Lazy Rendering](/concepts/lazy_rendering.md)
- [Slivers](/concepts/slivers.md)
- [Viewport Management](/concepts/viewport_management.md)

