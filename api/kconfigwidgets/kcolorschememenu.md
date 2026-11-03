---
title: "KColorSchemeMenu Namespace"
description: "A menu for switching color schemes."
---

# KColorSchemeMenu Namespace

A menu for switching color schemes. [More...](#details)

- Header: KColorSchemeMenu
- CMake: find\_package(KF6 REQUIRED COMPONENTS ConfigWidgets) target\_link\_libraries(mytarget PRIVATE KF6::ConfigWidgets)

## Detailed Description {#details}

## Function Documentation {#function-documentation}

### KActionMenu \*KColorSchemeMenu::createMenu(KColorSchemeManager \**manager*, QObject \**parent* = nullptr) {#createMenu}

Creates a [KActionMenu](../kwidgetsaddons/kactionmenu.md) populated with all the available color schemes. All actions are in an action group and when one of the actions is triggered the scheme referenced by this action is activated.
