---
title: "KPtyDevice Class"
description: "Encapsulates KPty into a QIODevice, so it can be used with QStream, etc."
---

# KPtyDevice Class

Encapsulates [KPty](kpty-module.md) into a [QIODevice](https://doc.qt.io/qt-6/qiodevice.html), so it can be used with Q\*Stream, etc. [More...](#details)

- **Header:** `#include <KPtyDevice>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS Pty)`  
  `target_link_libraries(mytarget PRIVATE KF6::Pty)`
- **Inherits:** [QIODevice](https://doc.qt.io/qt-6/qiodevice.html) and [KPty](kpty.md)

[List of all members, including inherited members](kptydevice-members.md)

## Public Functions

- [KPtyDevice(QObject \*parent = nullptr)](#KPtyDevice)
- [~KPtyDevice()](#dtor.KPtyDevice)
- [void close()](#close)
- [bool isSequential() const](#isSequential)
- [bool isSuspended() const](#isSuspended)
- [bool open(QIODeviceBase::OpenMode mode = ReadWrite \| Unbuffered)](#open)
- [bool open(int fd, QIODeviceBase::OpenMode mode = ReadWrite \| Unbuffered)](#open-1)
- [void setSuspended(bool suspended)](#setSuspended)

## Signals

- [void readEof()](#readEof)

## Detailed Description {#details}

## Member Function Documentation {#member-function-documentation}

### \[explicit\] KPtyDevice::KPtyDevice(QObject \**parent* = nullptr) {#KPtyDevice}

Constructor

### \[override virtual noexcept\] KPtyDevice::~KPtyDevice() {#dtor.KPtyDevice}

Destructor:

If the pty is still open, it will be closed. Note, however, that an utmp registration is not undone.

### \[override virtual\] void KPtyDevice::close() {#close}

Reimplements: [QIODevice::close()](https://doc.qt.io/qt-6/qiodevice.html#close).

Close the pty master/slave pair.

### \[override virtual\] bool KPtyDevice::isSequential() const {#isSequential}

Reimplements: [QIODevice::isSequential() const](https://doc.qt.io/qt-6/qiodevice.html#isSequential).

Returns always true

### bool KPtyDevice::isSuspended() const {#isSuspended}

Returns true if the [KPtyDevice](kptydevice.md) is not monitoring the pty for incoming data.

Do not use on closed ptys.

See [setSuspended](kptydevice.md#setSuspended)()

### \[override virtual\] bool KPtyDevice::open(QIODeviceBase::OpenMode *mode* = ReadWrite \| Unbuffered) {#open}

Reimplements: [QIODevice::open(QIODeviceBase::OpenMode mode)](https://doc.qt.io/qt-6/qiodevice.html#open).

Create a pty master/slave pair.

Returns true if a pty pair was successfully opened

### bool KPtyDevice::open(int *fd*, QIODeviceBase::OpenMode *mode* = ReadWrite \| Unbuffered) {#open-1}

Open using an existing pty master. The ownership of the fd remains with the caller, i.e., [close](kptydevice.md#close)() will not close the fd.

This is useful if you wish to attach a secondary "controller" to an existing pty device such as a terminal widget. Note that you will need to use [setSuspended](kptydevice.md#setSuspended)() on both devices to control which one gets the incoming data from the pty.

`fd` an open pty master file descriptor.

`mode` the device mode to open the pty with.

Returns true if a pty pair was successfully opened

### \[signal\] void KPtyDevice::readEof() {#readEof}

Emitted when EOF is read from the PTY.

Data may still remain in the buffers.

### void KPtyDevice::setSuspended(bool *suspended*) {#setSuspended}

Sets whether the [KPtyDevice](kptydevice.md) monitors the pty for incoming data.

When the [KPtyDevice](kptydevice.md) is suspended, it will no longer attempt to buffer data that becomes available from the pty and it will not emit any signals.

Do not use on closed ptys. After a call to [open](kptydevice.md#open)(), the pty is not suspended. If you need to ensure that no data is read, call this function before the main loop is entered again (i.e., immediately after opening the pty).

*See also* [isSuspended](kptydevice.md#isSuspended)()
