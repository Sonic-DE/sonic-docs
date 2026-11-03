---
title: "BluezQt::PendingCall Class"
description: "Pending method call."
---

# BluezQt::PendingCall Class

Pending method call. [More...](#details)

- **Header:** `#include <BluezQt/PendingCall>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS BluezQt)`  
  `target_link_libraries(mytarget PRIVATE KF6::BluezQt)`
- **Inherits:** [QObject](https://doc.qt.io/qt-6/qobject.html)
- **Inherited By:** [BluezQt::TPendingCall](bluezqt-tpendingcall.md)

[List of all members, including inherited members](bluezqt-pendingcall-members.md)

## Public Types

- [enum PendingCall::Error](#Error-enum)

## Properties

- [\[read-only\] error : int](#error-prop)
- [\[read-only\] errorText : QString](#errorText-prop)
- [\[read-only\] isFinished : bool](#isFinished-prop)
- [userData : QVariant](#userData-prop)
- [\[read-only\] value : QVariant](#value-prop)
- [\[read-only\] values : QVariantList](#values-prop)

## Public Functions

- [int error() const](#error)
- [QString errorText() const](#errorText)
- [bool isFinished() const](#isFinished)
- [void setUserData(const QVariant &userData)](#setUserData)
- [QVariant userData() const](#userData)
- [QVariant value() const](#value)
- [QVariantList values() const](#values)
- [void waitForFinished()](#waitForFinished)

## Signals

- [void finished(BluezQt::PendingCall \*call)](#finished)

## Detailed Description {#details}

This class represents a pending method call. It is a convenient wrapper around QDBusPendingReply and QDBusPendingCallWatcher.

## Member Type Documentation {#member-type-documentation}

### enum PendingCall::Error {#Error-enum}

Known error types.

| Constant | Value | Description |
| --- | --- | --- |
| `BluezQt::PendingCall::NoError` | `0` | Indicates there is no error. |
| `BluezQt::PendingCall::NotReady` | `1` | Indicates that the device is not ready. |
| `BluezQt::PendingCall::Failed` | `2` | Indicates that the action have failed. |
| `BluezQt::PendingCall::Rejected` | `3` | Indicates that the action was rejected. |
| `BluezQt::PendingCall::Canceled` | `4` | Indicates that the action was canceled. |
| `BluezQt::PendingCall::InvalidArguments` | `5` | Indicates that invalid arguments were passed. |
| `BluezQt::PendingCall::AlreadyExists` | `6` | Indicates that an agent or pairing record already exists. |
| `BluezQt::PendingCall::DoesNotExist` | `7` | Indicates that an agent, service or pairing operation does not exists. |
| `BluezQt::PendingCall::InProgress` | `8` | Indicates that the action is already in progress. |
| `BluezQt::PendingCall::NotInProgress` | `9` | Indicates that the action is not in progress. |
| `BluezQt::PendingCall::AlreadyConnected` | `10` | Indicates that the device is already connected. |
| `BluezQt::PendingCall::ConnectFailed` | `11` | Indicates that the connection to the device have failed. |
| `BluezQt::PendingCall::NotConnected` | `12` | Indicates that the device is not connected. |
| `BluezQt::PendingCall::NotSupported` | `13` | Indicates that the action is not supported. |
| `BluezQt::PendingCall::NotAuthorized` | `14` | Indicates that the caller is not authorized to do the action. |
| `BluezQt::PendingCall::AuthenticationCanceled` | `15` | Indicates that the authentication was canceled. |
| `BluezQt::PendingCall::AuthenticationFailed` | `16` | Indicates that the authentication have failed. |
| `BluezQt::PendingCall::AuthenticationRejected` | `17` | Indicates that the authentication was rejected. |
| `BluezQt::PendingCall::AuthenticationTimeout` | `18` | Indicates that the authentication timed out. |
| `BluezQt::PendingCall::ConnectionAttemptFailed` | `19` | Indicates that the connection attempt have failed. |
| `BluezQt::PendingCall::InvalidLength` | `20` | Indicates that the data provided generates a data packet which is too long. |
| `BluezQt::PendingCall::NotPermitted` | `21` | Indicates that the action is not permitted (e.g. maximum reached or socket locked). |
| `BluezQt::PendingCall::DBusError` | `98` | Indicates an error with D-Bus. |
| `BluezQt::PendingCall::InternalError` | `99` | Indicates an internal error. |
| `BluezQt::PendingCall::UnknownError` | `100` | Indicates an unknown error. |

## Property Documentation {#property-documentation}

### \[read-only\] error : int {#error-prop}

**Access functions:**

- `int` **[error](bluezqt-pendingcall.md#error)**() const

### \[read-only\] errorText : QString {#errorText-prop}

**Access functions:**

- `QString` **[errorText](bluezqt-pendingcall.md#errorText)**() const

### \[read-only\] isFinished : bool {#isFinished-prop}

**Access functions:**

- `bool` **[isFinished](bluezqt-pendingcall.md#isFinished)**() const

### userData : QVariant {#userData-prop}

**Access functions:**

- `QVariant` **[userData](bluezqt-pendingcall.md#userData)**() const
- `void` **[setUserData](bluezqt-pendingcall.md#setUserData)**(const `QVariant` &*userData*)

### \[read-only\] value : QVariant {#value-prop}

**Access functions:**

- `QVariant` **[value](bluezqt-pendingcall.md#value)**() const

### \[read-only\] values : QVariantList {#values-prop}

**Access functions:**

- `QVariantList` **[values](bluezqt-pendingcall.md#values)**() const

## Member Function Documentation {#member-function-documentation}

### int PendingCall::error() const {#error}

Returns an error code.

> **Note:** Getter function for property [error](bluezqt-pendingcall.md#error-prop).

*See also* [Error](bluezqt-pendingcall.md#Error-enum)

### QString PendingCall::errorText() const {#errorText}

Returns an error text.

> **Note:** Getter function for property [errorText](bluezqt-pendingcall.md#errorText-prop).

### \[signal\] void PendingCall::finished(BluezQt::PendingCall \**call*) {#finished}

Indicates that the `call` has finished.

### bool PendingCall::isFinished() const {#isFinished}

Returns whether the call is finished.

> **Note:** Getter function for property [isFinished](bluezqt-pendingcall.md#isFinished-prop).

### void PendingCall::setUserData(const QVariant &*userData*) {#setUserData}

Sets the `userData` of the call.

> **Note:** Setter function for property [userData](bluezqt-pendingcall.md#userData-prop).

*See also* [userData](bluezqt-pendingcall.md#userData)()

### QVariant PendingCall::userData() const {#userData}

Returns the user data of the call.

> **Note:** Getter function for property [userData](bluezqt-pendingcall.md#userData-prop).

*See also* [setUserData](bluezqt-pendingcall.md#setUserData)()

### QVariant PendingCall::value() const {#value}

Returns a first return value of the call.

> **Note:** Getter function for property [value](bluezqt-pendingcall.md#value-prop).

### QVariantList PendingCall::values() const {#values}

Returns all values of the call.

> **Note:** Getter function for property [values](bluezqt-pendingcall.md#values-prop).

### void PendingCall::waitForFinished() {#waitForFinished}

Waits for the call to finish.

> **Warning:** This method blocks until the call finishes!
