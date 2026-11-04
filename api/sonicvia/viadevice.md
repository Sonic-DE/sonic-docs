---
title: "ViaDevice Class"
description: "A thin, blocking wrapper over a single HID device path."
---

# ViaDevice Class

A thin, blocking wrapper over a single HID device path. [More...](#details)

- **Header:** `#include <via/viadevice.h>`
- **CMake:** `find_package(SonicVia REQUIRED)`  
  `target_link_libraries(mytarget PRIVATE SonicVia::SonicVia)`

[List of all members, including inherited members](viadevice-members.md)

## Public Functions

- [ViaDevice(QString devicePath)](#ViaDevice)
- [bool close()](#close)
- [QString devicePath() const](#devicePath)
- [bool isOpen() const](#isOpen)
- [QString lastError() const](#lastError)
- [bool open()](#open)
- [QByteArray sendReport(const QByteArray &report)](#sendReport)

## Detailed Description {#details}

[sendReport](viadevice.md#sendReport)() is virtual so that unit tests can inject a mock device.

## Member Function Documentation {#member-function-documentation}

### \[explicit\] ViaDevice::ViaDevice(QString *devicePath*) {#ViaDevice}

Creates a device for the HID path `devicePath`, as [ViaDiscovery](viadiscovery.md) lists it.

### bool ViaDevice::close() {#close}

Closes the device; always true.

### QString ViaDevice::devicePath() const {#devicePath}

The device's HID path.

### bool ViaDevice::isOpen() const {#isOpen}

Whether [open](viadevice.md#open)() succeeded and [close](viadevice.md#close)() hasn't been called since.

### QString ViaDevice::lastError() const {#lastError}

hidapi's description of the last error.

### bool ViaDevice::open() {#open}

Opens the device; true when it is open. Always false when built without VIA support (no hidapi).

### \[virtual\] QByteArray ViaDevice::sendReport(const QByteArray &*report*) {#sendReport}

Sends the 33-byte VIA `report` and reads the (\<=32 byte) response. Returns an empty [QByteArray](https://doc.qt.io/qt-6/qbytearray.html) on any error or when built as a stub.
