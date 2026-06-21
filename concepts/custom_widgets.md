---
id: flutter.custom_widgets
type: concept
title: Custom Widgets
description: Custom widgets encapsulate reusable UI and behavior behind a focused public API.
tags: [flutter, widgets, composition]
prerequisites:
  - flutter.widget_composition
related:
  - flutter.widget_composition
  - flutter.stateless_widget
  - flutter.platform_channels
resource: https://docs.flutter.dev/
timestamp: 2026-01-01
---

## Summary

Custom widgets wrap composition with **named parameters**, defaults, and documentation. They hide implementation details and expose only what callers need.

## Mental model

A custom widget is a **component contract**: stable constructor, minimal surface area, no leaky internals. Extract when a pattern repeats or subtree rebuild scope should shrink.

## Example

```dart
class PrimaryButton extends StatelessWidget {
  const PrimaryButton({super.key, required this.label, required this.onPressed});
  final String label;
  final VoidCallback onPressed;

  @override
  Widget build(BuildContext context) {
    return FilledButton(onPressed: onPressed, child: Text(label));
  }
}
```

## Common mistakes

- Exposing BuildContext-dependent children without documenting dependencies.
- Custom widgets that secretly mutate global singletons.
- Over-abstracting one-off UI into premature custom widgets.

## Related concepts

- [Widget Composition](/concepts/widget_composition.md)
- [Stateless Widget](/concepts/stateless_widget.md)
- [Platform Channels](/concepts/platform_channels.md)

