---
title: "ModemManager::Modem3gppUssd Class"
description: "The Modem3gppUssd class."
---

# ModemManager::Modem3gppUssd Class

The [Modem3gppUssd](modemmanager-modem3gppussd.md) class. [More...](#details)

- **Header:** `#include <ModemManagerQt/Modem3gppUssd>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS ModemManagerQt)`  
  `target_link_libraries(mytarget PRIVATE KF6::ModemManagerQt)`
- **Inherits:** [ModemManager::Interface](modemmanager-interface.md)

[List of all members, including inherited members](modemmanager-modem3gppussd-members.md)

## Public Types

- [Modem3gppUssd::List](#List-typedef)
- [Modem3gppUssd::Ptr](#Ptr-typedef)

## Public Functions

- [Modem3gppUssd(const QString &path, QObject \*parent = nullptr)](#Modem3gppUssd)
- [void cancel()](#cancel)
- [QDBusPendingReply\<QString\> initiate(const QString &command)](#initiate)
- [QString networkNotification() const](#networkNotification)
- [QString networkRequest() const](#networkRequest)
- [QDBusPendingReply\<QString\> respond(const QString &response)](#respond)
- [void setTimeout(int timeout)](#setTimeout)
- [MMModem3gppUssdSessionState state() const](#state)
- [int timeout() const](#timeout)

## Signals

- [void networkNotificationChanged(const QString &networkNotification)](#networkNotificationChanged)
- [void networkRequestChanged(const QString &networkRequest)](#networkRequestChanged)
- [void stateChanged(MMModem3gppUssdSessionState state)](#stateChanged)

## Detailed Description {#details}

This class provides access to actions based on the USSD protocol.

## Member Type Documentation {#member-type-documentation}

### Modem3gppUssd::List {#List-typedef}

### Modem3gppUssd::Ptr {#Ptr-typedef}

## Member Function Documentation {#member-function-documentation}

### \[explicit\] Modem3gppUssd::Modem3gppUssd(const QString &*path*, QObject \**parent* = nullptr) {#Modem3gppUssd}

### void Modem3gppUssd::cancel() {#cancel}

Cancel an ongoing USSD session, either mobile or network initiated.

### QDBusPendingReply\<QString\> Modem3gppUssd::initiate(const QString &*command*) {#initiate}

Sends a USSD `command` string to the network initiating a USSD session.

When the request is handled by the network, the method returns the response or an appropriate error. The network may be awaiting further response from the ME after returning from this method and no new command can be initiated until this one is cancelled or ended.

### QString Modem3gppUssd::networkNotification() const {#networkNotification}

Returns any network-initiated request to which no USSD response is required

When no USSD session is active, or when there is no network- initiated request, this property will be an empty string.

### \[signal\] void Modem3gppUssd::networkNotificationChanged(const QString &*networkNotification*) {#networkNotificationChanged}

### QString Modem3gppUssd::networkRequest() const {#networkRequest}

Returns any pending network-initiated request for a response. Client should call [respond](modemmanager-modem3gppussd.md#respond)() with the appropriate response to this request.

When no USSD session is active, or when there is no pending network-initiated request, this property will be an empty string.

### \[signal\] void Modem3gppUssd::networkRequestChanged(const QString &*networkRequest*) {#networkRequestChanged}

### QDBusPendingReply\<QString\> Modem3gppUssd::respond(const QString &*response*) {#respond}

Respond to a USSD request that is either initiated by the mobile network, or that is awaiting further input after [initiate](modemmanager-modem3gppussd.md#initiate)() was called.

### void Modem3gppUssd::setTimeout(int *timeout*) {#setTimeout}

Sets the timeout in milliseconds for all async method DBus calls. -1 means the default DBus timeout (usually 25 seconds).

*See also* [timeout](modemmanager-modem3gppussd.md#timeout)()

### MMModem3gppUssdSessionState Modem3gppUssd::state() const {#state}

Returns the state of any ongoing USSD session

### \[signal\] void Modem3gppUssd::stateChanged(MMModem3gppUssdSessionState *state*) {#stateChanged}

### int Modem3gppUssd::timeout() const {#timeout}

Returns the current value of the DBus timeout in milliseconds. -1 means the default DBus timeout (usually 25 seconds).

*See also* [setTimeout](modemmanager-modem3gppussd.md#setTimeout)()
