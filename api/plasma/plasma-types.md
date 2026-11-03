---
title: "Plasma::Types Class"
description: "Enums and constants used in Plasma."
---

# Plasma::Types Class

Enums and constants used in Plasma. [More...](#details)

- **Header:** `#include <Plasma/Plasma>`
- **CMake:** `find_package(Plasma REQUIRED)`  
  `target_link_libraries(mytarget PRIVATE Plasma::Plasma)`
- **Inherits:** [QObject](https://doc.qt.io/qt-6/qobject.html)

[List of all members, including inherited members](plasma-types-members.md)

## Public Types

- [enum Types::BackgroundHints](#BackgroundHints-enum)
- [enum Types::ContainmentDisplayHint](#ContainmentDisplayHint-enum)
- [enum Types::FormFactor](#FormFactor-enum)
- [enum Types::ImmutabilityType](#ImmutabilityType-enum)
- [enum Types::ItemStatus](#ItemStatus-enum)
- [enum Types::Location](#Location-enum)

## Detailed Description {#details}

## Member Type Documentation {#member-type-documentation}

### enum Types::BackgroundHints {#BackgroundHints-enum}

**flags Types::BackgroundFlags**

Description on how draw a background for the applet

| Constant | Value | Description |
| --- | --- | --- |
| `Plasma::Types::NoBackground` | `0` | Not drawing a background under the applet, the applet has its own implementation |
| `Plasma::Types::StandardBackground` | `1` | The standard background from the theme is drawn |
| `Plasma::Types::TranslucentBackground` | `2` | An alternate version of the background is drawn, usually more translucent |
| `Plasma::Types::ShadowBackground` | `4` | The applet won't have a svg background but a drop shadow of its content done via a shader |
| `Plasma::Types::ConfigurableBackground` | `8` | If the hint has this flag, the user is able to configure this background |
| `Plasma::Types::DefaultBackground` | `StandardBackground` | Default settings: both standard background |

The `BackgroundFlags` type is a typedef for `QFlags<BackgroundHints>. `It stores an OR combination of `BackgroundHints` values.

### enum Types::ContainmentDisplayHint {#ContainmentDisplayHint-enum}

**flags Types::ContainmentDisplayHints**

Display hints that come from the containment that suggest the applet how to look and behave.

| Constant | Value |   |
| --- | --- | --- |
| `Plasma::Types::NoContainmentDisplayHint` | `0` |   |
| `Plasma::Types::ContainmentDrawsPlasmoidHeading` | `1` | The containment will draw an titlebar-looking header for the applets, so the applets shouldn't attempt to paint a similar thing |
| `Plasma::Types::ContainmentForcesSquarePlasmoids` | `2` | The containment will force every plasmoid to be constrained in a square icon (An example is the System Tray) |
| `Plasma::Types::ContainmentPrefersOpaqueBackground` | `4` | The containment prefers the style of the applets to be opaque, where applicable |
| `Plasma::Types::ContainmentPrefersFloatingApplets` | `8` | The containment prefers applet's dialogs to be floating, where applicable |

The `ContainmentDisplayHints` type is a typedef for `QFlags<ContainmentDisplayHint>. `It stores an OR combination of `ContainmentDisplayHint` values.

### enum Types::FormFactor {#FormFactor-enum}

The FormFactor enumeration describes how a [Plasma::Applet](plasma-applet.md) should arrange itself. The value is derived from the container managing the Applet (e.g. in Plasma, a Corona on the desktop or on a panel).

| Constant | Value | Description |
| --- | --- | --- |
| `Plasma::Types::Planar` | `0` | The applet lives in a plane and has two degrees of freedom to grow. Optimize for desktop, laptop or tablet usage: a high resolution screen 1-3 feet distant from the viewer. |
| `Plasma::Types::MediaCenter` | `1` | As with Planar, the applet lives in a plane but the interface should be optimized for medium-to-high resolution screens that are 5-15 feet distant from the viewer. Sometimes referred to as a "ten foot interface". |
| `Plasma::Types::Horizontal` | `2` | The applet is constrained vertically, but can expand horizontally. |
| `Plasma::Types::Vertical` | `3` | The applet is constrained horizontally, but can expand vertically. |
| `Plasma::Types::Application` | `4` | The Applet lives in a plane and should be optimized to look as a full application, for the desktop or the particular device. |

### enum Types::ImmutabilityType {#ImmutabilityType-enum}

Defines the immutability of items like applets, corona and containments they can be free to modify, locked down by the user or locked down by the system (e.g. kiosk setups).

| Constant | Value | Description |
| --- | --- | --- |
| `Plasma::Types::Mutable` | `1` | The item can be modified in any way |
| `Plasma::Types::UserImmutable` | `2` | The user has requested a lock down, and can undo the lock down at any time |
| `Plasma::Types::SystemImmutable` | `4` | The item is locked down by the system, the user can't unlock it |

### enum Types::ItemStatus {#ItemStatus-enum}

Status of an applet

| Constant | Value | Description |
| --- | --- | --- |
| `Plasma::Types::UnknownStatus` | `0` | The status is unknown |
| `Plasma::Types::PassiveStatus` | `1` | The item is passive |
| `Plasma::Types::ActiveStatus` | `2` | The item is active |
| `Plasma::Types::NeedsAttentionStatus` | `3` | The item needs attention |
| `Plasma::Types::RequiresAttentionStatus` | `4` | The item needs persistent attention |
| `Plasma::Types::AcceptingInputStatus` | `5` | The item is accepting input |
| `Plasma::Types::HiddenStatus` | `6` | The item will be hidden totally |

### enum Types::Location {#Location-enum}

The Location enumeration describes where on screen an element, such as an Applet or its managing container, is positioned on the screen.

| Constant | Value | Description |
| --- | --- | --- |
| `Plasma::Types::Floating` | `0` | Free floating. Neither geometry or z-ordering is described precisely by this value. |
| `Plasma::Types::Desktop` | `1` | On the planar desktop layer, extending across the full screen from edge to edge. |
| `Plasma::Types::FullScreen` | `2` | Full screen |
| `Plasma::Types::TopEdge` | `3` | Along the top of the screen |
| `Plasma::Types::BottomEdge` | `4` | Along the bottom of the screen |
| `Plasma::Types::LeftEdge` | `5` | Along the left side of the screen |
| `Plasma::Types::RightEdge` | `6` | Along the right side of the screen |
