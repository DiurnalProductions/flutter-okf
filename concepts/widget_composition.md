---
id: flutter.widget_composition
type: concept
title: Widget Composition
description: Flutter UI is built by composing small widgets rather than subclassing framework widgets.
tags: [flutter, widgets, composition]
prerequisites:
  - flutter.stateless_widget
related:
  - flutter.custom_widgets
  - flutter.stateless_widget
  - flutter.navigator_stack
resource: https://docs.flutter.dev/
timestamp: 2026-01-01
---

## Summary

**Composition over inheritance** is the primary Flutter design technique. You combine `StatelessWidget`/`StatefulWidget` trees instead of extending `Text` or `Container`.

## Mental model

Build LEGO structures: small pieces with clear names snap together. Parents pass data down; callbacks pass events up. Deep trees of tiny widgets are idiomatic and enable cheap localized rebuilds.

## Example

```dart
class ProfileCard extends StatelessWidget {
  const ProfileCard({super.key, required this.name, required this.avatar});
  final String name;
  final Widget avatar;

  @override
  Widget build(BuildContext context) {
    return Card(
      child: ListTile(leading: avatar, title: Text(name)),
    );
  }
}
```

## Common mistakes

- Subclassing Material widgets to tweak one behavior.
- God widgets that mix layout, networking, and navigation.
- Duplicating subtrees instead of extracting reusable widgets.

## Related concepts

- [Custom Widgets](/concepts/custom_widgets.md)
- [Stateless Widget](/concepts/stateless_widget.md)
- [Navigator Stack](/concepts/navigator_stack.md)

