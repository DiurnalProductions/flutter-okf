---
id: flutter.state_lifting
type: concept
title: State Lifting
description: Lift shared state to the lowest common ancestor so multiple children read one source of truth.
tags: [flutter, state, architecture]
prerequisites:
  - flutter.set_state
related:
  - flutter.inherited_widget
  - flutter.provider_concept
  - flutter.widget_state_separation
resource: https://docs.flutter.dev/
timestamp: 2026-01-01
---

## Summary

**State lifting** moves mutable state up to the parent that coordinates siblings. Children receive values and callbacks instead of each owning duplicate state.

## Mental model

If two widgets must stay in sync, **one owns the truth** upstream. Downstream widgets are functions of that state—classic unidirectional data flow before global stores.

## Example

```dart
class Parent extends StatefulWidget {
  @override
  State<Parent> createState() => _ParentState();
}

class _ParentState extends State<Parent> {
  int _selected = 0;

  @override
  Widget build(BuildContext context) {
    return Row(
      children: [
        Selector(
          selected: _selected,
          onSelect: (i) => setState(() => _selected = i),
        ),
        DetailPane(index: _selected),
      ],
    );
  }
}
```

## Common mistakes

- Duplicating state in sibling StatefulWidgets.
- Lifting so high that unrelated subtrees rebuild together.
- Passing BuildContext to services instead of callbacks.

## Related concepts

- [Inherited Widget](/concepts/inherited_widget.md)
- [Provider Concept](/concepts/provider_concept.md)
- [Widget State Separation](/concepts/widget_state_separation.md)

