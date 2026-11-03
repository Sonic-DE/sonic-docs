---
title: "ModemManager::NetworkTimezone Class"
description: "This class represents the timezone data provided by the network."
---

# ModemManager::NetworkTimezone Class

This class represents the timezone data provided by the network. [More...](#details)

- **Header:** `#include <ModemManagerQt/ModemTime>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS ModemManagerQt)`  
  `target_link_libraries(mytarget PRIVATE KF6::ModemManagerQt)`

[List of all members, including inherited members](modemmanager-networktimezone-members.md)

## Public Functions

- [NetworkTimezone()](#NetworkTimezone)
- [NetworkTimezone(const ModemManager::NetworkTimezone &other)](#NetworkTimezone-1)
- [~NetworkTimezone()](#dtor.NetworkTimezone)
- [int dstOffset() const](#dstOffset)
- [int leapSecond() const](#leapSecond)
- [int offset() const](#offset)
- [void setDstOffset(int dstOffset)](#setDstOffset)
- [void setLeapSecond(int leapSecond)](#setLeapSecond)
- [void setOffset(int offset)](#setOffset)
- [ModemManager::NetworkTimezone &NetworkTimezone::operator=(const ModemManager::NetworkTimezone &other)](#operator-eq)

## Detailed Description {#details}

## Member Function Documentation {#member-function-documentation}

### NetworkTimezone::NetworkTimezone() {#NetworkTimezone}

Constructs an empty timezone data object

### NetworkTimezone::NetworkTimezone(const ModemManager::NetworkTimezone &*other*) {#NetworkTimezone-1}

Constructs an [NetworkTimezone](modemmanager-networktimezone.md) object that is a copy of the object `other`.

### \[noexcept\] NetworkTimezone::~NetworkTimezone() {#dtor.NetworkTimezone}

Destroys this [NetworkTimezone](modemmanager-networktimezone.md) object.

### int NetworkTimezone::dstOffset() const {#dstOffset}

Returns amount of offset that is due to DST (daylight saving time)

*See also* [setDstOffset](modemmanager-networktimezone.md#setDstOffset)()

### int NetworkTimezone::leapSecond() const {#leapSecond}

Returns number of leap seconds included in the network time

*See also* [setLeapSecond](modemmanager-networktimezone.md#setLeapSecond)()

### int NetworkTimezone::offset() const {#offset}

Returns offset of the timezone from UTC, in minutes (including DST, if applicable)

*See also* [setOffset](modemmanager-networktimezone.md#setOffset)()

### void NetworkTimezone::setDstOffset(int *dstOffset*) {#setDstOffset}

Sets amount of offset that is due to DST

*See also* [dstOffset](modemmanager-networktimezone.md#dstOffset)()

### void NetworkTimezone::setLeapSecond(int *leapSecond*) {#setLeapSecond}

Sets number of leap seconds included in the network timezone

*See also* [leapSecond](modemmanager-networktimezone.md#leapSecond)()

### void NetworkTimezone::setOffset(int *offset*) {#setOffset}

Sets offset of the timezone from UTC

*See also* [offset](modemmanager-networktimezone.md#offset)()

### ModemManager::NetworkTimezone &NetworkTimezone::operator=(const ModemManager::NetworkTimezone &*other*) {#operator-eq}

Makes a copy of the [NetworkTimezone](modemmanager-networktimezone.md) object `other`.
