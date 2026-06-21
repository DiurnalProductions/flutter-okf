---
id: flutter.state_management_boundaries
type: concept
title: State Management Boundaries
description: Define where global, feature, and local state live to control rebuild scope.
tags: [flutter, architecture, state]
prerequisites:
  - flutter.provider_concept
  - flutter.clean_architecture
related:
  - flutter.dependency_injection
  - flutter.provider_concept
  - flutter.clean_architecture
resource: https://docs.flutter.dev/
timestamp: 2026-01-01
---

## Summary

**State management boundaries** place ephemeral UI state in `State`, feature state in scoped providers, and session/global state high in the tree—avoid one god notifier.

## Mental model

Draw circles on the tree: who may rebuild whom? Narrow boundaries keep rebuilds cheap and the rendering pipeline calm.

## Example

```dart
MultiProvider(
  providers: [
    ChangeNotifierProvider(create: (_) => SessionController()),
    ChangeNotifierProvider(create: (_) => CartController()),
  ],
  child: const AppShell(),
);
```

## Common mistakes

- Global provider for form field focus.
- Passing BuildContext into repositories.
- Duplicate state across routes.

## Related concepts

- [Dependency Injection](/concepts/dependency_injection.md)
- [Provider Concept](/concepts/provider_concept.md)
- [Clean Architecture](/concepts/clean_architecture.md)

