---
title: "ToolsAreaBackground QML Type"
description: "The background of a toolbar or main menu bar, joining the window's tools area when it is part of the stack of bars at the window's top."
---

# ToolsAreaBackground QML Type

The background of a toolbar or main menu bar, joining the window's tools area when it is part of the stack of bars at the window's top. [More...](#details)

- Import Statement: import org.kde.kirigami.primitives
- Inherits: [Rectangle](https://doc.qt.io/qt-6/qml-qtquick-rectangle.html)

## Detailed Description {#details}

When the theme uses a tools area (Theme.toolsArea.active) and the bar is in it, it draws the tools area background (translucent with blur behind if the theme says so, opaque in a maximized window when asked), and only the lowest bar draws the separator, in the tools area separator color. Otherwise it is the inherited color set's background with the usual separator, as bars have always looked (set the Header color set on the bar, as headers do). Only the bar's background: controls on the bar keep their own styling. Everything follows the theme live.

## Property Documentation {#property-documentation}

### \[read-only\] inToolsArea : bool {#inToolsArea-prop}

Whether the bar is drawn as part of the window's tools area.

### \[read-only\] separator : Item {#separator-prop}

The separator item (for paddings that make room for it).

### separatorEdge : int {#separatorEdge-prop}

The edge the separator is drawn along outside the tools area: Qt.BottomEdge (default) or Qt.TopEdge. In the tools area it is always the bottom.

### separatorVisible : bool {#separatorVisible-prop}

Whether to draw the separator.

### toolsAreaCandidate : bool {#toolsAreaCandidate-prop}

Whether the bar may join the tools area (false for footers, for example).
