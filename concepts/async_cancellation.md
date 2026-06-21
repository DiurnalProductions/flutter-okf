---
id: flutter.async_cancellation
type: concept
title: Async Cancellation
description: Cancel timers, subscriptions, and in-flight work when widgets dispose or routes pop.
tags: [flutter, async, lifecycle]
prerequisites:
  - flutter.widget_lifecycle_async
related:
  - flutter.widget_lifecycle_async
  - flutter.navigation_lifecycle
  - flutter.stream_builder
resource: https://docs.flutter.dev/
timestamp: 2026-01-01
---

## Summary

**Async cancellation** stops work that would update disposed widgets: `StreamSubscription.cancel`, `Timer.cancel`, `CancelableOperation`, and abort tokens for HTTP.

## Mental model

Leaving a page should tear down listeners. Navigation lifecycle and dispose are the hooks. State drives UI only while element is mounted.

## Example

```dart
late final StreamSubscription _sub;

@override
void initState() {
  super.initState();
  _sub = repo.changes.listen(_onChange);
}

@override
void dispose() {
  _sub.cancel();
  super.dispose();
}
```

## Common mistakes

- Fire-and-forget futures without mounted guard.
- Global streams never unsubscribed.
- Animation controllers left running after pop.

## Related concepts

- [Widget Lifecycle Async](/concepts/widget_lifecycle_async.md)
- [Navigation Lifecycle](/concepts/navigation_lifecycle.md)
- [Stream Builder](/concepts/stream_builder.md)

