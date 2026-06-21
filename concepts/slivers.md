---
id: flutter.slivers
type: concept
title: Slivers
description: Slivers are scroll-aware layout units composed in CustomScrollView for advanced scrolling.
tags: [flutter, lists, slivers]
prerequisites:
  - flutter.list_view
  - flutter.viewport_management
related:
  - flutter.viewport_management
  - flutter.lazy_rendering
  - flutter.list_view
resource: https://docs.flutter.dev/
timestamp: 2026-01-01
---

## Summary

**Slivers** (`SliverList`, `SliverGrid`, `SliverAppBar`) participate in a shared **viewport** with lazy layout. Use for collapsing headers, sticky groups, and performant complex scroll views.

## Mental model

Slivers are **scroll pipeline citizens**: they receive sliver constraints, produce geometry incrementally. Essential for scroll performance beyond simple ListView.

## Example

```dart
CustomScrollView(
  slivers: [
    const SliverAppBar(title: Text('Shop'), floating: true),
    SliverList.builder(
      itemCount: items.length,
      itemBuilder: (_, i) => ListTile(title: Text(items[i])),
    ),
  ],
)
```

## Common mistakes

- Mixing shrinkWrap scrollables inside slivers without need.
- One giant SliverChildListDelegate for thousands of items.
- Ignoring cacheExtent tuning.

## Related concepts

- [Viewport Management](/concepts/viewport_management.md)
- [Lazy Rendering](/concepts/lazy_rendering.md)
- [List View](/concepts/list_view.md)

