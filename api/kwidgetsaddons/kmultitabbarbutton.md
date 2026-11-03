---
title: "KMultiTabBarButton Class"
description: "Use KMultiTabBar::appendButton to append a button, which creates a KMultiTabBarButton instance."
---

# KMultiTabBarButton Class

Use [KMultiTabBar::appendButton](kmultitabbar.md#appendButton) to append a button, which creates a [KMultiTabBarButton](kmultitabbarbutton.md) instance. [More...](#details)

- **Header:** `#include <KMultiTabBar>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS WidgetsAddons)`  
  `target_link_libraries(mytarget PRIVATE KF6::WidgetsAddons)`
- **Inherits:** [QPushButton](https://doc.qt.io/qt-6/qpushbutton.html)
- **Inherited By:** [KMultiTabBarTab](kmultitabbartab.md)

[List of all members, including inherited members](kmultitabbarbutton-members.md)

## Public Functions

- [int id() const](#id)

## Public Slots

- [void setText(const QString &text)](#setText)
- [void slotClicked()](#slotClicked)

## Signals

- [void clicked(int id)](#clicked)

## Protected Functions

- [KMultiTabBarButton(const QIcon &icon, const QString &, int id, QWidget \*parent)](#KMultiTabBarButton)

## Detailed Description {#details}

## Member Function Documentation {#member-function-documentation}

### \[protected\] KMultiTabBarButton::KMultiTabBarButton(const QIcon &*icon*, *const QString &*, int *id*, QWidget \**parent*) {#KMultiTabBarButton}

Should not be created directly. Use [KMultiTabBar::appendButton](kmultitabbar.md#appendButton)

### \[signal\] void KMultiTabBarButton::clicked(int *id*) {#clicked}

this is emitted if the button is clicked

`id` the ID identifying the button

### int KMultiTabBarButton::id() const {#id}

### \[slot\] void KMultiTabBarButton::setText(const QString &*text*) {#setText}

### \[virtual protected slot\] void KMultiTabBarButton::slotClicked() {#slotClicked}
