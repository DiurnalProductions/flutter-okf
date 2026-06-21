---
id: flutter.intrinsic_sizing
type: concept
title: Intrinsic Sizing
description: Intrinsic dimensions let parents query a child's preferred size before full layout.
tags: [flutter, layout]
prerequisites:
  - flutter.box_constraints
related:
  - flutter.box_constraints
  - flutter.flex_layout
  - flutter.layout_passes
resource: https://docs.flutter.dev/
timestamp: 2026-01-01
---

## Summary

**Intrinsic sizing** (`IntrinsicHeight`, `IntrinsicWidth`, `RenderBox.computeMinIntrinsicWidth`, etc.) resolves sizes that depend on cross-axis measurements. It is expensive—use sparingly.

## Mental model

Normally layout is one pass down/up. Intrinsic layout asks 'how big would you like to be?' before committing—like measuring clothes twice. Prefer flex and fixed sizes when possible.

## Example

```dart
IntrinsicHeight(
  child: Row(
    crossAxisAlignment: CrossAxisAlignment.stretch,
    children: [
      Expanded(child: Text('Long text...')),
      VerticalDivider(),
      Text('Side'),
    ],
  ),
)
```

## Common mistakes

- Wrapping large lists in IntrinsicHeight.
- Assuming intrinsic passes are free.
- Using intrinsic sizing where Expanded/Flex suffices.

## Related concepts

- [Box Constraints](/concepts/box_constraints.md)
- [Flex Layout](/concepts/flex_layout.md)
- [Layout Passes](/concepts/layout_passes.md)

