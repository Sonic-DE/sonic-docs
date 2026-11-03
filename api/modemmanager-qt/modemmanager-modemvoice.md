---
title: "ModemManager::ModemVoice Class"
description: "The ModemVoice class."
---

# ModemManager::ModemVoice Class

The [ModemVoice](modemmanager-modemvoice.md) class. [More...](#details)

- **Header:** `#include <ModemManagerQt/ModemVoice>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS ModemManagerQt)`  
  `target_link_libraries(mytarget PRIVATE KF6::ModemManagerQt)`
- **Inherits:** [ModemManager::Interface](modemmanager-interface.md)

[List of all members, including inherited members](modemmanager-modemvoice-members.md)

## Public Types

- [ModemVoice::List](#List-typedef)
- [ModemVoice::Ptr](#Ptr-typedef)

## Public Functions

- [ModemVoice(const QString &path, QObject \*parent = nullptr)](#ModemVoice)
- [QDBusPendingReply\<bool\> callWaitingQuery()](#callWaitingQuery) (since 6.24.0)
- [QDBusPendingReply\<void\> callWaitingSetup(bool enabled)](#callWaitingSetup) (since 6.24.0)
- [ModemManager::Call::List calls() const](#calls)
- [QDBusPendingReply\<QDBusObjectPath\> createCall(const QString &number)](#createCall)
- [QDBusPendingReply\<QDBusObjectPath\> createCall(const QVariantMap &call)](#createCall-1)
- [QDBusPendingReply\<void\> deleteCall(const QString &uni)](#deleteCall)
- [bool emergencyOnly() const](#emergencyOnly) (since 6.24.0)
- [ModemManager::Call::Ptr findCall(const QString &uni)](#findCall)
- [QDBusPendingReply\<void\> hangupAll()](#hangupAll) (since 6.24.0)
- [QDBusPendingReply\<void\> hangupAndAccept()](#hangupAndAccept) (since 6.24.0)
- [QDBusPendingReply\<void\> holdAndAccept()](#holdAndAccept) (since 6.24.0)
- [void setTimeout(int timeout)](#setTimeout)
- [int timeout() const](#timeout)
- [QDBusPendingReply\<void\> transfer()](#transfer) (since 6.24.0)

## Signals

- [void callAdded(const QString &uni)](#callAdded)
- [void callDeleted(const QString &uni)](#callDeleted)
- [void emergencyOnlyChanged(bool emergencyOnly)](#emergencyOnlyChanged) (since 6.24.0)

## Detailed Description {#details}

The Voice interface handles call related actions.

## Member Type Documentation {#member-type-documentation}

### ModemVoice::List {#List-typedef}

### ModemVoice::Ptr {#Ptr-typedef}

## Member Function Documentation {#member-function-documentation}

### \[explicit\] ModemVoice::ModemVoice(const QString &*path*, QObject \**parent* = nullptr) {#ModemVoice}

### \[signal\] void ModemVoice::callAdded(const QString &*uni*) {#callAdded}

Emitted when an new Call is detected.

`uni` path to the Call object

### \[signal\] void ModemVoice::callDeleted(const QString &*uni*) {#callDeleted}

Emitted when a call has been deleted.

`uni` path to the Call object

### \[since 6.24.0\] QDBusPendingReply\<bool\> ModemVoice::callWaitingQuery() {#callWaitingQuery}

Query call waiting status.

This function was introduced in Qt 6.24.0.

### \[since 6.24.0\] QDBusPendingReply\<void\> ModemVoice::callWaitingSetup(bool *enabled*) {#callWaitingSetup}

Enable or disable call waiting.

This function was introduced in Qt 6.24.0.

### ModemManager::Call::List ModemVoice::calls() const {#calls}

Retrieve all calls.

This method should only be used once and subsequent information retrieved either by listening for the [callAdded](modemmanager-modemvoice.md#callAdded)() signal, or by querying the specific call object of interest using [findCall](modemmanager-modemvoice.md#findCall)()

### QDBusPendingReply\<QDBusObjectPath\> ModemVoice::createCall(const QString &*number*) {#createCall}

Creates a new call object. `number` Number property

### QDBusPendingReply\<QDBusObjectPath\> ModemVoice::createCall(const QVariantMap &*call*) {#createCall-1}

Creates a new call object.

`call` [QVariantMap](https://doc.qt.io/qt-6/qvariant.html#QVariantMap-typedef) containing call properties

The 'number' property is mandatory.

### QDBusPendingReply\<void\> ModemVoice::deleteCall(const QString &*uni*) {#deleteCall}

Delete a call.

`uni` path to the Call object

### \[since 6.24.0\] bool ModemVoice::emergencyOnly() const {#emergencyOnly}

Returns whether only emergency calls are allowed.

This function was introduced in Qt 6.24.0.

### \[signal, since 6.24.0\] void ModemVoice::emergencyOnlyChanged(bool *emergencyOnly*) {#emergencyOnlyChanged}

Emitted when emergency-only state changes.

This function was introduced in Qt 6.24.0.

### ModemManager::Call::Ptr ModemVoice::findCall(const QString &*uni*) {#findCall}

`uni` path to the Call object Returns pointer to the found Call (may be null if not found)

### \[since 6.24.0\] QDBusPendingReply\<void\> ModemVoice::hangupAll() {#hangupAll}

Hang up all calls.

This function was introduced in Qt 6.24.0.

### \[since 6.24.0\] QDBusPendingReply\<void\> ModemVoice::hangupAndAccept() {#hangupAndAccept}

Hang up the current call and accept a waiting call.

This function was introduced in Qt 6.24.0.

### \[since 6.24.0\] QDBusPendingReply\<void\> ModemVoice::holdAndAccept() {#holdAndAccept}

Hold the current call and accept a waiting call.

This function was introduced in Qt 6.24.0.

### void ModemVoice::setTimeout(int *timeout*) {#setTimeout}

Sets the timeout in milliseconds for all async method DBus calls. -1 means the default DBus timeout (usually 25 seconds).

*See also* [timeout](modemmanager-modemvoice.md#timeout)()

### int ModemVoice::timeout() const {#timeout}

Returns the current value of the DBus timeout in milliseconds. -1 means the default DBus timeout (usually 25 seconds).

*See also* [setTimeout](modemmanager-modemvoice.md#setTimeout)()

### \[since 6.24.0\] QDBusPendingReply\<void\> ModemVoice::transfer() {#transfer}

Transfer a call.

This function was introduced in Qt 6.24.0.
