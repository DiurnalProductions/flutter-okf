---
id: flutter.provider_concept
type: concept
title: Provider Concept
description: Provider exposes inherited models with listen/watch APIs for scoped, reactive state distribution.
tags: [flutter, state, provider]
prerequisites:
  - flutter.inherited_widget_model
  - flutter.reactive_updates
related:
  - flutter.inherited_widget_model
  - flutter.state_management_boundaries
  - flutter.widget_state_separation
resource: https://docs.flutter.dev/
timestamp: 2026-01-01
---

## Summary

**Provider** places models above subtrees and exposes `context.watch`, `read`, and `select` for efficient rebuilds. It builds on inherited widget mechanics with ergonomics and scoping.

## Mental model

Provider is **state lifting with plumbing included**: register once near the feature root, consume deep in the tree without prop drilling. `select` narrows rebuilds to slices of model.

## Example

```dart
ChangeNotifierProvider(
  create: (_) => CartController(),
  child: const CheckoutPage(),
);

// In descendant:
final cart = context.watch<CartController>();
```

## Common mistakes

- Providing at app root when feature-local scope suffices.
- Using watch inside initState or callbacks (use read).
- Putting UI widgets inside ChangeNotifier.

## Related concepts

- [Inherited Widget Model](/concepts/inherited_widget_model.md)
- [State Management Boundaries](/concepts/state_management_boundaries.md)
- [Widget State Separation](/concepts/widget_state_separation.md)

