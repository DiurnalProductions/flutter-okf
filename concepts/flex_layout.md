---
id: flutter.flex_layout
type: concept
title: Flex Layout
description: Row and Column use flex factors to distribute space along the main axis under box constraints.
tags: [flutter, layout, flex]
prerequisites:
  - flutter.box_constraints
related:
  - flutter.box_constraints
  - flutter.stack_layout
  - flutter.layout_passes
resource: https://docs.flutter.dev/
timestamp: 2026-01-01
---

## Summary

**Flex layout** (`Row`, `Column`, `Flex`) divides **main-axis** space using `Expanded` and `Flexible` (`flex` factors). Cross-axis alignment is separate (`CrossAxisAlignment`).

## Mental model

Flex is **elastic band splitting**: remaining space after non-flex children is shared by flex children proportionally. Unbounded main axis + Expanded = runtime error.

## Example

```dart
Row(
  children: [
    const Icon(Icons.star),
    Expanded(child: Text(title)),
    Text(trailing),
  ],
)
```

## Common mistakes

- Expanded inside unbounded scrollable main axis.
- Nested Rows without Expanded causing overflow.
- Using Spacer without flex parent.

## Related concepts

- [Box Constraints](/concepts/box_constraints.md)
- [Stack Layout](/concepts/stack_layout.md)
- [Layout Passes](/concepts/layout_passes.md)

