---
title: "NetworkManager::DeviceStatistics Class"
description: "Represents device statistics interface."
---

# NetworkManager::DeviceStatistics Class

Represents device statistics interface. [More...](#details)

- **Header:** `#include <NetworkManagerQt/DeviceStatistics>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS NetworkManagerQt)`  
  `target_link_libraries(mytarget PRIVATE KF6::NetworkManagerQt)`
- **Inherits:** [QObject](https://doc.qt.io/qt-6/qobject.html)

[List of all members, including inherited members](networkmanager-devicestatistics-members.md)

## Public Types

- [DeviceStatistics::List](#List-typedef)
- [DeviceStatistics::Ptr](#Ptr-typedef)

## Properties

- [refreshRateMs : uint](#refreshRateMs-prop)
- [\[read-only\] rxBytes : qulonglong](#rxBytes-prop)
- [\[read-only\] txBytes : qulonglong](#txBytes-prop)

## Public Functions

- [DeviceStatistics(const QString &path, QObject \*parent = nullptr)](#DeviceStatistics)
- [uint refreshRateMs() const](#refreshRateMs)
- [qulonglong rxBytes() const](#rxBytes)
- [void setRefreshRateMs(uint refreshRate)](#setRefreshRateMs)
- [qulonglong txBytes() const](#txBytes)

## Signals

- [void refreshRateMsChanged(uint refreshRate)](#refreshRateMsChanged)
- [void rxBytesChanged(qulonglong rxBytes)](#rxBytesChanged)
- [void txBytesChanged(qulonglong txBytes)](#txBytesChanged)

## Detailed Description {#details}

## Member Type Documentation {#member-type-documentation}

### DeviceStatistics::List {#List-typedef}

### DeviceStatistics::Ptr {#Ptr-typedef}

## Property Documentation {#property-documentation}

### refreshRateMs : uint {#refreshRateMs-prop}

**Access functions:**

- `uint` **[refreshRateMs](networkmanager-devicestatistics.md#refreshRateMs)**() const
- `void` **[setRefreshRateMs](networkmanager-devicestatistics.md#setRefreshRateMs)**(`uint` *refreshRate*)

**Notifier signal:**

- `void` **[refreshRateMsChanged](networkmanager-devicestatistics.md#refreshRateMsChanged)**(`uint` *refreshRate*)

### \[read-only\] rxBytes : qulonglong {#rxBytes-prop}

**Access functions:**

- `qulonglong` **[rxBytes](networkmanager-devicestatistics.md#rxBytes)**() const

**Notifier signal:**

- `void` **[rxBytesChanged](networkmanager-devicestatistics.md#rxBytesChanged)**(`qulonglong` *rxBytes*)

### \[read-only\] txBytes : qulonglong {#txBytes-prop}

**Access functions:**

- `qulonglong` **[txBytes](networkmanager-devicestatistics.md#txBytes)**() const

**Notifier signal:**

- `void` **[txBytesChanged](networkmanager-devicestatistics.md#txBytesChanged)**(`qulonglong` *txBytes*)

## Member Function Documentation {#member-function-documentation}

### \[explicit\] DeviceStatistics::DeviceStatistics(const QString &*path*, QObject \**parent* = nullptr) {#DeviceStatistics}

### uint DeviceStatistics::refreshRateMs() const {#refreshRateMs}

Refresh rate of the rest of properties of this interface. The properties are guaranteed to be refreshed each RefreshRateMs milliseconds in case the underlying counter has changed too. If zero, there is no guaranteed refresh rate of the properties.

> **Note:** Getter function for property [refreshRateMs](networkmanager-devicestatistics.md#refreshRateMs-prop).

*See also* [setRefreshRateMs](networkmanager-devicestatistics.md#setRefreshRateMs)()

### \[signal\] void DeviceStatistics::refreshRateMsChanged(uint *refreshRate*) {#refreshRateMsChanged}

Emitted when the refresh rate has changed

> **Note:** Notifier signal for property [refreshRateMs](networkmanager-devicestatistics.md#refreshRateMs-prop).

### qulonglong DeviceStatistics::rxBytes() const {#rxBytes}

Number of received bytes

> **Note:** Getter function for property [rxBytes](networkmanager-devicestatistics.md#rxBytes-prop).

### \[signal\] void DeviceStatistics::rxBytesChanged(qulonglong *rxBytes*) {#rxBytesChanged}

Emitted when the received bytes has changed

> **Note:** Notifier signal for property [rxBytes](networkmanager-devicestatistics.md#rxBytes-prop).

### void DeviceStatistics::setRefreshRateMs(uint *refreshRate*) {#setRefreshRateMs}

> **Note:** Setter function for property [refreshRateMs](networkmanager-devicestatistics.md#refreshRateMs-prop).

*See also* [refreshRateMs](networkmanager-devicestatistics.md#refreshRateMs)()

### qulonglong DeviceStatistics::txBytes() const {#txBytes}

Number of transmitted bytes

> **Note:** Getter function for property [txBytes](networkmanager-devicestatistics.md#txBytes-prop).

### \[signal\] void DeviceStatistics::txBytesChanged(qulonglong *txBytes*) {#txBytesChanged}

Emitted when the transmitted bytes has changed

> **Note:** Notifier signal for property [txBytes](networkmanager-devicestatistics.md#txBytes-prop).
