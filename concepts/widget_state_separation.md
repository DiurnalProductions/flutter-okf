---
id: flutter.widget_state_separation
type: concept
title: Widget State Separation
description: Separate presentation widgets from state/models so UI stays declarative and testable.
tags: [flutter, architecture]
prerequisites:
  - flutter.provider_concept
  - flutter.state_lifting
related:
  - flutter.clean_architecture
  - flutter.provider_concept
  - flutter.state_management_boundaries
resource: https://docs.flutter.dev/
timestamp: 2026-01-01
---

## Summary

**Widget/state separation** keeps widgets thin: map state to widget trees; put logic in models, controllers, or notifiers. Composition over inheritance at app scale.

## Mental model

Widgets describe; models decide. Lifting and provider distribute state; widgets remain immutable configurations rebuilt cheaply.

## Example

```dart
class CartView extends StatelessWidget {
  const CartView({super.key, required this.controller});
  final CartController controller;

  @override
  Widget build(BuildContext context) {
    return ListenableBuilder(
      listenable: controller,
      builder: (_, __) => Text('Items: ${controller.count}'),
    );
  }
}
```

## Common mistakes

- 500-line build methods with business rules.
- Direct API calls inside StatelessWidget build.
- Mixing navigation and domain logic in widgets.

## Related concepts

- [Clean Architecture](/concepts/clean_architecture.md)
- [Provider Concept](/concepts/provider_concept.md)
- [State Management Boundaries](/concepts/state_management_boundaries.md)

