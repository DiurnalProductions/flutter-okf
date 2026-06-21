---
id: flutter.stream_builder
type: concept
title: Stream Builder
description: StreamBuilder rebuilds on stream events, similar to FutureBuilder for ongoing data.
tags: [flutter, async, streams]
prerequisites:
  - flutter.future_builder
related:
  - flutter.future_builder
  - flutter.widget_lifecycle_async
  - flutter.async_cancellation
resource: https://docs.flutter.dev/
timestamp: 2026-01-01
---

## Summary

**StreamBuilder** listens to a `Stream` and rebuilds on events. Use for live data; cancel via widget disposal when stream is not broadcast-managed elsewhere.

## Mental model

FutureBuilder's chatty sibling—events keep coming. Lifecycle matters: don't leak subscriptions; prefer exposing streams from controllers disposed with State.

## Example

```dart
StreamBuilder<int>(
  stream: counterStream,
  initialData: 0,
  builder: (context, snapshot) => Text('${snapshot.data}'),
)
```

## Common mistakes

- Listening to same single-subscription stream twice.
- No initialData when UI needs synchronous first frame.
- Building stream inside build without caching.

## Related concepts

- [Future Builder](/concepts/future_builder.md)
- [Widget Lifecycle Async](/concepts/widget_lifecycle_async.md)
- [Async Cancellation](/concepts/async_cancellation.md)

