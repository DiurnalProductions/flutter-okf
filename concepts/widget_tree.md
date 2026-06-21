---
id: flutter.widget_tree
type: concept
title: Widget Tree
description: The widget tree is the hierarchical, immutable description of UI produced by build methods and composition.
tags: [flutter, widgets, tree]
prerequisites:
  - flutter.declarative_rendering_model
  - flutter.widget_immutability
related:
  - flutter.element_tree
  - flutter.widget_composition
  - flutter.build_lifecycle
resource: https://docs.flutter.dev/
timestamp: 2026-01-01
---

## Summary

The **widget tree** is the tree of widget instances from `build`, nested via **composition**. It exists for the current frame's reconciliation and is rebuilt frequently—it is not what is painted.

## Mental model

Blueprints submitted each frame. Architects (`build`) hand fresh blueprints; the crew (framework) maps them to existing scaffolding (elements) where possible instead of demolishing every time.

## Example

```dart
Widget build(BuildContext context) {
  return Scaffold(
    appBar: AppBar(title: const Text('Home')),
    body: Column(
      children: [
        const Header(),
        Expanded(child: ItemList(items: items)),
      ],
    ),
  );
}
```

## Common mistakes

- Confusing widget tree with persistent UI objects.
- Monolithic build methods instead of composed subtrees.
- Using print in build and assuming the tree is built once.

## Related concepts

- [Element Tree](/concepts/element_tree.md)
- [Widget Composition](/concepts/widget_composition.md)
- [Build Lifecycle](/concepts/build_lifecycle.md)

