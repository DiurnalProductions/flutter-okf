---
id: flutter.set_state
type: concept
title: setState
description: setState marks an element dirty after mutating State, scheduling a localized rebuild.
tags: [flutter, state]
prerequisites:
  - flutter.stateful_widget
  - flutter.rebuild_behavior
related:
  - flutter.rebuild_behavior
  - flutter.state_lifting
  - flutter.reactive_updates
resource: https://docs.flutter.dev/
timestamp: 2026-01-01
---

## Summary

`setState` notifies the framework that **State fields changed** and a rebuild is needed. The closure should only mutate state; build reads the new values.

## Mental model

Flip a dirty flag on your element: 'my description is stale.' State drives rebuilds; reconciliation then decides layout/paint work. Keep setState granular to subtrees that actually changed.

## Example

```dart
void _toggle() {
  setState(() {
    _enabled = !_enabled;
  });
}
```

## Common mistakes

- Mutating state without setState (UI won't update).
- Heavy async work inside the setState closure.
- setState after dispose.

## Related concepts

- [Rebuild Behavior](/concepts/rebuild_behavior.md)
- [State Lifting](/concepts/state_lifting.md)
- [Reactive Updates](/concepts/reactive_updates.md)

