---
id: flutter.widget_identity
type: concept
title: Widget Identity
description: Widget identity (type, key, slot) determines how elements match old and new configurations during reconciliation.
tags: [flutter, widgets, keys]
prerequisites:
  - flutter.widget_tree
  - flutter.rebuild_behavior
related:
  - flutter.element_tree
  - flutter.rebuild_behavior
  - flutter.list_view
resource: https://docs.flutter.dev/
timestamp: 2026-01-01
---

## Summary

Reconciliation matches widgets by **runtimeType**, **key**, and **child slot**. Same type + same key → update in place. Different key → replace subtree (new State).

## Mental model

Keys are **name tags on moving boxes**. Without keys, Flutter matches by position; reordering lists can reuse wrong State. `ValueKey`, `ObjectKey`, and `GlobalKey` solve different problems.

## Example

```dart
ListView.builder(
  itemCount: items.length,
  itemBuilder: (context, index) {
    final item = items[index];
    return ListTile(key: ValueKey(item.id), title: Text(item.title));
  },
);
```

## Common mistakes

- Using GlobalKey everywhere (expensive, rarely needed).
- Random keys that force unnecessary element recreation.
- Keys on Stateless-only subtrees that never move.

## Related concepts

- [Element Tree](/concepts/element_tree.md)
- [Rebuild Behavior](/concepts/rebuild_behavior.md)
- [List View](/concepts/list_view.md)

