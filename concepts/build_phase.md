---
id: flutter.build_phase
type: concept
title: Build Phase
description: The build phase reconciles dirty elements and produces an updated widget-to-element tree.
tags: [flutter, pipeline, build]
prerequisites:
  - flutter.build_system
  - flutter.rebuild_behavior
related:
  - flutter.build_system
  - flutter.layout_phase
  - flutter.rebuild_behavior
resource: https://docs.flutter.dev/
timestamp: 2026-01-01
---

## Summary

During the **build phase**, `BuildOwner.buildScope` rebuilds dirty elements, running `build` methods and updating child slots. It precedes layout and paint in the frame pipeline.

## Mental model

First station on the assembly line: refresh descriptions. State drives rebuilds here; cheap widget allocation is expected. Coalesced per `drawFrame`.

## Example

```dart
WidgetsBinding.instance.addPostFrameCallback((_) {
  // Runs after build/layout/paint for this frame
});
```

## Common mistakes

- Synchronous layout reads in build before layout runs.
- Forcing rebuilds every frame without need.
- Side effects in build that mark more elements dirty recursively.

## Related concepts

- [Build System](/concepts/build_system.md)
- [Layout Phase](/concepts/layout_phase.md)
- [Rebuild Behavior](/concepts/rebuild_behavior.md)

