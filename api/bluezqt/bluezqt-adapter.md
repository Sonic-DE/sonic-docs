---
title: "BluezQt::Adapter Class"
description: "Bluetooth adapter."
---

# BluezQt::Adapter Class

Bluetooth adapter. [More...](#details)

- **Header:** `#include <BluezQt/Adapter>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS BluezQt)`  
  `target_link_libraries(mytarget PRIVATE KF6::BluezQt)`
- **Inherits:** [QObject](https://doc.qt.io/qt-6/qobject.html)

[List of all members, including inherited members](bluezqt-adapter-members.md)

## Properties

- [\[read-only\] adapterClass : quint32](#adapterClass-prop)
- [\[read-only\] address : QString](#address-prop)
- [\[read-only\] devices : QList\<DevicePtr\>](#devices-prop)
- [discoverable : bool](#discoverable-prop)
- [discoverableTimeout : quint32](#discoverableTimeout-prop)
- [\[read-only\] discovering : bool](#discovering-prop)
- [\[read-only\] leAdvertisingManager : LEAdvertisingManagerPtr](#leAdvertisingManager-prop)
- [\[read-only\] media : MediaPtr](#media-prop)
- [\[read-only\] modalias : QString](#modalias-prop)
- [name : QString](#name-prop)
- [pairable : bool](#pairable-prop)
- [pairableTimeout : quint32](#pairableTimeout-prop)
- [powered : bool](#powered-prop)
- [\[read-only\] systemName : QString](#systemName-prop)
- [\[read-only\] ubi : QString](#ubi-prop)
- [\[read-only\] uuids : QStringList](#uuids-prop)

## Public Functions

- [quint32 adapterClass() const](#adapterClass)
- [QString address() const](#address)
- [BluezQt::DevicePtr deviceForAddress(const QString &address) const](#deviceForAddress)
- [QList\<BluezQt::DevicePtr\> devices() const](#devices)
- [quint32 discoverableTimeout() const](#discoverableTimeout)
- [BluezQt::GattManagerPtr gattManager() const](#gattManager)
- [BluezQt::PendingCall \*getDiscoveryFilters()](#getDiscoveryFilters)
- [bool isDiscoverable() const](#isDiscoverable)
- [bool isDiscovering()](#isDiscovering)
- [bool isPairable() const](#isPairable)
- [bool isPowered() const](#isPowered)
- [BluezQt::LEAdvertisingManagerPtr leAdvertisingManager() const](#leAdvertisingManager)
- [BluezQt::MediaPtr media() const](#media)
- [QString modalias() const](#modalias)
- [QString name() const](#name)
- [quint32 pairableTimeout() const](#pairableTimeout)
- [BluezQt::PendingCall \*removeDevice(BluezQt::DevicePtr device)](#removeDevice)
- [BluezQt::PendingCall \*setDiscoverable(bool discoverable)](#setDiscoverable)
- [BluezQt::PendingCall \*setDiscoverableTimeout(quint32 timeout)](#setDiscoverableTimeout)
- [BluezQt::PendingCall \*setDiscoveryFilter(const QVariantMap &filter)](#setDiscoveryFilter)
- [BluezQt::PendingCall \*setName(const QString &name)](#setName)
- [BluezQt::PendingCall \*setPairable(bool pairable)](#setPairable)
- [BluezQt::PendingCall \*setPairableTimeout(quint32 timeout)](#setPairableTimeout)
- [BluezQt::PendingCall \*setPowered(bool powered)](#setPowered)
- [BluezQt::PendingCall \*startDiscovery()](#startDiscovery)
- [BluezQt::PendingCall \*stopDiscovery()](#stopDiscovery)
- [QString systemName() const](#systemName)
- [BluezQt::AdapterPtr toSharedPtr() const](#toSharedPtr)
- [QString ubi() const](#ubi)
- [QStringList uuids() const](#uuids)

## Signals

- [void adapterChanged(BluezQt::AdapterPtr adapter)](#adapterChanged)
- [void adapterClassChanged(quint32 adapterClass)](#adapterClassChanged)
- [void adapterRemoved(BluezQt::AdapterPtr adapter)](#adapterRemoved)
- [void deviceAdded(BluezQt::DevicePtr device)](#deviceAdded)
- [void deviceChanged(BluezQt::DevicePtr device)](#deviceChanged)
- [void deviceRemoved(BluezQt::DevicePtr device)](#deviceRemoved)
- [void discoverableChanged(bool discoverable)](#discoverableChanged)
- [void discoverableTimeoutChanged(quint32 timeout)](#discoverableTimeoutChanged)
- [void discoveringChanged(bool discovering)](#discoveringChanged)
- [void gattManagerChanged(BluezQt::GattManagerPtr gattManager)](#gattManagerChanged)
- [void leAdvertisingManagerChanged(BluezQt::LEAdvertisingManagerPtr leAdvertisingManager)](#leAdvertisingManagerChanged)
- [void mediaChanged(BluezQt::MediaPtr media)](#mediaChanged)
- [void modaliasChanged(const QString &modalias)](#modaliasChanged)
- [void nameChanged(const QString &name)](#nameChanged)
- [void pairableChanged(bool pairable)](#pairableChanged)
- [void pairableTimeoutChanged(quint32 timeout)](#pairableTimeoutChanged)
- [void poweredChanged(bool powered)](#poweredChanged)
- [void systemNameChanged(const QString &systemName)](#systemNameChanged)
- [void uuidsChanged(const QStringList &uuids)](#uuidsChanged)

## Detailed Description {#details}

This class represents a Bluetooth adapter.

## Property Documentation {#property-documentation}

### \[read-only\] adapterClass : quint32 {#adapterClass-prop}

**Access functions:**

- `quint32` **[adapterClass](bluezqt-adapter.md#adapterClass)**() const

**Notifier signal:**

- `void` **[adapterClassChanged](bluezqt-adapter.md#adapterClassChanged)**(`quint32` *adapterClass*)

### \[read-only\] address : QString {#address-prop}

**Access functions:**

- `QString` **[address](bluezqt-adapter.md#address)**() const

### \[read-only\] devices : QList\<DevicePtr\> {#devices-prop}

**Access functions:**

- `QList`\<`BluezQt::DevicePtr`\> **[devices](bluezqt-adapter.md#devices)**() const

### discoverable : bool {#discoverable-prop}

**Access functions:**

- `bool` **[isDiscoverable](bluezqt-adapter.md#isDiscoverable)**() const
- `BluezQt::PendingCall` \***[setDiscoverable](bluezqt-adapter.md#setDiscoverable)**(`bool` *discoverable*)

**Notifier signal:**

- `void` **[discoverableChanged](bluezqt-adapter.md#discoverableChanged)**(`bool` *discoverable*)

### discoverableTimeout : quint32 {#discoverableTimeout-prop}

**Access functions:**

- `quint32` **[discoverableTimeout](bluezqt-adapter.md#discoverableTimeout)**() const
- `BluezQt::PendingCall` \***[setDiscoverableTimeout](bluezqt-adapter.md#setDiscoverableTimeout)**(`quint32` *timeout*)

**Notifier signal:**

- `void` **[discoverableTimeoutChanged](bluezqt-adapter.md#discoverableTimeoutChanged)**(`quint32` *timeout*)

### \[read-only\] discovering : bool {#discovering-prop}

**Access functions:**

- `bool` **[isDiscovering](bluezqt-adapter.md#isDiscovering)**()

**Notifier signal:**

- `void` **[discoveringChanged](bluezqt-adapter.md#discoveringChanged)**(`bool` *discovering*)

### \[read-only\] leAdvertisingManager : LEAdvertisingManagerPtr {#leAdvertisingManager-prop}

**Access functions:**

- `BluezQt::LEAdvertisingManagerPtr` **[leAdvertisingManager](bluezqt-adapter.md#leAdvertisingManager)**() const

**Notifier signal:**

- `void` **[leAdvertisingManagerChanged](bluezqt-adapter.md#leAdvertisingManagerChanged)**(`BluezQt::LEAdvertisingManagerPtr` *leAdvertisingManager*)

### \[read-only\] media : MediaPtr {#media-prop}

**Access functions:**

- `BluezQt::MediaPtr` **[media](bluezqt-adapter.md#media)**() const

**Notifier signal:**

- `void` **[mediaChanged](bluezqt-adapter.md#mediaChanged)**(`BluezQt::MediaPtr` *media*)

### \[read-only\] modalias : QString {#modalias-prop}

**Access functions:**

- `QString` **[modalias](bluezqt-adapter.md#modalias)**() const

**Notifier signal:**

- `void` **[modaliasChanged](bluezqt-adapter.md#modaliasChanged)**(const `QString` &*modalias*)

### name : QString {#name-prop}

**Access functions:**

- `QString` **[name](bluezqt-adapter.md#name)**() const
- `BluezQt::PendingCall` \***[setName](bluezqt-adapter.md#setName)**(const `QString` &*name*)

**Notifier signal:**

- `void` **[nameChanged](bluezqt-adapter.md#nameChanged)**(const `QString` &*name*)

### pairable : bool {#pairable-prop}

**Access functions:**

- `bool` **[isPairable](bluezqt-adapter.md#isPairable)**() const
- `BluezQt::PendingCall` \***[setPairable](bluezqt-adapter.md#setPairable)**(`bool` *pairable*)

**Notifier signal:**

- `void` **[pairableChanged](bluezqt-adapter.md#pairableChanged)**(`bool` *pairable*)

### pairableTimeout : quint32 {#pairableTimeout-prop}

**Access functions:**

- `quint32` **[pairableTimeout](bluezqt-adapter.md#pairableTimeout)**() const
- `BluezQt::PendingCall` \***[setPairableTimeout](bluezqt-adapter.md#setPairableTimeout)**(`quint32` *timeout*)

**Notifier signal:**

- `void` **[pairableTimeoutChanged](bluezqt-adapter.md#pairableTimeoutChanged)**(`quint32` *timeout*)

### powered : bool {#powered-prop}

**Access functions:**

- `bool` **[isPowered](bluezqt-adapter.md#isPowered)**() const
- `BluezQt::PendingCall` \***[setPowered](bluezqt-adapter.md#setPowered)**(`bool` *powered*)

**Notifier signal:**

- `void` **[poweredChanged](bluezqt-adapter.md#poweredChanged)**(`bool` *powered*)

### \[read-only\] systemName : QString {#systemName-prop}

**Access functions:**

- `QString` **[systemName](bluezqt-adapter.md#systemName)**() const

**Notifier signal:**

- `void` **[systemNameChanged](bluezqt-adapter.md#systemNameChanged)**(const `QString` &*systemName*)

### \[read-only\] ubi : QString {#ubi-prop}

**Access functions:**

- `QString` **[ubi](bluezqt-adapter.md#ubi)**() const

### \[read-only\] uuids : QStringList {#uuids-prop}

**Access functions:**

- `QStringList` **[uuids](bluezqt-adapter.md#uuids)**() const

**Notifier signal:**

- `void` **[uuidsChanged](bluezqt-adapter.md#uuidsChanged)**(const `QStringList` &*uuids*)

## Member Function Documentation {#member-function-documentation}

### \[signal\] void Adapter::adapterChanged(BluezQt::AdapterPtr *adapter*) {#adapterChanged}

Indicates that at least one of the adapter's properties have changed.

### quint32 Adapter::adapterClass() const {#adapterClass}

Returns a class of the adapter.

> **Note:** Getter function for property [adapterClass](bluezqt-adapter.md#adapterClass-prop).

### \[signal\] void Adapter::adapterClassChanged(quint32 *adapterClass*) {#adapterClassChanged}

Indicates that adapter's class has changed.

> **Note:** Notifier signal for property [adapterClass](bluezqt-adapter.md#adapterClass-prop).

### \[signal\] void Adapter::adapterRemoved(BluezQt::AdapterPtr *adapter*) {#adapterRemoved}

Indicates that the adapter was removed.

### QString Adapter::address() const {#address}

Returns an address of the adapter.

Example address: "1C:E5:C3:BC:94:7E"

> **Note:** Getter function for property [address](bluezqt-adapter.md#address-prop).

### \[signal\] void Adapter::deviceAdded(BluezQt::DevicePtr *device*) {#deviceAdded}

Indicates that a new device was added (e.g. found by discovery).

### \[signal\] void Adapter::deviceChanged(BluezQt::DevicePtr *device*) {#deviceChanged}

Indicates that at least one of the device's properties has changed.

### BluezQt::DevicePtr Adapter::deviceForAddress(const QString &*address*) const {#deviceForAddress}

Returns a device with the specified `address`.

The `address` follows a scheme similar to "40:79:6A:0C:39:75".

Returns null if there is no device with the specified address.

### \[signal\] void Adapter::deviceRemoved(BluezQt::DevicePtr *device*) {#deviceRemoved}

Indicates that a device was removed.

### QList\<BluezQt::DevicePtr\> Adapter::devices() const {#devices}

Returns list of devices known by the adapter.

> **Note:** Getter function for property [devices](bluezqt-adapter.md#devices-prop).

### \[signal\] void Adapter::discoverableChanged(bool *discoverable*) {#discoverableChanged}

Indicates that adapter's discoverable state has changed.

> **Note:** Notifier signal for property [discoverable](bluezqt-adapter.md#discoverable-prop).

### quint32 Adapter::discoverableTimeout() const {#discoverableTimeout}

Returns the discoverable timeout in seconds of the adapter.

The discoverable timeout defines how long the adapter stays in discoverable state after calling [setDiscoverable](bluezqt-adapter.md#setDiscoverable)(true).

Timeout 0 means infinitely.

> **Note:** Getter function for property [discoverableTimeout](bluezqt-adapter.md#discoverableTimeout-prop).

*See also* [setDiscoverableTimeout](bluezqt-adapter.md#setDiscoverableTimeout)()

### \[signal\] void Adapter::discoverableTimeoutChanged(quint32 *timeout*) {#discoverableTimeoutChanged}

Indicates that adapter's discoverable timeout has changed.

> **Note:** Notifier signal for property [discoverableTimeout](bluezqt-adapter.md#discoverableTimeout-prop).

### \[signal\] void Adapter::discoveringChanged(bool *discovering*) {#discoveringChanged}

Indicates that adapter's discovering state has changed.

> **Note:** Notifier signal for property [discovering](bluezqt-adapter.md#discovering-prop).

### BluezQt::GattManagerPtr Adapter::gattManager() const {#gattManager}

Returns the GATT manager interface for the adapter.

Returns null if the adapter has no GATT manager.

### \[signal\] void Adapter::gattManagerChanged(BluezQt::GattManagerPtr *gattManager*) {#gattManagerChanged}

Indicates that adapter's GATT manager has changed.

### BluezQt::PendingCall \*Adapter::getDiscoveryFilters() {#getDiscoveryFilters}

Gets the discovery filters for the caller.

This returns the available filters that can be given to [setDiscoveryFilter](bluezqt-adapter.md#setDiscoveryFilter).

For details and available filter options, see the [Bluez documentation for Adapter object](https://git.kernel.org/pub/scm/bluetooth/bluez.git/tree/doc/adapter-api.txt).

Possible errors:

- [PendingCall::Failed](bluezqt-pendingcall.md#Error-enum)

Returns string list pending call.

### bool Adapter::isDiscoverable() const {#isDiscoverable}

Returns whether the adapter is discoverable by other devices.

> **Note:** Getter function for property [discoverable](bluezqt-adapter.md#discoverable-prop).

### bool Adapter::isDiscovering() {#isDiscovering}

Returns whether the adapter is discovering for other devices.

> **Note:** Getter function for property [discovering](bluezqt-adapter.md#discovering-prop).

### bool Adapter::isPairable() const {#isPairable}

Returns whether the adapter is pairable with other devices.

> **Note:** Getter function for property [pairable](bluezqt-adapter.md#pairable-prop).

### bool Adapter::isPowered() const {#isPowered}

Returns whether the adapter is powered on.

> **Note:** Getter function for property [powered](bluezqt-adapter.md#powered-prop).

### BluezQt::LEAdvertisingManagerPtr Adapter::leAdvertisingManager() const {#leAdvertisingManager}

Returns the LE advertising manager interface for the adapter.

Returns null if the adapter has no Bluetooth LE.

> **Note:** Getter function for property [leAdvertisingManager](bluezqt-adapter.md#leAdvertisingManager-prop).

### \[signal\] void Adapter::leAdvertisingManagerChanged(BluezQt::LEAdvertisingManagerPtr *leAdvertisingManager*) {#leAdvertisingManagerChanged}

Indicates that adapter's LE advertising manager has changed.

> **Note:** Notifier signal for property [leAdvertisingManager](bluezqt-adapter.md#leAdvertisingManager-prop).

### BluezQt::MediaPtr Adapter::media() const {#media}

Returns the media interface for the adapter.

Returns null if the adapter has no media.

> **Note:** Getter function for property [media](bluezqt-adapter.md#media-prop).

### \[signal\] void Adapter::mediaChanged(BluezQt::MediaPtr *media*) {#mediaChanged}

Indicates that adapter's media has changed.

> **Note:** Notifier signal for property [media](bluezqt-adapter.md#media-prop).

### QString Adapter::modalias() const {#modalias}

Returns local device ID in modalias format.

> **Note:** Getter function for property [modalias](bluezqt-adapter.md#modalias-prop).

### \[signal\] void Adapter::modaliasChanged(const QString &*modalias*) {#modaliasChanged}

Indicates that adapter's modalias has changed.

> **Note:** Notifier signal for property [modalias](bluezqt-adapter.md#modalias-prop).

### QString Adapter::name() const {#name}

Returns the name of the adapter.

> **Note:** Getter function for property [name](bluezqt-adapter.md#name-prop).

*See also* [setName](bluezqt-adapter.md#setName)()

### \[signal\] void Adapter::nameChanged(const QString &*name*) {#nameChanged}

Indicates that adapter's name has changed.

> **Note:** Notifier signal for property [name](bluezqt-adapter.md#name-prop).

### \[signal\] void Adapter::pairableChanged(bool *pairable*) {#pairableChanged}

Indicates that adapter's pairable state has changed.

> **Note:** Notifier signal for property [pairable](bluezqt-adapter.md#pairable-prop).

### quint32 Adapter::pairableTimeout() const {#pairableTimeout}

Returns the pairable timeout in seconds of the adapter.

The pairable timeout defines how long the adapter stays in pairable state after calling [setPairable](bluezqt-adapter.md#setPairable)(true).

Timeout 0 means infinitely.

> **Note:** Getter function for property [pairableTimeout](bluezqt-adapter.md#pairableTimeout-prop).

*See also* [setPairableTimeout](bluezqt-adapter.md#setPairableTimeout)()

### \[signal\] void Adapter::pairableTimeoutChanged(quint32 *timeout*) {#pairableTimeoutChanged}

Indicates that adapter's pairable timeout has changed.

> **Note:** Notifier signal for property [pairableTimeout](bluezqt-adapter.md#pairableTimeout-prop).

### \[signal\] void Adapter::poweredChanged(bool *powered*) {#poweredChanged}

Indicates that adapter's powered state has changed.

> **Note:** Notifier signal for property [powered](bluezqt-adapter.md#powered-prop).

### BluezQt::PendingCall \*Adapter::removeDevice(BluezQt::DevicePtr *device*) {#removeDevice}

Removes the specified `device`.

It will also remove the pairing information.

Possible errors:

- [PendingCall::InvalidArguments](bluezqt-pendingcall.md#Error-enum)
- [PendingCall::Failed](bluezqt-pendingcall.md#Error-enum)

Returns void pending call.

### BluezQt::PendingCall \*Adapter::setDiscoverable(bool *discoverable*) {#setDiscoverable}

Sets the `discoverable` state of the adapter.

Returns void pending call.

> **Note:** Setter function for property [discoverable](bluezqt-adapter.md#discoverable-prop).

*See also* [isDiscoverable](bluezqt-adapter.md#isDiscoverable)()

### BluezQt::PendingCall \*Adapter::setDiscoverableTimeout(quint32 *timeout*) {#setDiscoverableTimeout}

Sets the discoverable `timeout` of the adapter in seconds.

Returns void pending call.

> **Note:** Setter function for property [discoverableTimeout](bluezqt-adapter.md#discoverableTimeout-prop).

*See also* [discoverableTimeout](bluezqt-adapter.md#discoverableTimeout)()

### BluezQt::PendingCall \*Adapter::setDiscoveryFilter(const QVariantMap &*filter*) {#setDiscoveryFilter}

Sets the discovery `filter` for the caller.

When this method is called with no filter parameter, the filter is removed.

For details and available filter options, see the [Bluez documentation for Adapter object](https://git.kernel.org/pub/scm/bluetooth/bluez.git/tree/doc/adapter-api.txt).

Possible errors:

- [PendingCall::InvalidArguments](bluezqt-pendingcall.md#Error-enum)
- [PendingCall::Failed](bluezqt-pendingcall.md#Error-enum)

Returns void pending call.

### BluezQt::PendingCall \*Adapter::setName(const QString &*name*) {#setName}

Sets the `name` of the adapter.

Returns void pending call.

> **Note:** Setter function for property [name](bluezqt-adapter.md#name-prop).

*See also* [name](bluezqt-adapter.md#name)()

### BluezQt::PendingCall \*Adapter::setPairable(bool *pairable*) {#setPairable}

Sets the `pairable` state of the adapter.

Returns void pending call.

> **Note:** Setter function for property [pairable](bluezqt-adapter.md#pairable-prop).

*See also* [isPairable](bluezqt-adapter.md#isPairable)()

### BluezQt::PendingCall \*Adapter::setPairableTimeout(quint32 *timeout*) {#setPairableTimeout}

Sets the pairable `timeout` of the adapter in seconds.

Returns void pending call.

> **Note:** Setter function for property [pairableTimeout](bluezqt-adapter.md#pairableTimeout-prop).

*See also* [pairableTimeout](bluezqt-adapter.md#pairableTimeout)()

### BluezQt::PendingCall \*Adapter::setPowered(bool *powered*) {#setPowered}

Sets the `powered` state of the adapter.

Returns void pending call.

> **Note:** Setter function for property [powered](bluezqt-adapter.md#powered-prop).

*See also* [isPowered](bluezqt-adapter.md#isPowered)()

### BluezQt::PendingCall \*Adapter::startDiscovery() {#startDiscovery}

Starts device discovery.

Possible errors:

- [PendingCall::NotReady](bluezqt-pendingcall.md#Error-enum)
- [PendingCall::Failed](bluezqt-pendingcall.md#Error-enum)

Returns void pending call.

*See also* [discoverableTimeout](bluezqt-adapter.md#discoverableTimeout)()

### BluezQt::PendingCall \*Adapter::stopDiscovery() {#stopDiscovery}

Stops device discovery.

Possible errors:

- [PendingCall::NotReady](bluezqt-pendingcall.md#Error-enum)
- [PendingCall::Failed](bluezqt-pendingcall.md#Error-enum)
- [PendingCall::NotAuthorized](bluezqt-pendingcall.md#Error-enum)

Returns void pending call.

### QString Adapter::systemName() const {#systemName}

Returns a system name (hostname) of the adapter.

> **Note:** Getter function for property [systemName](bluezqt-adapter.md#systemName-prop).

### \[signal\] void Adapter::systemNameChanged(const QString &*systemName*) {#systemNameChanged}

Indicates that adapter's system name has changed.

> **Note:** Notifier signal for property [systemName](bluezqt-adapter.md#systemName-prop).

### BluezQt::AdapterPtr Adapter::toSharedPtr() const {#toSharedPtr}

Returns a shared pointer from this.

### QString Adapter::ubi() const {#ubi}

Returns an UBI of the adapter.

Example UBI: "/org/bluez/hci0"

> **Note:** Getter function for property [ubi](bluezqt-adapter.md#ubi-prop).

### QStringList Adapter::uuids() const {#uuids}

Returns UUIDs of supported services by the adapter in uppercase.

> **Note:** Getter function for property [uuids](bluezqt-adapter.md#uuids-prop).

### \[signal\] void Adapter::uuidsChanged(const QStringList &*uuids*) {#uuidsChanged}

Indicates that adapter's UUIDs has changed.

> **Note:** Notifier signal for property [uuids](bluezqt-adapter.md#uuids-prop).
