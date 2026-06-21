---
id: flutter.plugin_architecture
type: concept
title: Plugin Architecture
description: Plugins package Dart API, platform interface, and per-OS implementations for reuse.
tags: [flutter, platform, plugins]
prerequisites:
  - flutter.native_bridges
related:
  - flutter.native_bridges
  - flutter.platform_channels
  - flutter.dependency_injection
resource: https://docs.flutter.dev/
timestamp: 2026-01-01
---

## Summary

**Plugin architecture**: app-facing Dart package, `plugin_platform_interface`, and federated `android`/`ios`/`web` implementations registered via pubspec.

## Mental model

USB-C hub: one Dart port, many native cables. Keeps widget layer clean; native bridges stay behind stable APIs.

## Example

```dart
// pubspec.yaml
// dependencies:
//   my_plugin: ^1.0.0

final result = await MyPlugin.instance.getVersion();
```

## Common mistakes

- Forking plugins instead of federated implementation.
- Breaking platform interface semver.
- Plugin API that returns widgets (anti-pattern).

## Related concepts

- [Native Bridges](/concepts/native_bridges.md)
- [Platform Channels](/concepts/platform_channels.md)
- [Dependency Injection](/concepts/dependency_injection.md)

