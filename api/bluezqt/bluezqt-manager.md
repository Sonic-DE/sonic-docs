---
title: "BluezQt::Manager Class"
description: "Bluetooth manager."
---

# BluezQt::Manager Class

Bluetooth manager. [More...](#details)

- **Header:** `#include <BluezQt/Manager>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS BluezQt)`  
  `target_link_libraries(mytarget PRIVATE KF6::BluezQt)`
- **Inherits:** [QObject](https://doc.qt.io/qt-6/qobject.html)

[List of all members, including inherited members](bluezqt-manager-members.md)

## Properties

- [\[read-only\] adapters : QList\<AdapterPtr\>](#adapters-prop)
- [bluetoothBlocked : bool](#bluetoothBlocked-prop)
- [\[read-only\] bluetoothOperational : bool](#bluetoothOperational-prop)
- [\[read-only\] devices : QList\<DevicePtr\>](#devices-prop)
- [\[read-only\] initialized : bool](#initialized-prop)
- [\[read-only\] operational : bool](#operational-prop)
- [\[read-only\] rfkill : BluezQt::Rfkill\* const](#rfkill-prop)
- [\[read-only\] usableAdapter : AdapterPtr](#usableAdapter-prop)

## Public Functions

- [Manager(QObject \*parent = nullptr)](#Manager)
- [BluezQt::AdapterPtr adapterForAddress(const QString &address) const](#adapterForAddress)
- [BluezQt::AdapterPtr adapterForUbi(const QString &ubi) const](#adapterForUbi)
- [QList\<BluezQt::AdapterPtr\> adapters() const](#adapters)
- [BluezQt::DevicePtr deviceForAddress(const QString &address) const](#deviceForAddress)
- [BluezQt::DevicePtr deviceForUbi(const QString &ubi) const](#deviceForUbi)
- [QList\<BluezQt::DevicePtr\> devices() const](#devices)
- [BluezQt::InitManagerJob \*init()](#init)
- [bool isBluetoothBlocked() const](#isBluetoothBlocked)
- [bool isBluetoothOperational() const](#isBluetoothOperational)
- [bool isInitialized() const](#isInitialized)
- [bool isOperational() const](#isOperational)
- [BluezQt::PendingCall \*registerAgent(BluezQt::Agent \*agent)](#registerAgent)
- [BluezQt::PendingCall \*registerProfile(BluezQt::Profile \*profile)](#registerProfile)
- [BluezQt::PendingCall \*requestDefaultAgent(BluezQt::Agent \*agent)](#requestDefaultAgent)
- [BluezQt::Rfkill \*rfkill() const](#rfkill)
- [void setBluetoothBlocked(bool blocked)](#setBluetoothBlocked)
- [BluezQt::PendingCall \*unregisterAgent(BluezQt::Agent \*agent)](#unregisterAgent)
- [BluezQt::PendingCall \*unregisterProfile(BluezQt::Profile \*profile)](#unregisterProfile)
- [BluezQt::AdapterPtr usableAdapter() const](#usableAdapter)

## Signals

- [void adapterAdded(BluezQt::AdapterPtr adapter)](#adapterAdded)
- [void adapterChanged(BluezQt::AdapterPtr adapter)](#adapterChanged)
- [void adapterRemoved(BluezQt::AdapterPtr adapter)](#adapterRemoved)
- [void allAdaptersRemoved()](#allAdaptersRemoved)
- [void bluetoothBlockedChanged(bool blocked)](#bluetoothBlockedChanged)
- [void bluetoothOperationalChanged(bool operational)](#bluetoothOperationalChanged)
- [void deviceAdded(BluezQt::DevicePtr device)](#deviceAdded)
- [void deviceChanged(BluezQt::DevicePtr device)](#deviceChanged)
- [void deviceRemoved(BluezQt::DevicePtr device)](#deviceRemoved)
- [void operationalChanged(bool operational)](#operationalChanged)
- [void usableAdapterChanged(BluezQt::AdapterPtr adapter)](#usableAdapterChanged)

## Static Public Members

- [BluezQt::PendingCall \*startService()](#startService)

## Detailed Description {#details}

The entry point to communicate with system BlueZ daemon.

The typical usecase is to work with [usableAdapter](bluezqt-manager.md#usableAdapter)() (any powered adapter), but it is also possible to use specific adapter.

You must call [init](bluezqt-manager.md#init)() before other functions can be used.

The only functions that can be used before initialization are two rfkill-related functions: [isBluetoothBlocked](bluezqt-manager.md#isBluetoothBlocked)() and [setBluetoothBlocked](bluezqt-manager.md#setBluetoothBlocked)().

Example use in C++ code:

```cpp
BluezQt::Manager *manager = new BluezQt::Manager();
BluezQt::InitManagerJob *job = manager->init();
job->start();
connect(job, &BluezQt::InitManagerJob::result, ...);
```

In QML, manager is a singleton and initialization is started when first using the manager. You don't need to track initialized state, just use property binding.

Example use in QML code:

```cpp
import QtQuick
import org.kde.bluezqt as BluezQt

Item {
    readonly property BluezQt.Manager manager: BluezQt.Manager
    property devicesCount: manager.devices.length
    property adaptersCount: manager.adapters.length

    Component.onCompleted: {
        console.log("Manager operational:", manager.operational)
    }
}
```

> **Note:** All communication with BlueZ daemon happens asynchronously. Almost all methods returns [PendingCall](bluezqt-pendingcall.md) to help track the call progress and to check for any errors.

> **Note:** If manager is not operational, all methods that returns a [PendingCall](bluezqt-pendingcall.md) will fail with [PendingCall::InternalError](bluezqt-pendingcall.md#Error-enum).

*See also* [InitManagerJob](bluezqt-initmanagerjob.md)

## Property Documentation {#property-documentation}

### \[read-only\] adapters : QList\<AdapterPtr\> {#adapters-prop}

**Access functions:**

- `QList`\<`BluezQt::AdapterPtr`\> **[adapters](bluezqt-manager.md#adapters)**() const

### bluetoothBlocked : bool {#bluetoothBlocked-prop}

**Access functions:**

- `bool` **[isBluetoothBlocked](bluezqt-manager.md#isBluetoothBlocked)**() const
- `void` **[setBluetoothBlocked](bluezqt-manager.md#setBluetoothBlocked)**(`bool` *blocked*)

**Notifier signal:**

- `void` **[bluetoothBlockedChanged](bluezqt-manager.md#bluetoothBlockedChanged)**(`bool` *blocked*)

### \[read-only\] bluetoothOperational : bool {#bluetoothOperational-prop}

**Access functions:**

- `bool` **[isBluetoothOperational](bluezqt-manager.md#isBluetoothOperational)**() const

**Notifier signal:**

- `void` **[bluetoothOperationalChanged](bluezqt-manager.md#bluetoothOperationalChanged)**(`bool` *operational*)

### \[read-only\] devices : QList\<DevicePtr\> {#devices-prop}

**Access functions:**

- `QList`\<`BluezQt::DevicePtr`\> **[devices](bluezqt-manager.md#devices)**() const

### \[read-only\] initialized : bool {#initialized-prop}

**Access functions:**

- `bool` **[isInitialized](bluezqt-manager.md#isInitialized)**() const

### \[read-only\] operational : bool {#operational-prop}

**Access functions:**

- `bool` **[isOperational](bluezqt-manager.md#isOperational)**() const

**Notifier signal:**

- `void` **[operationalChanged](bluezqt-manager.md#operationalChanged)**(`bool` *operational*)

### \[read-only\] rfkill : BluezQt::Rfkill\* const {#rfkill-prop}

**Access functions:**

- `BluezQt::Rfkill` \***[rfkill](bluezqt-manager.md#rfkill)**() const

### \[read-only\] usableAdapter : AdapterPtr {#usableAdapter-prop}

**Access functions:**

- `BluezQt::AdapterPtr` **[usableAdapter](bluezqt-manager.md#usableAdapter)**() const

**Notifier signal:**

- `void` **[usableAdapterChanged](bluezqt-manager.md#usableAdapterChanged)**(`BluezQt::AdapterPtr` *adapter*)

## Member Function Documentation {#member-function-documentation}

### \[explicit\] Manager::Manager(QObject \**parent* = nullptr) {#Manager}

Creates a new Manager object as a child of `parent`.

### \[signal\] void Manager::adapterAdded(BluezQt::AdapterPtr *adapter*) {#adapterAdded}

Indicates that an `adapter` was added.

### \[signal\] void Manager::adapterChanged(BluezQt::AdapterPtr *adapter*) {#adapterChanged}

Indicates that at least one of the `adapter`'s properties has changed.

### BluezQt::AdapterPtr Manager::adapterForAddress(const QString &*address*) const {#adapterForAddress}

Returns an adapter for the specified `address`.

`address` The address of adapter (eg. "1C:E5:C3:BC:94:7E").

### BluezQt::AdapterPtr Manager::adapterForUbi(const QString &*ubi*) const {#adapterForUbi}

Returns an adapter for specified UBI.

`ubi` The UBI of adapter (eg. "/org/bluez/hci0")

### \[signal\] void Manager::adapterRemoved(BluezQt::AdapterPtr *adapter*) {#adapterRemoved}

Indicates that an `adapter` was removed.

### QList\<BluezQt::AdapterPtr\> Manager::adapters() const {#adapters}

Returns a list of all adapters.

> **Note:** Getter function for property [adapters](bluezqt-manager.md#adapters-prop).

### \[signal\] void Manager::allAdaptersRemoved() {#allAdaptersRemoved}

Indicates that all adapters were removed.

### \[signal\] void Manager::bluetoothBlockedChanged(bool *blocked*) {#bluetoothBlockedChanged}

Indicates that Bluetooth `blocked` state has changed.

> **Note:** Notifier signal for property [bluetoothBlocked](bluezqt-manager.md#bluetoothBlocked-prop).

### \[signal\] void Manager::bluetoothOperationalChanged(bool *operational*) {#bluetoothOperationalChanged}

Indicates that the Bluetooth `operational` state has changed.

> **Note:** Notifier signal for property [bluetoothOperational](bluezqt-manager.md#bluetoothOperational-prop).

### \[signal\] void Manager::deviceAdded(BluezQt::DevicePtr *device*) {#deviceAdded}

Indicates that a new `device` was added (found by discovery).

### \[signal\] void Manager::deviceChanged(BluezQt::DevicePtr *device*) {#deviceChanged}

Indicates that at least one of the `device`'s properties has changed.

### BluezQt::DevicePtr Manager::deviceForAddress(const QString &*address*) const {#deviceForAddress}

Returns a device for the specified address.

> **Note:** There may be more devices with the same address (same device in multiple adapters). In this case, the first found device will be returned while preferring powered adapters in search.

`address` The address of device (eg. "40:79:6A:0C:39:75")

### BluezQt::DevicePtr Manager::deviceForUbi(const QString &*ubi*) const {#deviceForUbi}

Returns a device for specified UBI.

`ubi` The UBI of device (eg. "/org/bluez/hci0/dev\_40\_79\_6A\_0C\_39\_75")

### \[signal\] void Manager::deviceRemoved(BluezQt::DevicePtr *device*) {#deviceRemoved}

Indicates that a `device` was removed.

### QList\<BluezQt::DevicePtr\> Manager::devices() const {#devices}

Returns a list of all devices.

> **Note:** Getter function for property [devices](bluezqt-manager.md#devices-prop).

### BluezQt::InitManagerJob \*Manager::init() {#init}

Creates a new init job.

### bool Manager::isBluetoothBlocked() const {#isBluetoothBlocked}

Returns whether Bluetooth is blocked.

Bluetooth is blocked if rfkill state for Bluetooth is either SOFT\_BLOCKED or HARD\_BLOCKED.

> **Note:** This requires read access to /dev/rfkill.

> **Note:** Getter function for property [bluetoothBlocked](bluezqt-manager.md#bluetoothBlocked-prop).

### bool Manager::isBluetoothOperational() const {#isBluetoothOperational}

Returns whether Bluetooth is operational.

Bluetooth is operational when manager is operational and there is a valid usable adapter.

> **Note:** Getter function for property [bluetoothOperational](bluezqt-manager.md#bluetoothOperational-prop).

### bool Manager::isInitialized() const {#isInitialized}

Returns whether the manager is initialized.

> **Note:** Getter function for property [initialized](bluezqt-manager.md#initialized-prop).

### bool Manager::isOperational() const {#isOperational}

Returns whether the manager is operational.

The manager is operational when initialization was successful and BlueZ system daemon is running.

> **Note:** Getter function for property [operational](bluezqt-manager.md#operational-prop).

### \[signal\] void Manager::operationalChanged(bool *operational*) {#operationalChanged}

Indicates that the `operational` state has changed.

> **Note:** Notifier signal for property [operational](bluezqt-manager.md#operational-prop).

### BluezQt::PendingCall \*Manager::registerAgent(BluezQt::Agent \**agent*) {#registerAgent}

Registers an `agent`.

This agent will be used for for all actions triggered by the application. Eg. show a PIN code in pairing process.

Possible errors:

- [PendingCall::InvalidArguments](bluezqt-pendingcall.md#Error-enum)
- [PendingCall::AlreadyExists](bluezqt-pendingcall.md#Error-enum)

Returns void pending call.

### BluezQt::PendingCall \*Manager::registerProfile(BluezQt::Profile \**profile*) {#registerProfile}

Registers a `profile`.

Possible errors:

- [PendingCall::InvalidArguments](bluezqt-pendingcall.md#Error-enum)
- [PendingCall::AlreadyExists](bluezqt-pendingcall.md#Error-enum)

Returns void pending call.

### BluezQt::PendingCall \*Manager::requestDefaultAgent(BluezQt::Agent \**agent*) {#requestDefaultAgent}

Requests the default `agent`.

This requests to make the application agent the default agent.

Possible errors:

- [PendingCall::DoesNotExist](bluezqt-pendingcall.md#Error-enum)

Returns void pending call.

### BluezQt::Rfkill \*Manager::rfkill() const {#rfkill}

> **Note:** Getter function for property [rfkill](bluezqt-manager.md#rfkill-prop).

### void Manager::setBluetoothBlocked(bool *blocked*) {#setBluetoothBlocked}

Sets a Bluetooth blocked state.

This may fail either due to insufficient permissions or because rfkill state is HARD\_BLOCKED. In that case, this function returns false.

> **Note:** This requires write access to /dev/rfkill.

> **Note:** Setter function for property [bluetoothBlocked](bluezqt-manager.md#bluetoothBlocked-prop).

*See also* [isBluetoothBlocked](bluezqt-manager.md#isBluetoothBlocked)()

### \[static\] BluezQt::PendingCall \*Manager::startService() {#startService}

Attempts to start org.bluez service by D-Bus activation.

Possible return values are 1 if the service was started, 2 if the service is already running or error if the service could not be started.

Returns quint32 pending call.

### BluezQt::PendingCall \*Manager::unregisterAgent(BluezQt::Agent \**agent*) {#unregisterAgent}

Unregisters an `agent`.

Possible errors:

- [PendingCall::DoesNotExist](bluezqt-pendingcall.md#Error-enum)

Returns void pending call.

### BluezQt::PendingCall \*Manager::unregisterProfile(BluezQt::Profile \**profile*) {#unregisterProfile}

Unregisters a `profile`.

Possible errors:

- [PendingCall::DoesNotExist](bluezqt-pendingcall.md#Error-enum)

Returns void pending call.

### BluezQt::AdapterPtr Manager::usableAdapter() const {#usableAdapter}

Returns a usable adapter.

A usable adapter is any adapter that is currently powered on.

> **Note:** Getter function for property [usableAdapter](bluezqt-manager.md#usableAdapter-prop).

### \[signal\] void Manager::usableAdapterChanged(BluezQt::AdapterPtr *adapter*) {#usableAdapterChanged}

Indicates that a usable `adapter` has changed.

> **Note:** Notifier signal for property [usableAdapter](bluezqt-manager.md#usableAdapter-prop).
