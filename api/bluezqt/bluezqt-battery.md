---
title: "BluezQt::Battery Class"
description: "Device battery."
---

# BluezQt::Battery Class

Device battery. [More...](#details)

- **Header:** `#include <BluezQt/Battery>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS BluezQt)`  
  `target_link_libraries(mytarget PRIVATE KF6::BluezQt)`
- **Inherits:** [QObject](https://doc.qt.io/qt-6/qobject.html)

[List of all members, including inherited members](bluezqt-battery-members.md)

## Properties

- [\[read-only\] percentage : int](#percentage-prop)

## Public Functions

- [int percentage() const](#percentage)
- [BluezQt::BatteryPtr toSharedPtr() const](#toSharedPtr)

## Signals

- [void percentageChanged(int percentage)](#percentageChanged)

## Detailed Description {#details}

This class represents a battery interface.

## Property Documentation {#property-documentation}

### \[read-only\] percentage : int {#percentage-prop}

**Access functions:**

- `int` **[percentage](bluezqt-battery.md#percentage)**() const

**Notifier signal:**

- `void` **[percentageChanged](bluezqt-battery.md#percentageChanged)**(`int` *percentage*)

## Member Function Documentation {#member-function-documentation}

### int Battery::percentage() const {#percentage}

Returns the battery percentage.

> **Note:** Getter function for property [percentage](bluezqt-battery.md#percentage-prop).

### \[signal\] void Battery::percentageChanged(int *percentage*) {#percentageChanged}

Indicates that battery's `percentage` has changed.

> **Note:** Notifier signal for property [percentage](bluezqt-battery.md#percentage-prop).

### BluezQt::BatteryPtr Battery::toSharedPtr() const {#toSharedPtr}

Returns a shared pointer from this.
