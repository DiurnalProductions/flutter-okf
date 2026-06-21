---
id: flutter.future_builder
type: concept
title: Future Builder
description: FutureBuilder rebuilds when a Future completes, mapping snapshot to widgets.
tags: [flutter, async]
prerequisites:
  - flutter.stateful_widget
  - flutter.reactive_updates
related:
  - flutter.stream_builder
  - flutter.widget_lifecycle_async
  - flutter.reactive_updates
resource: https://docs.flutter.dev/
timestamp: 2026-01-01
---

## Summary

**FutureBuilder** subscribes to a `Future` and builds from `AsyncSnapshot` (waiting, done, error). Tie futures to **StatefulWidget lifecycle**—don't recreate future every build.

## Mental model

Reactive shell around one-shot async: state drives rebuilds when snapshot changes. Presentation mapping belongs in builder; fetch belongs in initState or repository.

## Example

```dart
class _LoadState extends State<LoadPage> {
  late final Future<Data> _future;

  @override
  void initState() {
    super.initState();
    _future = repo.fetchData();
  }

  @override
  Widget build(BuildContext context) {
    return FutureBuilder<Data>(
      future: _future,
      builder: (context, snapshot) {
        if (snapshot.connectionState != ConnectionState.done) {
          return const CircularProgressIndicator();
        }
        if (snapshot.hasError) return Text('Error');
        return Text('${snapshot.data}');
      },
    );
  }
}
```

## Common mistakes

- Creating Future in build (restarts every rebuild).
- No error UI branch.
- Ignoring connectionState and showing stale data.

## Related concepts

- [Stream Builder](/concepts/stream_builder.md)
- [Widget Lifecycle Async](/concepts/widget_lifecycle_async.md)
- [Reactive Updates](/concepts/reactive_updates.md)

