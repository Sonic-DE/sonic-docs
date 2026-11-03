---
title: "BluezQt::Rfkill Class"
description: "Qt wrapper for BlueZ 5 DBus API."
---

# BluezQt::Rfkill Class

Qt wrapper for BlueZ 5 DBus API. [More...](#details)

- **Header:** `#include <BluezQt/Rfkill>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS BluezQt)`  
  `target_link_libraries(mytarget PRIVATE KF6::BluezQt)`
- **Inherits:** [QObject](https://doc.qt.io/qt-6/qobject.html)

[List of all members, including inherited members](bluezqt-rfkill-members.md)

## Public Types

- [enum Rfkill::State](#State-enum)

## Properties

- [\[read-only\] state : State](#state-prop)

## Public Functions

- [Rfkill(QObject \*parent = nullptr)](#Rfkill)
- [void block()](#block)
- [BluezQt::Rfkill::State state() const](#state)
- [void unblock()](#unblock)

## Signals

- [void stateChanged(BluezQt::Rfkill::State state)](#stateChanged)

## Detailed Description {#details}

## Member Type Documentation {#member-type-documentation}

### enum Rfkill::State {#State-enum}

| Constant |   |
| --- | --- |
| `BluezQt::Rfkill::Unblocked` | `0` |
| `BluezQt::Rfkill::SoftBlocked` | `1` |
| `BluezQt::Rfkill::HardBlocked` | `2` |
| `BluezQt::Rfkill::Unknown` | `3` |

## Property Documentation {#property-documentation}

### \[read-only\] state : State {#state-prop}

**Access functions:**

- `BluezQt::Rfkill::State` **[state](bluezqt-rfkill.md#state)**() const

**Notifier signal:**

- `void` **[stateChanged](bluezqt-rfkill.md#stateChanged)**(`BluezQt::Rfkill::State` *state*)

## Member Function Documentation {#member-function-documentation}

### \[explicit\] Rfkill::Rfkill(QObject \**parent* = nullptr) {#Rfkill}

### void Rfkill::block() {#block}

### BluezQt::Rfkill::State Rfkill::state() const {#state}

> **Note:** Getter function for property [state](bluezqt-rfkill.md#state-prop).

### \[signal\] void Rfkill::stateChanged(BluezQt::Rfkill::State *state*) {#stateChanged}

> **Note:** Notifier signal for property [state](bluezqt-rfkill.md#state-prop).

### void Rfkill::unblock() {#unblock}
