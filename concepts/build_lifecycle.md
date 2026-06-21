---
id: flutter.build_lifecycle
type: concept
title: Build Method Lifecycle
description: The build method produces updated widget descriptions whenever Flutter marks a subtree dirty.
tags: [flutter, build, lifecycle]
prerequisites:
  - flutter.widget_tree
related:
  - flutter.build_system
  - flutter.rebuild_behavior
  - flutter.reactive_updates
resource: https://docs.flutter.dev/
timestamp: 2026-01-01
---

## Summary

`build` describes children when the framework marks an element dirty. It must be **pure, fast, and side-effect free** for external systems.

## Mental model

Treat `build` like a **spreadsheet formula**: inputs change, output recalculates. Avoid I/O and imperative UI inside `build`. It may run many times per second during animations.

## Example

```dart
@override
Widget build(BuildContext context) {
  final theme = Theme.of(context);
  return Text('Title', style: theme.textTheme.titleLarge);
}
```

## Common mistakes

- Initializing controllers or futures inside build.
- Allocating heavy objects every build without caching.
- Putting business logic in build instead of presentation mapping.

## Related concepts

- [Build System](/concepts/build_system.md)
- [Rebuild Behavior](/concepts/rebuild_behavior.md)
- [Reactive Updates](/concepts/reactive_updates.md)

