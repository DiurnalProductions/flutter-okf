---
id: flutter.inherited_widget_model
type: concept
title: Inherited Widget Model
description: The recommended pattern wraps InheritedWidget with a model class and static lookup methods.
tags: [flutter, state, inherited]
prerequisites:
  - flutter.inherited_widget
related:
  - flutter.provider_concept
  - flutter.theme_data
  - flutter.inherited_widget
resource: https://docs.flutter.dev/
timestamp: 2026-01-01
---

## Summary

The **inherited widget model** pattern separates data (`ChangeNotifier`, immutable config) from the `InheritedWidget` shell that calls `updateShouldNotify`.

## Mental model

Model holds business-friendly API; inherited wrapper is plumbing. Provider and Theme extend this idea—state drives rebuilds through dependency edges, not manual setState in every leaf.

## Example

```dart
class CartModel extends InheritedWidget {
  const CartModel({super.key, required this.items, required super.child});
  final List<String> items;

  static CartModel watch(BuildContext context) {
    return context.dependOnInheritedWidgetOfExactType<CartModel>()!;
  }

  @override
  bool updateShouldNotify(CartModel old) => items != old.items;
}
```

## Common mistakes

- Fat inherited widgets that also perform side effects.
- Deep dependOn chains causing wide rebuilds.
- Not using listen: false vs watch patterns in Provider.

## Related concepts

- [Provider Concept](/concepts/provider_concept.md)
- [Theme Data](/concepts/theme_data.md)
- [Inherited Widget](/concepts/inherited_widget.md)

