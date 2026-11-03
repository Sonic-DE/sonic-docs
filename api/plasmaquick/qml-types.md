---
title: "Types QML Type"
description: "Enums and constants used in Plasma."
---

# Types QML Type

Enums and constants used in Plasma. [More...](#details)

## Detailed Description {#details}

## Property Documentation {#property-documentation}

### BackgroundHints : enumeration {#BackgroundHints-prop}

Description on how draw a background for the applet

| Constant | Description |
| --- | --- |
| NoBackground | Not drawing a background under the applet, the applet has its own implementation |
| StandardBackground | The standard background from the theme is drawn |
| TranslucentBackground | An alternate version of the background is drawn, usually more translucent |
| ShadowBackground | The applet won't have a svg background but a drop shadow of its content done via a shader |
| ConfigurableBackground | If the hint has this flag, the user is able to configure this background |
| DefaultBackground | Default settings: both standard background |

### ContainmentDisplayHint : enumeration {#ContainmentDisplayHint-prop}

Display hints that come from the containment that suggest the applet how to look and behave.

| Constant |   |
| --- | --- |
| NoContainmentDisplayHint |   |
| ContainmentDrawsPlasmoidHeading | The containment will draw a titlebar-looking header for the applets, so the applets shouldn't attempt to paint a similar thing |
| ContainmentForcesSquarePlasmoids | The containment will force every plasmoid to be constrained in a square icon (An example is the System Tray) |
| ContainmentPrefersOpaqueBackground | The containment prefers the style of the applets to be opaque, where applicable |
| ContainmentPrefersFloatingApplets | The containment prefers applet's dialogs to be floating, where applicable |

### FormFactor : enumeration {#FormFactor-prop}

Describes how a Plasmoid should arrange itself.

The value is derived from the container managing the Applet (e.g. in Plasma, a Corona on the desktop or on a panel).

| Constant | Description |
| --- | --- |
| Planar | The applet lives in a plane and has two degrees of freedom to grow. Optimize for desktop, laptop or tablet usage: a high resolution screen 1-3 feet distant from the viewer. |
| MediaCenter | As with Planar, the applet lives in a plane but the interface should be optimized for medium-to-high resolution screens that are 5-15 feet distant from the viewer. Sometimes referred to as a "ten foot interface". |
| Horizontal | The applet is constrained vertically, but can expand horizontally. |
| Vertical | The applet is constrained horizontally, but can expand vertically. |
| Application | The Applet lives in a plane and should be optimized to look as a full application, for the desktop or the particular device. |

### ImmutabilityType : enumeration {#ImmutabilityType-prop}

Defines the immutability of items like plasmoids, corona and containments they can be free to modify, locked down by the user or locked down by the system (e.g. kiosk setups).

| Constant | Description |
| --- | --- |
| Mutable | The item can be modified in any way |
| UserImmutable | The user has requested a lock down, and can undo the lock down at any time |
| SystemImmutable | The item is locked down by the system, the user can't unlock it |

### ItemStatus : enumeration {#ItemStatus-prop}

Status of a plasmoid

| Constant | Description |
| --- | --- |
| UnknownStatus | The status is unknown |
| PassiveStatus | The item is passive |
| ActiveStatus | The item is active |
| NeedsAttentionStatus | The item needs attention |
| RequiresAttentionStatus | The item needs persistent attention |
| AcceptingInputStatus | The item is accepting input |
| HiddenStatus | The item will be hidden totally |

### Location : enumeration {#Location-prop}

Describes where on screen an element, such as a Plasmoid or its managing container, is positioned on the screen.

| Constant | Description |
| --- | --- |
| Floating | Free floating. Neither geometry or z-ordering is described precisely by this value. |
| Desktop | On the planar desktop layer, extending across the full screen from edge to edge. |
| FullScreen | Full screen |
| TopEdge | Along the top of the screen |
| BottomEdge | Along the bottom of the screen |
| LeftEdge | Along the left side of the screen |
| RightEdge | Along the right side of the screen |
