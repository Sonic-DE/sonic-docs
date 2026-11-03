---
title: "KToggleFullScreenAction Class"
description: "An action for switching between to/from full screen mode."
---

# KToggleFullScreenAction Class

An action for switching between to/from full screen mode. [More...](#details)

- **Header:** `#include <KToggleFullScreenAction>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS WidgetsAddons)`  
  `target_link_libraries(mytarget PRIVATE KF6::WidgetsAddons)`
- **Inherits:** [KToggleAction](ktoggleaction.md)

[List of all members, including inherited members](ktogglefullscreenaction-members.md)

## Public Functions

- [KToggleFullScreenAction(QObject \*parent)](#KToggleFullScreenAction)
- [KToggleFullScreenAction(QWidget \*window, QObject \*parent)](#KToggleFullScreenAction-1)
- [void setWindow(QWidget \*window)](#setWindow)

## Static Public Members

- [void setFullScreen(QWidget \*window, bool set)](#setFullScreen)

## Detailed Description {#details}

Note that [QWidget::isFullScreen](https://doc.qt.io/qt-6/qwidget.html#fullScreen-prop)() may reflect the new or the old state depending on how the action was triggered (by the application or from the window manager). Also don't try to track the window state yourself. Rely on this action's state ([isChecked](https://doc.qt.io/qt-6/qaction.html#checked-prop)()) instead.

Important: If you need to set/change the fullscreen state manually, use [KToggleFullScreenAction::setFullScreen](ktogglefullscreenaction.md#setFullScreen)() or a similar function, do not call directly the slot connected to the [toggled](https://doc.qt.io/qt-6/qaction.html#toggled)() signal. The slot still needs to explicitly set the window state though.

> **Note:** Do NOT use [QWidget::showFullScreen](https://doc.qt.io/qt-6/qwidget.html#showFullScreen)() or [QWidget::showNormal](https://doc.qt.io/qt-6/qwidget.html#showNormal)(). They have several side-effects besides just switching the fullscreen state (for example, showNormal() resets all window states, not just fullscreen). Use the [KToggleFullScreenAction::setFullScreen](ktogglefullscreenaction.md#setFullScreen)() helper function.

## Member Function Documentation {#member-function-documentation}

### \[explicit\] KToggleFullScreenAction::KToggleFullScreenAction(QObject \**parent*) {#KToggleFullScreenAction}

Create a [KToggleFullScreenAction](ktogglefullscreenaction.md). Call [setWindow](ktogglefullscreenaction.md#setWindow)() to associate this action with a window.

`parent` This action's parent object.

### KToggleFullScreenAction::KToggleFullScreenAction(QWidget \**window*, QObject \**parent*) {#KToggleFullScreenAction-1}

Create a [KToggleFullScreenAction](ktogglefullscreenaction.md)

`window` the window that will switch to/from full screen mode

`parent` This action's parent object.

### \[static\] void KToggleFullScreenAction::setFullScreen(QWidget \**window*, bool *set*) {#setFullScreen}

Helper function to set or reset the fullscreen state of a window.

Use this function rather than showFullScreen()/showNormal() [QWidget](https://doc.qt.io/qt-6/qwidget.html) functions.

### void KToggleFullScreenAction::setWindow(QWidget \**window*) {#setWindow}

Sets the window that will be related to this action.
