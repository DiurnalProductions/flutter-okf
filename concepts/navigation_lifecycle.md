---
id: flutter.navigation_lifecycle
type: concept
title: Navigation Lifecycle
description: Route lifecycle hooks (initState, dispose, RouteAware) coordinate state with push and pop.
tags: [flutter, navigation, lifecycle]
prerequisites:
  - flutter.routes
  - flutter.stateful_widget
related:
  - flutter.async_cancellation
  - flutter.stateful_widget
  - flutter.routes
resource: https://docs.flutter.dev/
timestamp: 2026-01-01
---

## Summary

Screens enter and leave the stack: **`initState`/`dispose`** on StatefulWidgets, **`RouteAware`** for visibility, and async work must respect disposal on pop.

## Mental model

Leaving a room should turn off lights—cancel subscriptions and timers when route is popped. Navigation lifecycle ties to widget lifecycle and async cancellation.

## Example

```dart
class _PageState extends State<Page> with RouteAware {
  @override
  void didChangeDependencies() {
    super.didChangeDependencies();
    routeObserver.subscribe(this, ModalRoute.of(context)!);
  }

  @override
  void dispose() {
    routeObserver.unsubscribe(this);
    super.dispose();
  }
}
```

## Common mistakes

- Starting streams in build instead of initState.
- Ignoring dispose on popped routes.
- Assuming widget stays mounted after pop.

## Related concepts

- [Async Cancellation](/concepts/async_cancellation.md)
- [Stateful Widget](/concepts/stateful_widget.md)
- [Routes](/concepts/routes.md)

