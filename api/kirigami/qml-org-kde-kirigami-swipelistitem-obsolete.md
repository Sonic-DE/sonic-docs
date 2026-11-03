---
title: "Obsolete Members for SwipeListItem"
description: "Deprecated members of SwipeListItem QML Type."
parent: "kirigami/qml-org-kde-kirigami-swipelistitem"
---

# Obsolete Members for SwipeListItem

**The following members of QML type [SwipeListItem](qml-org-kde-kirigami-swipelistitem.md) are deprecated.** We strongly advise against using them in new code.

## Properties

- [\[read-only, deprecated\] containsMouse : bool](#containsMouse-prop)
- [\[default: true, deprecated\] supportsMouseEvents : bool](#supportsMouseEvents-prop)

## Obsolete Property Documentation {#obsolete-property-documentation}

### \[read-only, deprecated\] containsMouse : bool {#containsMouse-prop}

This property is deprecated. We strongly advise against using it in new code.

This property tells whether the cursor is currently hovering over the item.

On mobile touch devices, this will be true only when pressed.

use the hovered property instead.

*See also* [ItemDelegate::hovered](https://doc.qt.io/qt-6/qml-qtquick-controls-control.html#hovered-prop)

### \[default: true, deprecated\] supportsMouseEvents : bool {#supportsMouseEvents-prop}

This property is deprecated. We strongly advise against using it in new code.

This property sets whether the item should emit signals related to mouse interaction.

Use hoverEnabled instead.
