---
title: "KToolBarSpacerAction Class"
description: "An extension to QAction which allows for adding a spacer item into a QToolBar / KToolBar."
---

# KToolBarSpacerAction Class

An extension to [QAction](https://doc.qt.io/qt-6/qaction.html) which allows for adding a spacer item into a [QToolBar](https://doc.qt.io/qt-6/qtoolbar.html) / KToolBar. [More...](#details)

- **Header:** `#include <KToolBarSpacerAction>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS WidgetsAddons)`  
  `target_link_libraries(mytarget PRIVATE KF6::WidgetsAddons)`
- **Inherits:** [QWidgetAction](https://doc.qt.io/qt-6/qwidgetaction.html)

[List of all members, including inherited members](ktoolbarspaceraction-members.md)

## Public Functions

- [KToolBarSpacerAction(QObject \*parent)](#KToolBarSpacerAction)

## Detailed Description {#details}

This is useful if you want to align at the right (or left if RTL) and need something that pushes the element to the end of the tool bar.

## Member Function Documentation {#member-function-documentation}

### \[explicit\] KToolBarSpacerAction::KToolBarSpacerAction(QObject \**parent*) {#KToolBarSpacerAction}

Creates a new toolbar spacer action.

`parent` The action's parent object.
