---
id: flutter.platform_rendering_constraints
type: concept
title: Platform Rendering Constraints
description: Embedding Flutter and platform views imposes hybrid composition and sizing constraints.
tags: [flutter, platform, rendering]
prerequisites:
  - flutter.render_tree
  - flutter.platform_channels
related:
  - flutter.render_tree
  - flutter.platform_channels
  - flutter.compositing_phase
resource: https://docs.flutter.dev/
timestamp: 2026-01-01
---

## Summary

**Platform views** (AndroidView, UiKitView, texture layers) integrate native UI into Flutter's render tree with **platform-specific compositing constraints** and performance tradeoffs.

## Mental model

Picture-in-picture: Flutter layout allocates a hole; native view fills it. Render tree + platform channel timing affect jank; not all widgets are Skia-painted.

## Example

```dart
AndroidView(
  viewType: 'map_view',
  layoutDirection: TextDirection.ltr,
  creationParams: const {'zoom': 12},
  creationParamsCodec: const StandardMessageCodec(),
)
```

## Common mistakes

- Many platform views in one scroll list.
- Ignoring Hybrid Composition vs Virtual Display docs.
- Assuming BoxConstraints behave identically on embedded views.

## Related concepts

- [Render Tree](/concepts/render_tree.md)
- [Platform Channels](/concepts/platform_channels.md)
- [Compositing Phase](/concepts/compositing_phase.md)

