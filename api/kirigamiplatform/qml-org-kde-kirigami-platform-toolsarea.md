---
title: "ToolsArea QML Type"
description: "How the window's tools area is drawn: the toolbars and main menu bar at the top of a window, under the title bar."
---

# ToolsArea QML Type

How the window's tools area is drawn: the toolbars and main menu bar at the top of a window, under the title bar. [More...](#details)

- Import Statement: import org.kde.kirigami.platform

## Detailed Description {#details}

Reached as `Theme.toolsArea`. The platform plugin fills it; the backgrounds of toolbars and main menu bars in the window header use it, together with the Header color set. Controls on those bars are not affected.

## Property Documentation {#property-documentation}

### \[read-only\] active : bool {#active-prop}

Whether the theme uses a tools area. While false, bars look as they always have.

### \[read-only\] backgroundColor : color {#backgroundColor-prop}

The tools area background in an active window (may be translucent); invalid when the platform gives none, in which case the Header color set's background is used.

### \[read-only\] blurBehind : bool {#blurBehind-prop}

Whether a translucent tools area background blurs what is behind the window.

### \[read-only\] inactiveBackgroundColor : color {#inactiveBackgroundColor-prop}

The tools area background in an inactive window; invalid when the platform gives none.

### \[read-only\] opaqueWhenMaximized : bool {#opaqueWhenMaximized-prop}

Whether the tools area background is drawn opaque in a maximized or full screen window.

### \[read-only\] separatorColor : color {#separatorColor-prop}

The color of the line under the tools area; invalid when the platform gives none, in which case the usual Separator color is used.

### \[read-only\] titleBarHidden : bool {#titleBarHidden-prop}

Whether the window decoration hides the title bar above the tools area.

### \[read-only\] translucent : bool {#translucent-prop}

Whether windows are created with an alpha channel so a translucent tools area shows what is behind the window. Application windows then paint their background only outside the tools area ([ToolsAreaWindowBackground](qml-org-kde-kirigami-platform-toolsareawindowbackground.md)).
