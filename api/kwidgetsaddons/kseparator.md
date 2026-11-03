---
title: "KSeparator Class"
description: "Standard horizontal or vertical separator."
---

# KSeparator Class

Standard horizontal or vertical separator. [More...](#details)

- **Header:** `#include <KSeparator>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS WidgetsAddons)`  
  `target_link_libraries(mytarget PRIVATE KF6::WidgetsAddons)`
- **Inherits:** [QFrame](https://doc.qt.io/qt-6/qframe.html)

[List of all members, including inherited members](kseparator-members.md)

## Properties

- [orientation : Qt::Orientation](#orientation-prop)

## Public Functions

- [KSeparator(QWidget \*parent = nullptr, Qt::WindowFlags f = WindowFlags())](#KSeparator)
- [KSeparator(Qt::Orientation orientation, QWidget \*parent = nullptr, Qt::WindowFlags f = WindowFlags())](#KSeparator-1)
- [Qt::Orientation orientation() const](#orientation)
- [void setOrientation(Qt::Orientation orientation)](#setOrientation)

## Detailed Description {#details}

## Property Documentation {#property-documentation}

### orientation : Qt::Orientation {#orientation-prop}

**Access functions:**

- `Qt::Orientation` **[orientation](kseparator.md#orientation)**() const
- `void` **[setOrientation](kseparator.md#setOrientation)**(`Qt::Orientation` *orientation*)

## Member Function Documentation {#member-function-documentation}

### \[explicit\] KSeparator::KSeparator(QWidget \**parent* = nullptr, Qt::WindowFlags *f* = Qt::WindowFlags()) {#KSeparator}

Constructor.

`parent` parent object.

`f` extra [QWidget](https://doc.qt.io/qt-6/qwidget.html) flags.

### \[explicit\] KSeparator::KSeparator(Qt::Orientation *orientation*, QWidget \**parent* = nullptr, Qt::WindowFlags *f* = Qt::WindowFlags()) {#KSeparator-1}

Constructor.

`orientation` Set the orientation of the separator. Possible values are Horizontal or Vertical.

`parent` parent object.

`f` extra [QWidget](https://doc.qt.io/qt-6/qwidget.html) flags.

### Qt::Orientation KSeparator::orientation() const {#orientation}

Returns the orientation of the separator.

> **Note:** Getter function for property [orientation](kseparator.md#orientation-prop).

*See also* [setOrientation](kseparator.md#setOrientation)()

### void KSeparator::setOrientation(Qt::Orientation *orientation*) {#setOrientation}

Set the orientation of the separator to `orientation`

`orientation` Possible values are Vertical and Horizontal.

> **Note:** Setter function for property [orientation](kseparator.md#orientation-prop).

*See also* [orientation](kseparator.md#orientation)()
