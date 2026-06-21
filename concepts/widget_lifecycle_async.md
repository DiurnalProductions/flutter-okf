---
id: flutter.widget_lifecycle_async
type: concept
title: Widget Lifecycle Async
description: Async work must align with initState, dispose, and mounted checks in StatefulWidget.
tags: [flutter, async, lifecycle]
prerequisites:
  - flutter.stateful_widget
  - flutter.future_builder
related:
  - flutter.async_cancellation
  - flutter.future_builder
  - flutter.stateful_widget
resource: https://docs.flutter.dev/
timestamp: 2026-01-01
---

## Summary

Start async work in **`initState`** (or after first frame), guard with **`mounted`** before `setState`, and **cancel/dispose** in `dispose`. Widget lifecycle for async prevents leaks and exceptions.

## Mental model

A widget's life has doors: enter (initState), maybe leave (dispose). Don't send mail to a demolished house—check mounted after awaits.

## Example

```dart
Future<void> _load() async {
  final data = await api.fetch();
  if (!mounted) return;
  setState(() => _data = data);
}

@override
void dispose() {
  _subscription?.cancel();
  super.dispose();
}
```

## Common mistakes

- setState after dispose.
- Starting HTTP in build.
- Ignoring mounted after await.

## Related concepts

- [Async Cancellation](/concepts/async_cancellation.md)
- [Future Builder](/concepts/future_builder.md)
- [Stateful Widget](/concepts/stateful_widget.md)

