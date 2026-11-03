---
title: "KMultiTabBar Class"
description: "A Widget for horizontal and vertical tabs. (Note that in Qt4, QTabBar can be vertical as well)."
---

# KMultiTabBar Class

A Widget for horizontal and vertical tabs. (Note that in Qt4, [QTabBar](https://doc.qt.io/qt-6/qtabbar.html) can be vertical as well). [More...](#details)

- **Header:** `#include <KMultiTabBar>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS WidgetsAddons)`  
  `target_link_libraries(mytarget PRIVATE KF6::WidgetsAddons)`
- **Inherits:** [QWidget](https://doc.qt.io/qt-6/qwidget.html)

[List of all members, including inherited members](kmultitabbar-members.md)

## Public Types

- [enum KMultiTabBar::KMultiTabBarPosition](#KMultiTabBarPosition-enum)
- [enum KMultiTabBar::KMultiTabBarStyle](#KMultiTabBarStyle-enum)

## Properties

- [position : KMultiTabBarPosition](#position-prop)

## Public Functions

- [KMultiTabBar(QWidget \*parent = nullptr)](#KMultiTabBar)
- [KMultiTabBar(KMultiTabBar::KMultiTabBarPosition pos, QWidget \*parent = nullptr)](#KMultiTabBar-1)
- [int appendButton(const QIcon &icon, int id = -1, QMenu \*popup = nullptr, const QString &not\_used\_yet = QString())](#appendButton)
- [int appendTab(const QIcon &icon, int id = -1, const QString &text = QString())](#appendTab)
- [bool isTabRaised(int id) const](#isTabRaised)
- [KMultiTabBar::KMultiTabBarPosition position() const](#position)
- [void removeButton(int id)](#removeButton)
- [void removeTab(int id)](#removeTab)
- [void setPosition(KMultiTabBar::KMultiTabBarPosition pos)](#setPosition)
- [void setStyle(KMultiTabBar::KMultiTabBarStyle style)](#setStyle)
- [void setTab(int id, bool state)](#setTab)
- [KMultiTabBar::KMultiTabBarStyle tabStyle() const](#tabStyle)

## Detailed Description {#details}

It is possible to add normal buttons to the top/left The handling if only one tab at a time or multiple tabs should be raisable is left to the "user".

*\[Missing image kmultitabbar.png\]*

## Member Type Documentation {#member-type-documentation}

### enum KMultiTabBar::KMultiTabBarPosition {#KMultiTabBarPosition-enum}

| Constant |   |
| --- | --- |
| `KMultiTabBar::Left` | `0` |
| `KMultiTabBar::Right` | `1` |
| `KMultiTabBar::Top` | `2` |
| `KMultiTabBar::Bottom` | `3` |

### enum KMultiTabBar::KMultiTabBarStyle {#KMultiTabBarStyle-enum}

The list of available styles for [KMultiTabBar](kmultitabbar.md)

| Constant | Value | Description |
| --- | --- | --- |
| `KMultiTabBar::VSNET` | `0` | Visual Studio .Net like, always shows icon, only show the text of active tabs |
| `KMultiTabBar::KDEV3ICON` | `2` | KDevelop 3 like, always shows the text and icons |

## Property Documentation {#property-documentation}

### position : KMultiTabBarPosition {#position-prop}

**Access functions:**

- `KMultiTabBar::KMultiTabBarPosition` **[position](kmultitabbar.md#position)**() const
- `void` **[setPosition](kmultitabbar.md#setPosition)**(`KMultiTabBar::KMultiTabBarPosition` *pos*)

## Member Function Documentation {#member-function-documentation}

### \[explicit\] KMultiTabBar::KMultiTabBar(QWidget \**parent* = nullptr) {#KMultiTabBar}

Create a [KMultiTabBar](kmultitabbar.md) with Left as [KMultiTabBar](kmultitabbar.md) position.

`parent` The parent of the widget.

### \[explicit\] KMultiTabBar::KMultiTabBar(KMultiTabBar::KMultiTabBarPosition *pos*, QWidget \**parent* = nullptr) {#KMultiTabBar-1}

### int KMultiTabBar::appendButton(const QIcon &*icon*, int *id* = -1, QMenu \**popup* = nullptr, const QString &*not\_used\_yet* = QString()) {#appendButton}

append a new button to the button area. The button can later on be accessed with button(ID) eg for connecting signals to it

`icon` a icon for the button

`id` an arbitrary ID value. It will be emitted in the clicked signal for identifying the button if more than one button is connected to a signals.

`popup` A popup menu which should be displayed if the button is clicked

`not_used_yet` will be used for a popup text in the future

### int KMultiTabBar::appendTab(const QIcon &*icon*, int *id* = -1, const QString &*text* = QString()) {#appendTab}

append a new tab to the tab area. It can be accessed lateron with tabb(id);

`icon` a icon for the tab

`id` an arbitrary ID which can be used later on to identify the tab

`text` if a mode with text is used it will be the tab text, otherwise a mouse over hint

### bool KMultiTabBar::isTabRaised(int *id*) const {#isTabRaised}

return the state of a tab, identified by its ID

### KMultiTabBar::KMultiTabBarPosition KMultiTabBar::position() const {#position}

Returns the tabbar position.

> **Note:** Getter function for property [position](kmultitabbar.md#position-prop).

*See also* [setPosition](kmultitabbar.md#setPosition)()

### void KMultiTabBar::removeButton(int *id*) {#removeButton}

remove a button with the given ID

### void KMultiTabBar::removeTab(int *id*) {#removeTab}

remove a tab with a given ID

### void KMultiTabBar::setPosition(KMultiTabBar::KMultiTabBarPosition *pos*) {#setPosition}

set the real position of the widget.

`pos` if the mode is horizontal, only use top, bottom, if it is vertical use left or right

> **Note:** Setter function for property [position](kmultitabbar.md#position-prop).

*See also* [position](kmultitabbar.md#position)()

### void KMultiTabBar::setStyle(KMultiTabBar::KMultiTabBarStyle *style*) {#setStyle}

set the display style of the tabs

> **Note:** Setter function for property tabStyle.

### void KMultiTabBar::setTab(int *id*, bool *state*) {#setTab}

set a tab to "raised"

`id` The ID of the tab to manipulate

`state` true == activated/raised, false == not active

### KMultiTabBar::KMultiTabBarStyle KMultiTabBar::tabStyle() const {#tabStyle}

Returns the display style of the tabs

> **Note:** Getter function for property tabStyle.
