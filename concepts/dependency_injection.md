---
id: flutter.dependency_injection
type: concept
title: Dependency Injection
description: Inject dependencies via constructors, providers, or service locators for testability.
tags: [flutter, architecture, di]
prerequisites:
  - flutter.state_management_boundaries
related:
  - flutter.clean_architecture
  - flutter.state_management_boundaries
  - flutter.provider_concept
resource: https://docs.flutter.dev/
timestamp: 2026-01-01
---

## Summary

**Dependency injection** supplies repositories, clients, and use cases without hard-coded `new` in widgets. Provider, `get_it`, and manual constructor injection are common.

## Mental model

Widgets ask for capabilities, not concrete singletons. Swap fakes in tests; compose graphs at app bootstrap.

## Example

```dart
Provider<AuthRepository>(
  create: (_) => ApiAuthRepository(client: httpClient),
  child: const App(),
);
```

## Common mistakes

- Service locator calls inside build.
- Hidden singletons in static fields.
- Injecting BuildContext into data layer.

## Related concepts

- [Clean Architecture](/concepts/clean_architecture.md)
- [State Management Boundaries](/concepts/state_management_boundaries.md)
- [Provider Concept](/concepts/provider_concept.md)

