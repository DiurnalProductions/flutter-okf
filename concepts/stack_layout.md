---
id: flutter.stack_layout
type: concept
title: Stack Layout
description: Stack positions non-positioned children aligned, and Positioned children relative to the stack.
tags: [flutter, layout, stack]
prerequisites:
  - flutter.box_constraints
related:
  - flutter.box_constraints
  - flutter.flex_layout
  - flutter.compositing_phase
resource: https://docs.flutter.dev/
timestamp: 2026-01-01
---

## Summary

**Stack** paints children **overlapped** in z-order. Non-positioned children are sized by `StackFit` and aligned via `alignment`. `Positioned` uses edge insets.

## Mental model

A deck of cards stacked on a table. Bottom child sizes the stack (unless positioned-only). Use `clipBehavior` when children paint outside bounds.

## Example

```dart
Stack(
  alignment: Alignment.center,
  children: [
    Container(width: 200, height: 200, color: Colors.grey),
    Positioned(
      bottom: 8,
      right: 8,
      child: Icon(Icons.check),
    ),
  ],
)
```

## Common mistakes

- Positioned without Stack parent.
- Expecting Stack to scroll overflow content.
- Too many overlapping unpainted layers hurting performance.

## Related concepts

- [Box Constraints](/concepts/box_constraints.md)
- [Flex Layout](/concepts/flex_layout.md)
- [Compositing Phase](/concepts/compositing_phase.md)

