---
title: "KParts::PartActivateEvent Class"
description: "This event is sent by the part manager when the active part changes."
---

# KParts::PartActivateEvent Class

This event is sent by the part manager when the active part changes. [More...](#details)

- **Header:** `#include <KParts/PartActivateEvent>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS Parts)`  
  `target_link_libraries(mytarget PRIVATE KF6::Parts)`
- **Inherits:** [QEvent](https://doc.qt.io/qt-6/qevent.html)

[List of all members, including inherited members](kparts-partactivateevent-members.md)

## Public Functions

- [PartActivateEvent(bool activated, KParts::Part \*part, QWidget \*widget)](#PartActivateEvent)
- [bool activated() const](#activated)
- [KParts::Part \*part() const](#part)
- [QWidget \*widget() const](#widget)

## Static Public Members

- [bool test(const QEvent \*event)](#test)

## Detailed Description {#details}

Each time the active part changes, it will send first a [PartActivateEvent](kparts-partactivateevent.md) with activated=false, part=oldActivePart, widget=oldActiveWidget and then another [PartActivateEvent](kparts-partactivateevent.md) with activated=true, part=newPart, widget=newWidget.

*See also* [KParts::Part::partActivateEvent](kparts-index.md)

## Member Function Documentation {#member-function-documentation}

### PartActivateEvent::PartActivateEvent(bool *activated*, KParts::Part \**part*, QWidget \**widget*) {#PartActivateEvent}

### bool PartActivateEvent::activated() const {#activated}

### KParts::Part \*PartActivateEvent::part() const {#part}

### \[static\] bool PartActivateEvent::test(const QEvent \**event*) {#test}

### QWidget \*PartActivateEvent::widget() const {#widget}
