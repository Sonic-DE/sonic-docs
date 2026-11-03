---
title: "BluezQt::ObexTransfer Class"
description: "OBEX transfer."
---

# BluezQt::ObexTransfer Class

OBEX transfer. [More...](#details)

- **Header:** `#include <BluezQt/ObexTransfer>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS BluezQt)`  
  `target_link_libraries(mytarget PRIVATE KF6::BluezQt)`
- **Inherits:** [QObject](https://doc.qt.io/qt-6/qobject.html)

[List of all members, including inherited members](bluezqt-obextransfer-members.md)

## Public Types

- [enum ObexTransfer::Status](#Status-enum)

## Properties

- [\[read-only\] fileName : QString](#fileName-prop)
- [\[read-only\] name : QString](#name-prop)
- [\[read-only\] size : quint64](#size-prop)
- [\[read-only\] status : Status](#status-prop)
- [\[read-only\] suspendable : bool](#suspendable-prop)
- [\[read-only\] time : quint64](#time-prop)
- [\[read-only\] transferred : quint64](#transferred-prop)
- [\[read-only\] type : QString](#type-prop)

## Public Functions

- [BluezQt::PendingCall \*cancel()](#cancel)
- [QString fileName() const](#fileName)
- [bool isSuspendable() const](#isSuspendable)
- [QString name() const](#name)
- [QDBusObjectPath objectPath() const](#objectPath)
- [BluezQt::PendingCall \*resume()](#resume)
- [quint64 size() const](#size)
- [BluezQt::ObexTransfer::Status status() const](#status)
- [BluezQt::PendingCall \*suspend()](#suspend)
- [quint64 time() const](#time)
- [BluezQt::ObexTransferPtr toSharedPtr() const](#toSharedPtr)
- [quint64 transferred() const](#transferred)
- [QString type() const](#type)

## Signals

- [void fileNameChanged(const QString &fileName)](#fileNameChanged)
- [void statusChanged(BluezQt::ObexTransfer::Status status)](#statusChanged)
- [void transferredChanged(quint64 transferred)](#transferredChanged)

## Detailed Description {#details}

This class represents transfer of one file.

## Member Type Documentation {#member-type-documentation}

### enum ObexTransfer::Status {#Status-enum}

Transfer status.

| Constant | Value | Description |
| --- | --- | --- |
| `BluezQt::ObexTransfer::Queued` | `0` | Indicates that the transfer is queued. |
| `BluezQt::ObexTransfer::Active` | `1` | Indicates that the transfer is active. |
| `BluezQt::ObexTransfer::Suspended` | `2` | Indicates that the transfer is suspended. |
| `BluezQt::ObexTransfer::Complete` | `3` | Indicates that the transfer have completed successfully. |
| `BluezQt::ObexTransfer::Error` | `4` | Indicates that the transfer have failed with error. |
| `BluezQt::ObexTransfer::Unknown` | `5` | Indicates that the transfer status is unknown. |

## Property Documentation {#property-documentation}

### \[read-only\] fileName : QString {#fileName-prop}

**Access functions:**

- `QString` **[fileName](bluezqt-obextransfer.md#fileName)**() const

**Notifier signal:**

- `void` **[fileNameChanged](bluezqt-obextransfer.md#fileNameChanged)**(const `QString` &*fileName*)

### \[read-only\] name : QString {#name-prop}

**Access functions:**

- `QString` **[name](bluezqt-obextransfer.md#name)**() const

### \[read-only\] size : quint64 {#size-prop}

**Access functions:**

- `quint64` **[size](bluezqt-obextransfer.md#size)**() const

### \[read-only\] status : Status {#status-prop}

**Access functions:**

- `BluezQt::ObexTransfer::Status` **[status](bluezqt-obextransfer.md#status)**() const

**Notifier signal:**

- `void` **[statusChanged](bluezqt-obextransfer.md#statusChanged)**(`BluezQt::ObexTransfer::Status` *status*)

### \[read-only\] suspendable : bool {#suspendable-prop}

**Access functions:**

- `bool` **[isSuspendable](bluezqt-obextransfer.md#isSuspendable)**() const

### \[read-only\] time : quint64 {#time-prop}

**Access functions:**

- `quint64` **[time](bluezqt-obextransfer.md#time)**() const

### \[read-only\] transferred : quint64 {#transferred-prop}

**Access functions:**

- `quint64` **[transferred](bluezqt-obextransfer.md#transferred)**() const

**Notifier signal:**

- `void` **[transferredChanged](bluezqt-obextransfer.md#transferredChanged)**(`quint64` *transferred*)

### \[read-only\] type : QString {#type-prop}

**Access functions:**

- `QString` **[type](bluezqt-obextransfer.md#type)**() const

## Member Function Documentation {#member-function-documentation}

### BluezQt::PendingCall \*ObexTransfer::cancel() {#cancel}

Stops the current transfer.

Possible errors:

- [PendingCall::NotAuthorized](bluezqt-pendingcall.md#Error-enum)
- [PendingCall::InProgress](bluezqt-pendingcall.md#Error-enum)
- [PendingCall::Failed](bluezqt-pendingcall.md#Error-enum)

Returns void pending call.

### QString ObexTransfer::fileName() const {#fileName}

Returns the full name of the transferred file.

> **Note:** Getter function for property [fileName](bluezqt-obextransfer.md#fileName-prop).

### \[signal\] void ObexTransfer::fileNameChanged(const QString &*fileName*) {#fileNameChanged}

Indicates that the transferred `fileName` has changed.

> **Note:** Notifier signal for property [fileName](bluezqt-obextransfer.md#fileName-prop).

### bool ObexTransfer::isSuspendable() const {#isSuspendable}

Returns whether the transfer is suspendable.

> **Note:** Getter function for property [suspendable](bluezqt-obextransfer.md#suspendable-prop).

### QString ObexTransfer::name() const {#name}

Returns the name of the transferred object.

> **Note:** Getter function for property [name](bluezqt-obextransfer.md#name-prop).

### QDBusObjectPath ObexTransfer::objectPath() const {#objectPath}

Returns the D-Bus object path of the transfer.

### BluezQt::PendingCall \*ObexTransfer::resume() {#resume}

Resumes the current transfer.

Possible errors:

- [PendingCall::NotAuthorized](bluezqt-pendingcall.md#Error-enum)
- [PendingCall::NotInProgress](bluezqt-pendingcall.md#Error-enum)

Returns void pending call.

### quint64 ObexTransfer::size() const {#size}

Returns the total size of the transferred object.

> **Note:** Getter function for property [size](bluezqt-obextransfer.md#size-prop).

### BluezQt::ObexTransfer::Status ObexTransfer::status() const {#status}

Returns the status of the transfer.

> **Note:** Getter function for property [status](bluezqt-obextransfer.md#status-prop).

### \[signal\] void ObexTransfer::statusChanged(BluezQt::ObexTransfer::Status *status*) {#statusChanged}

Indicates that the `status` of transfer has changed.

> **Note:** Notifier signal for property [status](bluezqt-obextransfer.md#status-prop).

### BluezQt::PendingCall \*ObexTransfer::suspend() {#suspend}

Suspends the current transfer.

Only suspendable transfers can be suspended.

Possible errors:

- [PendingCall::NotAuthorized](bluezqt-pendingcall.md#Error-enum)
- [PendingCall::NotInProgress](bluezqt-pendingcall.md#Error-enum)

Returns void pending call.

*See also* [isSuspendable](bluezqt-obextransfer.md#isSuspendable)()

### quint64 ObexTransfer::time() const {#time}

Returns the time of the transferred object.

> **Note:** Getter function for property [time](bluezqt-obextransfer.md#time-prop).

### BluezQt::ObexTransferPtr ObexTransfer::toSharedPtr() const {#toSharedPtr}

Returns a shared pointer from this.

### quint64 ObexTransfer::transferred() const {#transferred}

Returns the number of bytes transferred.

> **Note:** Getter function for property [transferred](bluezqt-obextransfer.md#transferred-prop).

### \[signal\] void ObexTransfer::transferredChanged(quint64 *transferred*) {#transferredChanged}

Indicates that the number of `transferred` bytes has changed.

> **Note:** Notifier signal for property [transferred](bluezqt-obextransfer.md#transferred-prop).

### QString ObexTransfer::type() const {#type}

Returns the type of the transferred object.

> **Note:** Getter function for property [type](bluezqt-obextransfer.md#type-prop).
