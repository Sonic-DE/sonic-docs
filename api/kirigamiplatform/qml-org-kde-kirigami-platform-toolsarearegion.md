---
title: "ToolsAreaRegion QML Type"
description: "Marks its area as part of the window's tools area, for blur behind it."
---

# ToolsAreaRegion QML Type

Marks its area as part of the window's tools area, for blur behind it. [More...](#details)

- Import Statement: import org.kde.kirigami.platform

## Detailed Description {#details}

Put one in the background of a toolbar or main menu bar. The window's tools area is the stack of visible regions that starts at the window's top edge, as Silver's toolsAreaRect spans the menu bar and top toolbars; a region below a gap isn't part of it. The tools area is set as the window's `_sonic_tools_area_region` property (a [QRegion](https://doc.qt.io/qt-6/qregion.html) in window coordinates), which the platform uses to blur behind it.

## Property Documentation {#property-documentation}

### \[read-only\] bottomOfToolsArea : bool {#bottomOfToolsArea-prop}

Whether this region is the lowest in its window's tools area, where the tools area separator is drawn.

### \[read-only\] inToolsArea : bool {#inToolsArea-prop}

Whether this region is part of its window's tools area.
