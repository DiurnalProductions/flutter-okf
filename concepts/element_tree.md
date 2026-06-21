---
id: flutter.element_tree
type: concept
title: Element Tree
description: The element tree is the mutable, long-lived linkage layer that mounts widgets to render objects and survives rebuilds.
tags: [flutter, rendering, elements]
prerequisites:
  - flutter.widget_tree
related:
  - flutter.render_tree
  - flutter.widget_identity
  - flutter.rebuild_behavior
resource: https://docs.flutter.dev/
timestamp: 2026-01-01
---

## Summary

**Elements** are persistent handles between widgets and render objects. When the widget tree rebuilds, elements decide whether to update in place, replace children, or reuse subtrees based on type and keys.

## Mental model

Widgets are blueprints; **elements are scaffolding** that stays between revisions. `StatefulElement` holds `State`, which survives widget instance replacement.

## Example

```dart
// Rebuild with new Text data — TextElement updates in place
return Text(title);
```

## Common mistakes

- Assuming elements are recreated on every setState.
- Changing widget runtimeType without a key and expecting state preservation.
- Debugging only widgets and ignoring element reuse.

## Related concepts

- [Render Tree](/concepts/render_tree.md)
- [Widget Identity](/concepts/widget_identity.md)
- [Rebuild Behavior](/concepts/rebuild_behavior.md)

