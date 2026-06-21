---
id: flutter.inherited_widget
type: concept
title: Inherited Widget
description: InheritedWidget propagates configuration down the tree and notifies dependents when data changes.
tags: [flutter, state, inherited]
prerequisites:
  - flutter.state_lifting
related:
  - flutter.inherited_widget_model
  - flutter.theme_data
  - flutter.reactive_updates
resource: https://docs.flutter.dev/
timestamp: 2026-01-01
---

## Summary

`InheritedWidget` exposes data to descendants via `dependOnInheritedWidgetOfExactType`. Registered dependents **rebuild when the inherited widget updates**.

## Mental model

A **broadcast channel** in the widget tree: ancestors publish, descendants subscribe implicitly through context. Theme and MediaQuery are inherited widgets.

## Example

```dart
class SettingsScope extends InheritedWidget {
  const SettingsScope({super.key, required this.darkMode, required super.child});
  final bool darkMode;

  static SettingsScope of(BuildContext context) {
    return context.dependOnInheritedWidgetOfExactType<SettingsScope>()!;
  }

  @override
  bool updateShouldNotify(SettingsScope old) => darkMode != old.darkMode;
}
```

## Common mistakes

- Using InheritedWidget without updateShouldNotify precision.
- Calling of() without dependOn (no rebuild registration).
- Storing large mutable objects without immutable snapshots.

## Related concepts

- [Inherited Widget Model](/concepts/inherited_widget_model.md)
- [Theme Data](/concepts/theme_data.md)
- [Reactive Updates](/concepts/reactive_updates.md)

