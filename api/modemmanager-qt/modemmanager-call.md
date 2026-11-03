---
title: "ModemManager::Call Class"
description: "Provides an interface to manipulate and control a call."
---

# ModemManager::Call Class

Provides an interface to manipulate and control a call. [More...](#details)

- **Header:** `#include <ModemManagerQt/Call>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS ModemManagerQt)`  
  `target_link_libraries(mytarget PRIVATE KF6::ModemManagerQt)`
- **Inherits:** [QObject](https://doc.qt.io/qt-6/qobject.html)

[List of all members, including inherited members](modemmanager-call-members.md)

## Public Types

- [Call::List](#List-typedef)
- [Call::Ptr](#Ptr-typedef)

## Public Functions

- [Call(const QString &path, QObject \*parent = nullptr)](#Call)
- [QDBusPendingReply\<\> accept()](#accept)
- [QVariantMap audioFormat() const](#audioFormat) (since 6.24.0)
- [QString audioPort() const](#audioPort) (since 6.24.0)
- [QDBusPendingReply\<\> deflect(const QString &number)](#deflect) (since 6.24.0)
- [MMCallDirection direction() const](#direction)
- [QDBusPendingReply\<\> hangup()](#hangup)
- [bool isMultiparty() const](#isMultiparty) (since 6.24.0)
- [QDBusPendingReply\<\> joinMultiparty()](#joinMultiparty) (since 6.24.0)
- [QDBusPendingReply\<\> leaveMultiparty()](#leaveMultiparty) (since 6.24.0)
- [QString number() const](#number)
- [QDBusPendingReply\<\> sendDtmf(const QString &dtmf)](#sendDtmf)
- [void setTimeout(int timeout)](#setTimeout)
- [QDBusPendingReply\<\> start()](#start)
- [MMCallState state() const](#state)
- [MMCallStateReason stateReason() const](#stateReason)
- [int timeout() const](#timeout)
- [QString uni() const](#uni)

## Signals

- [void audioFormatChanged(const QVariantMap &audioFormat)](#audioFormatChanged) (since 6.24.0)
- [void audioPortChanged(const QString &audioPort)](#audioPortChanged) (since 6.24.0)
- [void dtmfReceived(const QString &dtmf)](#dtmfReceived)
- [void multipartyChanged(bool multiparty)](#multipartyChanged) (since 6.24.0)
- [void numberChanged(const QString &number)](#numberChanged)
- [void stateChanged(MMCallState oldState, MMCallState newState, MMCallStateReason reason)](#stateChanged)

## Detailed Description {#details}

> **Note:** MMCallState, MMCallStateReason and MMCallDirection enums are defined in \<[ModemManager](modemmanager.md)/[ModemManager](modemmanager.md)-enums.h\> See http://www.freedesktop.org/software/[ModemManager](modemmanager.md)/api/latest/[ModemManager](modemmanager.md)-Flags-and-Enumerations.html .

## Member Type Documentation {#member-type-documentation}

### Call::List {#List-typedef}

### Call::Ptr {#Ptr-typedef}

## Member Function Documentation {#member-function-documentation}

### \[explicit\] Call::Call(const QString &*path*, QObject \**parent* = nullptr) {#Call}

### QDBusPendingReply\<\> Call::accept() {#accept}

Accept incoming call (answer).

Applicable only if state is `MM_CALL_STATE_RINGING_IN` and direction is `MM_CALL_DIRECTION_INCOMING`.

### \[since 6.24.0\] QVariantMap Call::audioFormat() const {#audioFormat}

If call audio is routed via the host, returns a description of the audio format supported by the audio port.

The returned map may include the following items:

`"encoding"` - The audio encoding format (e.g. "pcm").

`"resolution"` - The sampling precision and encoding format (e.g. "s16le").

`"rate"` - The sampling rate as an unsigned integer (e.g. 8000).

This function was introduced in Qt 6.24.0.

### \[signal, since 6.24.0\] void Call::audioFormatChanged(const QVariantMap &*audioFormat*) {#audioFormatChanged}

This function was introduced in Qt 6.24.0.

### \[since 6.24.0\] QString Call::audioPort() const {#audioPort}

If call audio is routed via the host, returns the name of the kernel device that provides the audio. For example, with certain Huawei USB modems, this might be "ttyUSB2" indicating audio is available via ttyUSB2 in the format described by the [audioFormat](modemmanager-call.md#audioFormat) property.

This function was introduced in Qt 6.24.0.

### \[signal, since 6.24.0\] void Call::audioPortChanged(const QString &*audioPort*) {#audioPortChanged}

This function was introduced in Qt 6.24.0.

### \[since 6.24.0\] QDBusPendingReply\<\> Call::deflect(const QString &*number*) {#deflect}

Deflect an incoming or waiting call to a new `number`. The call will be considered terminated once the deflection is performed.

Applicable only if state is `MM_CALL_STATE_RINGING_IN` or `MM_CALL_STATE_WAITING` and direction is `MM_CALL_DIRECTION_INCOMING`.

This function was introduced in Qt 6.24.0.

### MMCallDirection Call::direction() const {#direction}

Returns the MMCallDirection value describing the direction of the call.

### \[signal\] void Call::dtmfReceived(const QString &*dtmf*) {#dtmfReceived}

### QDBusPendingReply\<\> Call::hangup() {#hangup}

Hangup the active call.

Applicable only if state is `MM_CALL_STATE_UNKNOWN`.

### \[since 6.24.0\] bool Call::isMultiparty() const {#isMultiparty}

Returns whether the call is currently part of a multiparty conference call.

This function was introduced in Qt 6.24.0.

### \[since 6.24.0\] QDBusPendingReply\<\> Call::joinMultiparty() {#joinMultiparty}

Join the currently held call into a single multiparty call with another already active call.

The calls will be flagged with the Multiparty property while they are part of the multiparty call.

Applicable only if state is `MM_CALL_STATE_HELD`.

This function was introduced in Qt 6.24.0.

### \[since 6.24.0\] QDBusPendingReply\<\> Call::leaveMultiparty() {#leaveMultiparty}

If this call is part of an ongoing multiparty call, detach it from the multiparty call, put the multiparty call on hold, and activate this one alone. This operation makes this call private again between both ends of the call.

Applicable only if state is `MM_CALL_STATE_ACTIVE` or `MM_CALL_STATE_HELD` and the call is a multiparty call.

This function was introduced in Qt 6.24.0.

### \[signal, since 6.24.0\] void Call::multipartyChanged(bool *multiparty*) {#multipartyChanged}

This function was introduced in Qt 6.24.0.

### QString Call::number() const {#number}

Returns the remote phone number.

### \[signal\] void Call::numberChanged(const QString &*number*) {#numberChanged}

### QDBusPendingReply\<\> Call::sendDtmf(const QString &*dtmf*) {#sendDtmf}

Send a DTMF tone (Dual Tone Multi-Frequency) (only on supported modems).

`dtmf` is the DTMF tone identifier \[0-9A-D\*\#\].

Applicable only if state is `MM_CALL_STATE_ACTIVE`.

### void Call::setTimeout(int *timeout*) {#setTimeout}

Sets the timeout in milliseconds for all async method DBus calls. -1 means the default DBus timeout (usually 25 seconds).

*See also* [timeout](modemmanager-call.md#timeout)()

### QDBusPendingReply\<\> Call::start() {#start}

If the outgoing call has not yet been started, start it.

Applicable only if state is `MM_CALL_STATE_UNKNOWN` and direction is `MM_CALL_DIRECTION_OUTGOING`.

### MMCallState Call::state() const {#state}

Returns the current MMCallState value describing the state of the call.

### \[signal\] void Call::stateChanged(MMCallState *oldState*, MMCallState *newState*, MMCallStateReason *reason*) {#stateChanged}

### MMCallStateReason Call::stateReason() const {#stateReason}

Returns the MMCallStateReason value describing why the state changed.

### int Call::timeout() const {#timeout}

Returns the current value of the DBus timeout in milliseconds. -1 means the default DBus timeout (usually 25 seconds).

*See also* [setTimeout](modemmanager-call.md#setTimeout)()

### QString Call::uni() const {#uni}
