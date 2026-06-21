---
id: flutter.build_system
type: concept
title: Build System
description: Flutter's build system schedules dirty elements on the UI thread and reconciles widgets into the element tree.
tags: [flutter, build, framework]
prerequisites:
  - flutter.build_lifecycle
related:
  - flutter.build_phase
  - flutter.element_tree
  - flutter.reactive_updates
resource: https://docs.flutter.dev/
timestamp: 2026-01-01
---

## Summary

The **build system** covers dirty tracking, build traversal, and widget-to-element reconciliation. Changes enqueue `Element.rebuild`, coalesced per frame via `WidgetsBinding.drawFrame`.

## Mental model

A per-frame todo list of stale descriptions. `BuildOwner` tracks dirty elements; `BuildScope` roots dependency resolution for `InheritedWidget`. Updates are single-threaded on the UI isolate.

## Example

```dart
void _onTick() {
  setState(() => a++);
  setState(() => b++);
  // Batched into one drawFrame
}
```

## Common mistakes

- Calling setState after dispose.
- Root setState forcing unnecessary global rebuilds.
- Manual markNeedsBuild without framework contracts.

## Related concepts

- [Build Phase](/concepts/build_phase.md)
- [Element Tree](/concepts/element_tree.md)
- [Reactive Updates](/concepts/reactive_updates.md)

