---
id: flutter.clean_architecture
type: concept
title: Clean Architecture
description: Layer UI, domain, and data with dependencies pointing inward toward business rules.
tags: [flutter, architecture]
prerequisites:
  - flutter.widget_state_separation
related:
  - flutter.state_management_boundaries
  - flutter.dependency_injection
  - flutter.widget_state_separation
resource: https://docs.flutter.dev/
timestamp: 2026-01-01
---

## Summary

**Clean architecture** in Flutter: presentation (widgets), domain (entities, use cases), data (repositories, APIs). Framework details stay at the edges.

## Mental model

Onion layers: Flutter is outer skin. Inner layers know nothing about widgets. State management boundaries align with use case orchestration.

## Example

```dart
// domain
class LoadUser {
  LoadUser(this.repo);
  final UserRepository repo;
  Future<User> call(String id) => repo.getUser(id);
}

// presentation consumes use case via DI
```

## Common mistakes

- Repositories imported in widgets directly.
- Domain layer importing material.dart.
- Over-layering tiny apps.

## Related concepts

- [State Management Boundaries](/concepts/state_management_boundaries.md)
- [Dependency Injection](/concepts/dependency_injection.md)
- [Widget State Separation](/concepts/widget_state_separation.md)

