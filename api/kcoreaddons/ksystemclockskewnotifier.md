---
title: "KSystemClockSkewNotifier Class"
description: "The KSystemClockSkewNotifier class provides a way for monitoring system clock changes. This class was introduced in Qt 6.15."
---

# KSystemClockSkewNotifier Class

The [KSystemClockSkewNotifier](ksystemclockskewnotifier.md) class provides a way for monitoring system clock changes. This class was introduced in Qt 6.15. [More...](#details)

- **Header:** `#include <KSystemClockSkewNotifier>`
- **Since:** Qt 6.15
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS CoreAddons)`  
  `target_link_libraries(mytarget PRIVATE KF6::CoreAddons)`
- **Inherits:** [QObject](https://doc.qt.io/qt-6/qobject.html)

[List of all members, including inherited members](ksystemclockskewnotifier-members.md)

## Public Functions

- [bool isActive() const](#isActive)
- [void setActive(bool active)](#setActive)

## Signals

- [void activeChanged()](#activeChanged)
- [void skewed()](#skewed)

## Detailed Description {#details}

The [KSystemClockSkewNotifier](ksystemclockskewnotifier.md) class makes it possible to detect discontinuous changes to the system clock. Such changes are usually initiated by the user adjusting values in the Date and Time KCM or calls made to functions like settimeofday().

## Member Function Documentation {#member-function-documentation}

### \[signal\] void KSystemClockSkewNotifier::activeChanged() {#activeChanged}

This signal is emitted whenever the active property is changed.

> **Note:** Notifier signal for property active.

### bool KSystemClockSkewNotifier::isActive() const {#isActive}

Returns true if the notifier is active; otherwise returns false.

> **Note:** Getter function for property active.

### void KSystemClockSkewNotifier::setActive(bool *active*) {#setActive}

Sets the active status of the clock skew notifier to `active`.

The [skewed](ksystemclockskewnotifier.md#skewed)() signal won't be emitted while the notifier is inactive.

The notifier is inactive by default.

> **Note:** Setter function for property active.

*See also* [isActive](ksystemclockskewnotifier.md#isActive)(), [activeChanged](ksystemclockskewnotifier.md#activeChanged)()

### \[signal\] void KSystemClockSkewNotifier::skewed() {#skewed}

This signal is emitted whenever the system clock is changed.
