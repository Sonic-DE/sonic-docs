---
title: "ModemManager::Cbm Class"
description: "Provides an interface to access a cell broadcast message. This class was introduced in Qt 6.24.0."
---

# ModemManager::Cbm Class

Provides an interface to access a cell broadcast message. This class was introduced in Qt 6.24.0. [More...](#details)

- **Header:** `#include <ModemManagerQt/Cbm>`
- **Since:** Qt 6.24.0
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS ModemManagerQt)`  
  `target_link_libraries(mytarget PRIVATE KF6::ModemManagerQt)`
- **Inherits:** [QObject](https://doc.qt.io/qt-6/qobject.html)

[List of all members, including inherited members](modemmanager-cbm-members.md)

## Public Types

- [Cbm::List](#List-typedef)
- [Cbm::Ptr](#Ptr-typedef)

## Public Functions

- [Cbm(const QString &path, QObject \*parent = nullptr)](#Cbm)
- [uint channel() const](#channel)
- [uint messageCode() const](#messageCode)
- [void setTimeout(int timeout)](#setTimeout)
- [MMCbmState state() const](#state)
- [QString text() const](#text)
- [int timeout() const](#timeout)
- [QString uni() const](#uni)
- [uint update() const](#update)

## Signals

- [void channelChanged(uint channel)](#channelChanged)
- [void messageCodeChanged(uint messageCode)](#messageCodeChanged)
- [void stateChanged(MMCbmState state)](#stateChanged)
- [void textChanged(const QString &text)](#textChanged)
- [void updateChanged(uint update)](#updateChanged)

## Detailed Description {#details}

> **Note:** MMCbmState enum is defined in \<[ModemManager](modemmanager.md)/[ModemManager](modemmanager.md)-enums.h\>

## Member Type Documentation {#member-type-documentation}

### Cbm::List {#List-typedef}

### Cbm::Ptr {#Ptr-typedef}

## Member Function Documentation {#member-function-documentation}

### \[explicit\] Cbm::Cbm(const QString &*path*, QObject \**parent* = nullptr) {#Cbm}

### uint Cbm::channel() const {#channel}

Returns the channel (or message identifier) specifying the source and type of the cell broadcast message.

### \[signal\] void Cbm::channelChanged(uint *channel*) {#channelChanged}

### uint Cbm::messageCode() const {#messageCode}

Returns the message code of this CBM. The message code differentiates between CBMs from the same channel.

### \[signal\] void Cbm::messageCodeChanged(uint *messageCode*) {#messageCodeChanged}

### void Cbm::setTimeout(int *timeout*) {#setTimeout}

Sets the timeout in milliseconds for all async method DBus calls. -1 means the default DBus timeout (usually 25 seconds).

*See also* [timeout](modemmanager-cbm.md#timeout)()

### MMCbmState Cbm::state() const {#state}

Returns the MMCbmState value describing the state of the message.

### \[signal\] void Cbm::stateChanged(MMCbmState *state*) {#stateChanged}

### QString Cbm::text() const {#text}

Returns the message text, in UTF-8.

### \[signal\] void Cbm::textChanged(const QString &*text*) {#textChanged}

### int Cbm::timeout() const {#timeout}

Returns the current value of the DBus timeout in milliseconds. -1 means the default DBus timeout (usually 25 seconds).

*See also* [setTimeout](modemmanager-cbm.md#setTimeout)()

### QString Cbm::uni() const {#uni}

Returns the D-Bus object path of the cell broadcast message.

### uint Cbm::update() const {#update}

Returns the update number of this CBM. The update number allows to update CBMs with the same channel and message code.

### \[signal\] void Cbm::updateChanged(uint *update*) {#updateChanged}
