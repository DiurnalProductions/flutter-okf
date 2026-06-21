---
id: flutter.material_vs_cupertino
type: concept
title: Material vs Cupertino
description: Material and Cupertino libraries offer platform-styled widgets sharing the same rendering pipeline.
tags: [flutter, theming, platform]
prerequisites:
  - flutter.inherited_theming
related:
  - flutter.inherited_theming
  - flutter.design_tokens
  - flutter.platform_channels
resource: https://docs.flutter.dev/
timestamp: 2026-01-01
---

## Summary

**Material** (Android/Material 3) and **Cupertino** (iOS) are composable widget sets atop the same engine. `platform` package or adaptive constructors pick per OS.

## Mental model

Same immutable widget/render pipeline; different design languages. Composition lets you mix; inherited theming keeps each subtree coherent.

## Example

```dart
import 'dart:io' show Platform;

Widget build(BuildContext context) {
  if (Platform.isIOS) {
    return const CupertinoPageScaffold(child: Body());
  }
  return const Scaffold(body: Body());
}
```

## Common mistakes

- Cupertino inside Material without theme bridge.
- Platform checks scattered instead of adaptive widgets.
- Assuming Cupertino skips layout constraints (it doesn't).

## Related concepts

- [Inherited Theming](/concepts/inherited_theming.md)
- [Design Tokens](/concepts/design_tokens.md)
- [Platform Channels](/concepts/platform_channels.md)

