---
id: flutter.box_constraints
type: concept
title: Box Constraints
description: BoxConstraints encode minimum and maximum width and height for a render object's layout.
tags: [flutter, layout]
prerequisites:
  - flutter.constraints_model
related:
  - flutter.constraints_model
  - flutter.flex_layout
  - flutter.intrinsic_sizing
resource: https://docs.flutter.dev/
timestamp: 2026-01-01
---

## Summary

A **BoxConstraints** has `minWidth`, `maxWidth`, `minHeight`, `maxHeight`. `constrainSize` clamps a desired size. `tightFor` and `loose` are common factory patterns.

## Mental model

A box must fit inside the envelope. `hasBoundedWidth`, `isTight`, and `biggest` answer layout questions during debugging.

## Example

```dart
BoxConstraints constraints = BoxConstraints(
  minWidth: 0,
  maxWidth: 300,
  minHeight: 48,
  maxHeight: 48,
);
```

## Common mistakes

- Using double.infinity without a bounded parent.
- Tight height inside vertical ListView without shrinkWrap/slivers.
- Mixing intrinsic sizing with unbounded flex children incorrectly.

## Related concepts

- [Constraints Model](/concepts/constraints_model.md)
- [Flex Layout](/concepts/flex_layout.md)
- [Intrinsic Sizing](/concepts/intrinsic_sizing.md)

