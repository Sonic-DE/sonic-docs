---
title: "ModemManager::ModemMessaging Class"
description: "The ModemMessaging class."
---

# ModemManager::ModemMessaging Class

The [ModemMessaging](modemmanager-modemmessaging.md) class. [More...](#details)

- **Header:** `#include <ModemManagerQt/ModemMessaging>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS ModemManagerQt)`  
  `target_link_libraries(mytarget PRIVATE KF6::ModemManagerQt)`
- **Inherits:** [ModemManager::Interface](modemmanager-interface.md)

[List of all members, including inherited members](modemmanager-modemmessaging-members.md)

## Public Types

- [ModemMessaging::List](#List-typedef)
- [ModemMessaging::Ptr](#Ptr-typedef)

## Public Functions

- [ModemMessaging(const QString &path, QObject \*parent = nullptr)](#ModemMessaging)
- [QDBusPendingReply\<QDBusObjectPath\> createMessage(const ModemManager::ModemMessaging::Message &message)](#createMessage)
- [QDBusPendingReply\<QDBusObjectPath\> createMessage(const QVariantMap &message)](#createMessage-1)
- [MMSmsStorage defaultStorage() const](#defaultStorage)
- [QDBusPendingReply\<void\> deleteMessage(const QString &uni)](#deleteMessage)
- [ModemManager::Sms::Ptr findMessage(const QString &uni)](#findMessage)
- [ModemManager::Sms::List messages() const](#messages)
- [QDBusPendingReply\<void\> setDefaultStorage(MMSmsStorage storage)](#setDefaultStorage) (since 6.24.0)
- [void setTimeout(int timeout)](#setTimeout)
- [QList\<MMSmsStorage\> supportedStorages() const](#supportedStorages)
- [int timeout() const](#timeout)

## Signals

- [void messageAdded(const QString &uni, bool received)](#messageAdded)
- [void messageDeleted(const QString &uni)](#messageDeleted)

## Detailed Description {#details}

The Messaging interface handles sending SMS messages and notification of new incoming messages.

## Member Type Documentation {#member-type-documentation}

### ModemMessaging::List {#List-typedef}

### ModemMessaging::Ptr {#Ptr-typedef}

## Member Function Documentation {#member-function-documentation}

### \[explicit\] ModemMessaging::ModemMessaging(const QString &*path*, QObject \**parent* = nullptr) {#ModemMessaging}

### QDBusPendingReply\<QDBusObjectPath\> ModemMessaging::createMessage(const ModemManager::ModemMessaging::Message &*message*) {#createMessage}

Creates a new message object.

`message` Message structure with the 'number' and either 'text' or 'data' properties

### QDBusPendingReply\<QDBusObjectPath\> ModemMessaging::createMessage(const QVariantMap &*message*) {#createMessage-1}

Creates a new message object.

`message` [QVariantMap](https://doc.qt.io/qt-6/qvariant.html#QVariantMap-typedef) containing message properties

The 'number' and either 'text' or 'data' properties are mandatory, others are optional.

### MMSmsStorage ModemMessaging::defaultStorage() const {#defaultStorage}

Returns A MMSmsStorage value, specifying the storage to be used when receiving or storing SMS.

*See also* [setDefaultStorage](modemmanager-modemmessaging.md#setDefaultStorage)()

### QDBusPendingReply\<void\> ModemMessaging::deleteMessage(const QString &*uni*) {#deleteMessage}

Delete an SMS message.

`uni` path to the Sms object

### ModemManager::Sms::Ptr ModemMessaging::findMessage(const QString &*uni*) {#findMessage}

`uni` path to the Sms object

Returns pointer to the found Sms (may be null if not found)

### \[signal\] void ModemMessaging::messageAdded(const QString &*uni*, bool *received*) {#messageAdded}

Emitted when any part of a new SMS has been received or added (but not for subsequent parts, if any). For messages received from the network, not all parts may have been received and the message may not be complete.

Check the 'State' property to determine if the message is complete.

`uni` path to the Sms object

`received` `true` if the message was received from the network, as opposed to being added locally.

### \[signal\] void ModemMessaging::messageDeleted(const QString &*uni*) {#messageDeleted}

Emitted when a message has been deleted.

`uni` path to the Sms object

### ModemManager::Sms::List ModemMessaging::messages() const {#messages}

Retrieve all SMS messages.

This method should only be used once and subsequent information retrieved either by listening for the [messageAdded](modemmanager-modemmessaging.md#messageAdded)() signal, or by querying the specific SMS object of interest using [findMessage](modemmanager-modemmessaging.md#findMessage)()

### \[since 6.24.0\] QDBusPendingReply\<void\> ModemMessaging::setDefaultStorage(MMSmsStorage *storage*) {#setDefaultStorage}

Set the default storage to use when receiving or storing SMS.

This function was introduced in Qt 6.24.0.

*See also* [defaultStorage](modemmanager-modemmessaging.md#defaultStorage)()

### void ModemMessaging::setTimeout(int *timeout*) {#setTimeout}

Sets the timeout in milliseconds for all async method DBus calls.

-1 means the default DBus timeout (usually 25 seconds).

*See also* [timeout](modemmanager-modemmessaging.md#timeout)()

### QList\<MMSmsStorage\> ModemMessaging::supportedStorages() const {#supportedStorages}

Returns A list of MMSmsStorage values, specifying the storages supported by this modem for storing and receiving SMS.

### int ModemMessaging::timeout() const {#timeout}

Returns the current value of the DBus timeout in milliseconds.

-1 means the default DBus timeout (usually 25 seconds).

*See also* [setTimeout](modemmanager-modemmessaging.md#setTimeout)()
