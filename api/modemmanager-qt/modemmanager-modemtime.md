---
title: "ModemManager::ModemTime Class"
description: "The ModemTime class."
---

# ModemManager::ModemTime Class

The [ModemTime](modemmanager-modemtime.md) class. [More...](#details)

- **Header:** `#include <ModemManagerQt/ModemTime>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS ModemManagerQt)`  
  `target_link_libraries(mytarget PRIVATE KF6::ModemManagerQt)`
- **Inherits:** [ModemManager::Interface](modemmanager-interface.md)

[List of all members, including inherited members](modemmanager-modemtime-members.md)

## Public Types

- [ModemTime::List](#List-typedef)
- [ModemTime::Ptr](#Ptr-typedef)

## Public Functions

- [ModemTime(const QString &path, QObject \*parent = nullptr)](#ModemTime)
- [QDBusPendingReply\<QString\> networkTime()](#networkTime)
- [ModemManager::NetworkTimezone networkTimezone() const](#networkTimezone)
- [void setTimeout(int timeout)](#setTimeout)
- [int timeout() const](#timeout)

## Signals

- [void networkTimeChanged(const QDateTime &dateTime)](#networkTimeChanged)
- [void networkTimezoneChanged(const ModemManager::NetworkTimezone &timeZone)](#networkTimezoneChanged)

## Detailed Description {#details}

This class allows clients to receive network time and timezone updates broadcast by mobile networks.

## Member Type Documentation {#member-type-documentation}

### ModemTime::List {#List-typedef}

### ModemTime::Ptr {#Ptr-typedef}

## Member Function Documentation {#member-function-documentation}

### \[explicit\] ModemTime::ModemTime(const QString &*path*, QObject \**parent* = nullptr) {#ModemTime}

### QDBusPendingReply\<QString\> ModemTime::networkTime() {#networkTime}

Returns the current network time in local time.

This method will only work if the modem tracks, or can request, the current network time; it will not attempt to use previously-received network time updates on the host to guess the current network time.

### \[signal\] void ModemTime::networkTimeChanged(const QDateTime &*dateTime*) {#networkTimeChanged}

Sent when the network time is updated.

`dateTime` the new date and time

### ModemManager::NetworkTimezone ModemTime::networkTimezone() const {#networkTimezone}

Returns the timezone data provided by the network.

*See also* [NetworkTimezone](modemmanager-networktimezone.md)

### \[signal\] void ModemTime::networkTimezoneChanged(const ModemManager::NetworkTimezone &*timeZone*) {#networkTimezoneChanged}

### void ModemTime::setTimeout(int *timeout*) {#setTimeout}

Sets the timeout in milliseconds for all async method DBus calls. -1 means the default DBus timeout (usually 25 seconds).

*See also* [timeout](modemmanager-modemtime.md#timeout)()

### int ModemTime::timeout() const {#timeout}

Returns the current value of the DBus timeout in milliseconds. -1 means the default DBus timeout (usually 25 seconds).

*See also* [setTimeout](modemmanager-modemtime.md#setTimeout)()
