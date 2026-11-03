---
title: "ModemManager::ModemCellBroadcast Class"
description: "The ModemCellBroadcast class. This class was introduced in Qt 6.24.0."
---

# ModemManager::ModemCellBroadcast Class

The [ModemCellBroadcast](modemmanager-modemcellbroadcast.md) class. This class was introduced in Qt 6.24.0. [More...](#details)

- **Header:** `#include <ModemManagerQt/ModemCellBroadcast>`
- **Since:** Qt 6.24.0
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS ModemManagerQt)`  
  `target_link_libraries(mytarget PRIVATE KF6::ModemManagerQt)`
- **Inherits:** [ModemManager::Interface](modemmanager-interface.md)

[List of all members, including inherited members](modemmanager-modemcellbroadcast-members.md)

## Public Types

- [ModemCellBroadcast::List](#List-typedef)
- [ModemCellBroadcast::Ptr](#Ptr-typedef)

## Public Functions

- [ModemCellBroadcast(const QString &path, QObject \*parent = nullptr)](#ModemCellBroadcast)
- [ModemManager::Cbm::List cellBroadcasts() const](#cellBroadcasts)
- [ModemManager::CellBroadcastChannelRangeList channels() const](#channels)
- [QDBusPendingReply\<void\> deleteCellBroadcast(const QString &uni)](#deleteCellBroadcast)
- [ModemManager::Cbm::Ptr findCellBroadcast(const QString &uni)](#findCellBroadcast)
- [QDBusPendingReply\<void\> setChannels(const ModemManager::CellBroadcastChannelRangeList &channels)](#setChannels)
- [void setTimeout(int timeout)](#setTimeout)
- [int timeout() const](#timeout)

## Signals

- [void cellBroadcastAdded(const QString &uni)](#cellBroadcastAdded)
- [void cellBroadcastDeleted(const QString &uni)](#cellBroadcastDeleted)
- [void channelsChanged(const ModemManager::CellBroadcastChannelRangeList &channels)](#channelsChanged)

## Detailed Description {#details}

This interface allows clients to configure the details of CellBroadcast service information.

This interface will only be available once the modem is ready to be registered in the cellular network.

## Member Type Documentation {#member-type-documentation}

### ModemCellBroadcast::List {#List-typedef}

### ModemCellBroadcast::Ptr {#Ptr-typedef}

## Member Function Documentation {#member-function-documentation}

### \[explicit\] ModemCellBroadcast::ModemCellBroadcast(const QString &*path*, QObject \**parent* = nullptr) {#ModemCellBroadcast}

### \[signal\] void ModemCellBroadcast::cellBroadcastAdded(const QString &*uni*) {#cellBroadcastAdded}

Emitted when any part of a new cell broadcast message has been received. Not all parts may have been received and the message may not be complete. Check the State property to determine if the message is complete.

`uni` object path of the new CBM

### \[signal\] void ModemCellBroadcast::cellBroadcastDeleted(const QString &*uni*) {#cellBroadcastDeleted}

Emitted when a message has been deleted.

`uni` object path of the now deleted CBM

### ModemManager::Cbm::List ModemCellBroadcast::cellBroadcasts() const {#cellBroadcasts}

Returns the list of CBM object paths.

### ModemManager::CellBroadcastChannelRangeList ModemCellBroadcast::channels() const {#channels}

Returns the list of channels that cell broadcast messages are received for.

*See also* [setChannels](modemmanager-modemcellbroadcast.md#setChannels)()

### \[signal\] void ModemCellBroadcast::channelsChanged(const ModemManager::CellBroadcastChannelRangeList &*channels*) {#channelsChanged}

### QDBusPendingReply\<void\> ModemCellBroadcast::deleteCellBroadcast(const QString &*uni*) {#deleteCellBroadcast}

Delete a cell broadcast message.

`uni` the object path of the CBM to delete

### ModemManager::Cbm::Ptr ModemCellBroadcast::findCellBroadcast(const QString &*uni*) {#findCellBroadcast}

Retrieve a specific cell broadcast message by its D-Bus object path.

`uni` the object path of the CBM to retrieve

### QDBusPendingReply\<void\> ModemCellBroadcast::setChannels(const ModemManager::CellBroadcastChannelRangeList &*channels*) {#setChannels}

Set the list of channels to receive Cell Broadcasts for.

`channels` the list of channel ranges

*See also* [channels](modemmanager-modemcellbroadcast.md#channels)()

### void ModemCellBroadcast::setTimeout(int *timeout*) {#setTimeout}

Sets the timeout in milliseconds for all async method DBus calls. -1 means the default DBus timeout (usually 25 seconds).

*See also* [timeout](modemmanager-modemcellbroadcast.md#timeout)()

### int ModemCellBroadcast::timeout() const {#timeout}

Returns the current value of the DBus timeout in milliseconds. -1 means the default DBus timeout (usually 25 seconds).

*See also* [setTimeout](modemmanager-modemcellbroadcast.md#setTimeout)()
