---
id: flutter.native_bridges
type: concept
title: Native Bridges
description: Native bridges expose device capabilities (camera, sensors, storage) to Flutter via plugins.
tags: [flutter, platform, native]
prerequisites:
  - flutter.platform_channels
related:
  - flutter.plugin_architecture
  - flutter.platform_channels
  - flutter.widget_composition
resource: https://docs.flutter.dev/
timestamp: 2026-01-01
---

## Summary

**Native bridges** implement platform APIs behind Dart facades. Federated plugins split per-platform implementations while sharing a common interface.

## Mental model

Flutter paints UI; native does what OS requires. Widget composition stays declarative; imperative work runs on platform threads with async results.

## Example

```dart
final picker = ImagePicker();
final file = await picker.pickImage(source: ImageSource.gallery);
if (file != null) {
  setState(() => _image = File(file.path));
}
```

## Common mistakes

- Assuming synchronous native calls.
- Not handling missing permissions.
- Embedding platform views without understanding performance.

## Related concepts

- [Plugin Architecture](/concepts/plugin_architecture.md)
- [Platform Channels](/concepts/platform_channels.md)
- [Widget Composition](/concepts/widget_composition.md)

