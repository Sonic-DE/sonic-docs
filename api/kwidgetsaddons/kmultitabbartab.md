---
title: "KMultiTabBarTab Class"
description: "Use KMultiTabBar::appendTab to append a tab, which creates a KMultiTabBarTab instance."
---

# KMultiTabBarTab Class

Use [KMultiTabBar::appendTab](kmultitabbar.md#appendTab) to append a tab, which creates a [KMultiTabBarTab](kmultitabbartab.md) instance. [More...](#details)

- **Header:** `#include <KMultiTabBar>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS WidgetsAddons)`  
  `target_link_libraries(mytarget PRIVATE KF6::WidgetsAddons)`
- **Inherits:** [KMultiTabBarButton](kmultitabbarbutton.md)

[List of all members, including inherited members](kmultitabbartab-members.md)

## Public Slots

- [void setPosition(KMultiTabBar::KMultiTabBarPosition)](#setPosition)
- [void setState(bool state)](#setState)
- [void setStyle(KMultiTabBar::KMultiTabBarStyle)](#setStyle)

## Detailed Description {#details}

## Member Function Documentation {#member-function-documentation}

### \[slot\] void KMultiTabBarTab::setPosition(*KMultiTabBar::KMultiTabBarPosition*) {#setPosition}

this is used internally, but can be used by the user, if (s)he wants to It the according call of [KMultiTabBar](kmultitabbar.md) is invoked though this modifications will be overwritten

### \[slot\] void KMultiTabBarTab::setState(bool *state*) {#setState}

set the active state of the tab

`state` true==active false==not active

### \[slot\] void KMultiTabBarTab::setStyle(*KMultiTabBar::KMultiTabBarStyle*) {#setStyle}

this is used internally, but can be used by the user, if (s)he wants to It the according call of [KMultiTabBar](kmultitabbar.md) is invoked though this modifications will be overwritten
