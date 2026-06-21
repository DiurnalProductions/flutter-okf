---
id: flutter.platform_channels
type: concept
title: Platform Channels
description: Platform channels send asynchronous messages between Dart and host-platform code.
tags: [flutter, platform]
prerequisites:
  - flutter.widget_composition
related:
  - flutter.native_bridges
  - flutter.plugin_architecture
  - flutter.platform_rendering_constraints
resource: https://docs.flutter.dev/
timestamp: 2026-01-01
---

## Summary

**Platform channels** (`MethodChannel`, `EventChannel`, `BasicMessageChannel`) marshal messages across the Dart/native boundary. Results are async; errors must be handled.

## Mental model

Bilingual phone line: Flutter speaks Dart, host speaks Kotlin/Swift/C++. Plugins wrap channels with typed APIs—keep widgets free of raw channel strings.

## Example

```dart
const channel = MethodChannel('app/battery');

Future<int> fetchLevel() async {
  final level = await channel.invokeMethod<int>('getBatteryLevel');
  return level ?? -1;
}
```

## Common mistakes

- Blocking UI isolate on platform work.
- Channel names colliding between plugins.
- Calling channels directly from build.

## Related concepts

- [Native Bridges](/concepts/native_bridges.md)
- [Plugin Architecture](/concepts/plugin_architecture.md)
- [Platform Rendering Constraints](/concepts/platform_rendering_constraints.md)

