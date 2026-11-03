---
title: "BluezQt::Input Class"
description: "Device input."
---

# BluezQt::Input Class

Device input. [More...](#details)

- **Header:** `#include <BluezQt/Input>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS BluezQt)`  
  `target_link_libraries(mytarget PRIVATE KF6::BluezQt)`
- **Inherits:** [QObject](https://doc.qt.io/qt-6/qobject.html)

[List of all members, including inherited members](bluezqt-input-members.md)

## Public Types

- [enum Input::ReconnectMode](#ReconnectMode-enum)

## Properties

- [\[read-only\] reconnectMode : ReconnectMode](#reconnectMode-prop)

## Public Functions

- [BluezQt::Input::ReconnectMode reconnectMode() const](#reconnectMode)
- [BluezQt::InputPtr toSharedPtr() const](#toSharedPtr)

## Signals

- [void reconnectModeChanged(BluezQt::Input::ReconnectMode mode)](#reconnectModeChanged)

## Detailed Description {#details}

This class represents an input interface.

## Member Type Documentation {#member-type-documentation}

### enum Input::ReconnectMode {#ReconnectMode-enum}

| Constant | Value | Description |
| --- | --- | --- |
| `BluezQt::Input::NoReconnect` | `0` | Device and host are not required to automatically restore the connection. |
| `BluezQt::Input::HostReconnect` | `1` | Host restores the connection. |
| `BluezQt::Input::DeviceReconnect` | `2` | Device restores the connection |
| `BluezQt::Input::AnyReconnect` | `3` | Device shall attempt to restore the lost connection, but host may also restore the connection. |

## Property Documentation {#property-documentation}

### \[read-only\] reconnectMode : ReconnectMode {#reconnectMode-prop}

**Access functions:**

- `BluezQt::Input::ReconnectMode` **[reconnectMode](bluezqt-input.md#reconnectMode)**() const

**Notifier signal:**

- `void` **[reconnectModeChanged](bluezqt-input.md#reconnectModeChanged)**(`BluezQt::Input::ReconnectMode` *mode*)

## Member Function Documentation {#member-function-documentation}

### BluezQt::Input::ReconnectMode Input::reconnectMode() const {#reconnectMode}

Returns the reconnect mode.

> **Note:** Getter function for property [reconnectMode](bluezqt-input.md#reconnectMode-prop).

### \[signal\] void Input::reconnectModeChanged(BluezQt::Input::ReconnectMode *mode*) {#reconnectModeChanged}

Indicates that the input's reconnect `mode` has changed.

> **Note:** Notifier signal for property [reconnectMode](bluezqt-input.md#reconnectMode-prop).

### BluezQt::InputPtr Input::toSharedPtr() const {#toSharedPtr}

Returns a shared pointer from this.
