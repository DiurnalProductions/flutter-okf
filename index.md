# Flutter Knowledge Pack

> Flutter is a declarative UI framework where UI is a function of widget composition over a multi-phase rendering pipeline.

This OKF knowledge pack covers modern Flutter (Dart 3+, current widget and rendering architecture). It assumes separate Dart fundamentals knowledge may exist elsewhere, but links Dart-specific concepts where Flutter requires them.

---

## Start Here

If you are new to Flutter's architecture, begin with the **rendering model** — understanding that widgets are immutable descriptions, not UI objects, is the foundation for everything else.

**Recommended first concepts:**

1. [Declarative Rendering Model](/concepts/declarative_rendering_model.md)
2. [Widget Immutability](/concepts/widget_immutability.md)
3. [Widget Tree](/concepts/widget_tree.md)
4. [Element Tree](/concepts/element_tree.md)
5. [Render Tree](/concepts/render_tree.md)
6. [Build Lifecycle](/concepts/build_lifecycle.md)
7. [Rebuild Behavior](/concepts/rebuild_behavior.md)

---

## Rendering model

How Flutter turns immutable widget descriptions into pixels.

* [Declarative Rendering Model](/concepts/declarative_rendering_model.md) — UI as a function of state, not imperative mutation
* [Widget Immutability](/concepts/widget_immutability.md) — widgets are configuration objects, rebuilt frequently
* [Widget Tree](/concepts/widget_tree.md) — hierarchical UI descriptions from `build`
* [Element Tree](/concepts/element_tree.md) — persistent linkage between widgets and render objects
* [Render Tree](/concepts/render_tree.md) — layout, paint, and compositing nodes closest to pixels
* [Build Lifecycle](/concepts/build_lifecycle.md) — when and why `build` runs
* [Rebuild Behavior](/concepts/rebuild_behavior.md) — dirty tracking, reconciliation, and subtree updates
* [Build System](/concepts/build_system.md) — scheduling and coalescing rebuilds per frame

---

## Widget system

Composing and identifying UI from small, immutable building blocks.

* [StatelessWidget](/concepts/stateless_widget.md) — widgets with no local mutable state
* [StatefulWidget](/concepts/stateful_widget.md) — widgets backed by persistent `State` objects
* [Widget Composition](/concepts/widget_composition.md) — building UI by nesting widgets, not subclassing
* [Custom Widgets](/concepts/custom_widgets.md) — extracting reusable, focused widget APIs
* [Widget Identity](/concepts/widget_identity.md) — keys and type-based element matching during reconciliation

---

## State management

How state changes propagate into UI updates.

* [setState](/concepts/set_state.md) — local state mutation and subtree rebuild trigger
* [State Lifting](/concepts/state_lifting.md) — moving shared state to common ancestors
* [Inherited Widget](/concepts/inherited_widget.md) — propagating data down the tree efficiently
* [Inherited Widget Model](/concepts/inherited_widget_model.md) — dependency registration and selective rebuilds
* [Reactive Updates](/concepts/reactive_updates.md) — notification-driven UI refresh patterns
* [Provider Concept](/concepts/provider_concept.md) — architecture-level scoped state distribution

---

## Layout system

Constraint-driven sizing and positioning.

* [Constraints Model](/concepts/constraints_model.md) — parent-to-child constraint negotiation
* [Box Constraints](/concepts/box_constraints.md) — min/max width and height envelopes
* [Intrinsic Sizing](/concepts/intrinsic_sizing.md) — measuring natural size before layout
* [Flex Layout](/concepts/flex_layout.md) — `Row`, `Column`, and `Flex` along main/cross axes
* [Stack Layout](/concepts/stack_layout.md) — overlapping children with alignment and positioning
* [Layout Passes](/concepts/layout_passes.md) — how the render tree measures and positions nodes

---

## Rendering pipeline

The explicit phases from description to screen.

* [Build Phase](/concepts/build_phase.md) — widget descriptions reconciled into elements
* [Layout Phase](/concepts/layout_phase.md) — constraints applied, sizes computed
* [Paint Phase](/concepts/paint_phase.md) — display lists recorded for visual output
* [Compositing Phase](/concepts/compositing_phase.md) — layers assembled for GPU upload
* [Rendering Performance](/concepts/rendering_performance.md) — repaint boundaries, rebuild scope, and profiling

---

## Navigation

Stack-based routing and screen lifecycle.

* [Navigator Stack](/concepts/navigator_stack.md) — route stack semantics and back navigation
* [Routes](/concepts/routes.md) — `Route` objects, pages, and transitions
* [Named vs Dynamic Navigation](/concepts/named_vs_dynamic_navigation.md) — declarative named routes vs imperative pushes
* [Navigation Lifecycle](/concepts/navigation_lifecycle.md) — route awareness, disposal, and state persistence

---

## Animation

Time-based UI transitions integrated with the frame pipeline.

* [vsync](/concepts/vsync.md) — frame ticker and `TickerProvider` contract
* [AnimationController](/concepts/animation_controller.md) — explicit time progression and status
* [Tween System](/concepts/tween_system.md) — interpolating between begin and end values
* [Implicit Animations](/concepts/implicit_animations.md) — animated widgets driven by property changes
* [Explicit Animations](/concepts/explicit_animations.md) — `AnimationController` + builder/listener integration

---

## Async UI integration

Connecting asynchronous work to the widget lifecycle.

* [FutureBuilder](/concepts/future_builder.md) — building UI from one-shot async results
* [StreamBuilder](/concepts/stream_builder.md) — building UI from ongoing stream events
* [Widget Lifecycle Async](/concepts/widget_lifecycle_async.md) — initState, dispose, and async interaction
* [Async Cancellation](/concepts/async_cancellation.md) — avoiding updates after disposal

---

## Architecture

Separation of concerns beyond individual widgets.

* [Widget State Separation](/concepts/widget_state_separation.md) — MVVM-style view vs view-model boundaries
* [Clean Architecture](/concepts/clean_architecture.md) — layers, dependencies, and testability in Flutter apps
* [State Management Boundaries](/concepts/state_management_boundaries.md) — where state lives and who may mutate it
* [Dependency Injection](/concepts/dependency_injection.md) — providing services and repositories to the widget tree

---

## Theming

Design system propagation through inherited configuration.

* [ThemeData](/concepts/theme_data.md) — centralized color, typography, and component styling
* [Inherited Theming](/concepts/inherited_theming.md) — `Theme.of` and subtree theme overrides
* [Material vs Cupertino](/concepts/material_vs_cupertino.md) — adaptive widget families and platform feel
* [Design Tokens](/concepts/design_tokens.md) — semantic tokens mapped into `ThemeData` and `ColorScheme`

---

## Platform integration

Bridging Flutter to native capabilities and constraints.

* [Platform Channels](/concepts/platform_channels.md) — async message passing to host platform code
* [Native Bridges](/concepts/native_bridges.md) — embedding Flutter and bidirectional communication
* [Plugin Architecture](/concepts/plugin_architecture.md) — federated plugins and platform interface pattern
* [Platform Rendering Constraints](/concepts/platform_rendering_constraints.md) — embedder, surface, and DPI considerations

---

## Recommended learning progression

### Phase 1 — Core mental model

Understand the three trees and why rebuilds are normal:

`declarative_rendering_model` → `widget_immutability` → `widget_tree` → `element_tree` → `render_tree` → `build_lifecycle` → `rebuild_behavior`

### Phase 2 — Widgets and local state

`stateless_widget` → `stateful_widget` → `widget_composition` → `custom_widgets` → `set_state` → `widget_identity`

### Phase 3 — Layout and pipeline

`constraints_model` → `box_constraints` → `flex_layout` → `stack_layout` → `layout_passes` → `build_phase` → `layout_phase` → `paint_phase` → `compositing_phase`

### Phase 4 — Shared state and architecture

`state_lifting` → `inherited_widget` → `inherited_widget_model` → `reactive_updates` → `provider_concept` → `widget_state_separation` → `clean_architecture`

### Phase 5 — Scrolling, navigation, animation

`viewport_management` → `list_view` → `lazy_rendering` → `slivers` → `navigator_stack` → `routes` → `vsync` → `animation_controller` → `explicit_animations`

### Phase 6 — Production concerns

`future_builder` → `widget_lifecycle_async` → `async_cancellation` → `theme_data` → `rendering_performance` → `platform_channels` → `plugin_architecture`

---

## Lists and performance

Concepts for scalable scrolling UIs (also covered in Phase 5):

* [ListView](/concepts/list_view.md) — scrollable linear lists with lazy children
* [GridView](/concepts/grid_view.md) — two-dimensional lazy grids
* [Slivers](/concepts/slivers.md) — composable scroll effects and custom scrollables
* [Lazy Rendering](/concepts/lazy_rendering.md) — building only visible children
* [Viewport Management](/concepts/viewport_management.md) — scroll offset, cache extent, and visible region

---

## Dependency graph overview

```text
declarative_rendering_model
  └─ widget_immutability
       └─ widget_tree
            ├─ element_tree → render_tree → constraints_model → layout...
            ├─ build_lifecycle → rebuild_behavior → build_system → build_phase
            └─ stateless_widget → stateful_widget → set_state → state_lifting
                 └─ inherited_widget → inherited_widget_model → provider_concept
```

The full graph is a directed acyclic graph (DAG) with no circular prerequisites. Each concept file lists its `prerequisites` and `related` IDs in YAML frontmatter.
