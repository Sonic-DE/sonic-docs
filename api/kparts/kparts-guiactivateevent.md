---
title: "KParts::GUIActivateEvent Class"
description: "This event is sent to a Part when its GUI has been activated or deactivated."
---

# KParts::GUIActivateEvent Class

This event is sent to a Part when its GUI has been activated or deactivated. [More...](#details)

- **Header:** `#include <KParts/GUIActivateEvent>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS Parts)`  
  `target_link_libraries(mytarget PRIVATE KF6::Parts)`
- **Inherits:** [QEvent](https://doc.qt.io/qt-6/qevent.html)

[List of all members, including inherited members](kparts-guiactivateevent-members.md)

## Public Functions

- [GUIActivateEvent(bool activated)](#GUIActivateEvent)
- [bool activated() const](#activated)

## Static Public Members

- [bool test(const QEvent \*event)](#test)

## Detailed Description {#details}

This is related to [PartActivateEvent](kparts-partactivateevent.md), but the difference is that [GUIActivateEvent](kparts-guiactivateevent.md) happens later (when the GUI is actually built), only for parts that have GUI elements, and only if using [KParts::MainWindow](kparts-mainwindow.md).

*See also* [KParts::Part::guiActivateEvent()](kparts-index.md)

## Member Function Documentation {#member-function-documentation}

### GUIActivateEvent::GUIActivateEvent(bool *activated*) {#GUIActivateEvent}

### bool GUIActivateEvent::activated() const {#activated}

### \[static\] bool GUIActivateEvent::test(const QEvent \**event*) {#test}
