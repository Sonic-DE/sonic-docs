---
title: "BluezQt::Device Class"
description: "Bluetooth device."
---

# BluezQt::Device Class

Bluetooth device. [More...](#details)

- **Header:** `#include <BluezQt/Device>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS BluezQt)`  
  `target_link_libraries(mytarget PRIVATE KF6::BluezQt)`
- **Inherits:** [QObject](https://doc.qt.io/qt-6/qobject.html)

[List of all members, including inherited members](bluezqt-device-members.md)

## Public Types

- [enum Device::Type](#Type-enum)

## Properties

- [\[read-only\] adapter : AdapterPtr](#adapter-prop)
- [\[read-only\] address : QString](#address-prop)
- [\[read-only\] appearance : quint16](#appearance-prop)
- [\[read-only\] battery : BatteryPtr](#battery-prop)
- [blocked : bool](#blocked-prop)
- [\[read-only\] connected : bool](#connected-prop)
- [\[read-only\] deviceClass : quint32](#deviceClass-prop)
- [\[read-only\] friendlyName : QString](#friendlyName-prop)
- [\[read-only\] gattServices : QList\<GattServiceRemotePtr\>](#gattServices-prop)
- [\[read-only\] icon : QString](#icon-prop)
- [\[read-only\] input : InputPtr](#input-prop)
- [\[read-only\] legacyPairing : bool](#legacyPairing-prop)
- [\[read-only\] manufacturerData : ManData](#manufacturerData-prop)
- [\[read-only\] mediaPlayer : MediaPlayerPtr](#mediaPlayer-prop)
- [\[read-only\] mediaTransport : MediaTransportPtr](#mediaTransport-prop)
- [\[read-only\] modalias : QString](#modalias-prop)
- [name : QString](#name-prop)
- [\[read-only\] paired : bool](#paired-prop)
- [\[read-only\] remoteName : QString](#remoteName-prop)
- [\[read-only\] rssi : qint16](#rssi-prop)
- [\[read-only\] servicesResolved : bool](#servicesResolved-prop)
- [trusted : bool](#trusted-prop)
- [\[read-only\] type : Type](#type-prop)
- [\[read-only\] ubi : QString](#ubi-prop)
- [\[read-only\] uuids : QStringList](#uuids-prop)

## Public Functions

- [BluezQt::AdapterPtr adapter() const](#adapter)
- [QString address() const](#address)
- [quint16 appearance() const](#appearance)
- [BluezQt::BatteryPtr battery() const](#battery)
- [quint32 deviceClass() const](#deviceClass)
- [QString friendlyName() const](#friendlyName)
- [QList\<BluezQt::GattServiceRemotePtr\> gattServices() const](#gattServices)
- [bool hasLegacyPairing() const](#hasLegacyPairing)
- [QString icon() const](#icon)
- [BluezQt::InputPtr input() const](#input)
- [bool isBlocked() const](#isBlocked)
- [bool isConnected() const](#isConnected)
- [bool isPaired() const](#isPaired)
- [bool isServicesResolved() const](#isServicesResolved)
- [bool isTrusted() const](#isTrusted)
- [BluezQt::ManData manufacturerData() const](#manufacturerData)
- [BluezQt::MediaPlayerPtr mediaPlayer() const](#mediaPlayer)
- [BluezQt::MediaTransportPtr mediaTransport() const](#mediaTransport)
- [QString modalias() const](#modalias)
- [QString name() const](#name)
- [QString remoteName() const](#remoteName)
- [qint16 rssi() const](#rssi)
- [QHash\<QString, QByteArray\> serviceData() const](#serviceData)
- [BluezQt::PendingCall \*setBlocked(bool blocked)](#setBlocked)
- [BluezQt::PendingCall \*setName(const QString &name)](#setName)
- [BluezQt::PendingCall \*setTrusted(bool trusted)](#setTrusted)
- [BluezQt::DevicePtr toSharedPtr() const](#toSharedPtr)
- [BluezQt::Device::Type type() const](#type)
- [QString ubi() const](#ubi)
- [QStringList uuids() const](#uuids)

## Public Slots

- [BluezQt::PendingCall \*cancelPairing()](#cancelPairing)
- [BluezQt::PendingCall \*connectProfile(const QString &uuid)](#connectProfile)
- [BluezQt::PendingCall \*connectToDevice()](#connectToDevice)
- [BluezQt::PendingCall \*disconnectFromDevice()](#disconnectFromDevice)
- [BluezQt::PendingCall \*disconnectProfile(const QString &uuid)](#disconnectProfile)
- [BluezQt::PendingCall \*pair()](#pair)

## Signals

- [void addressChanged(const QString &address)](#addressChanged)
- [void appearanceChanged(quint16 appearance)](#appearanceChanged)
- [void batteryChanged(BluezQt::BatteryPtr battery)](#batteryChanged)
- [void blockedChanged(bool blocked)](#blockedChanged)
- [void connectedChanged(bool connected)](#connectedChanged)
- [void deviceChanged(BluezQt::DevicePtr device)](#deviceChanged)
- [void deviceClassChanged(quint32 deviceClass)](#deviceClassChanged)
- [void deviceRemoved(BluezQt::DevicePtr device)](#deviceRemoved)
- [void friendlyNameChanged(const QString &friendlyName)](#friendlyNameChanged)
- [void gattServiceAdded(BluezQt::GattServiceRemotePtr service)](#gattServiceAdded)
- [void gattServiceChanged(BluezQt::GattServiceRemotePtr service)](#gattServiceChanged)
- [void gattServiceRemoved(BluezQt::GattServiceRemotePtr service)](#gattServiceRemoved)
- [void gattServicesChanged(QList\<BluezQt::GattServiceRemotePtr\> services)](#gattServicesChanged)
- [void iconChanged(const QString &icon)](#iconChanged)
- [void inputChanged(BluezQt::InputPtr input)](#inputChanged)
- [void legacyPairingChanged(bool legacyPairing)](#legacyPairingChanged)
- [void manufacturerDataChanged(BluezQt::ManData man)](#manufacturerDataChanged)
- [void mediaPlayerChanged(BluezQt::MediaPlayerPtr mediaPlayer)](#mediaPlayerChanged)
- [void mediaTransportChanged(BluezQt::MediaTransportPtr mediaTransport)](#mediaTransportChanged)
- [void modaliasChanged(const QString &modalias)](#modaliasChanged)
- [void nameChanged(const QString &name)](#nameChanged)
- [void pairedChanged(bool paired)](#pairedChanged)
- [void remoteNameChanged(const QString &remoteName)](#remoteNameChanged)
- [void rssiChanged(qint16 rssi)](#rssiChanged)
- [void serviceDataChanged(const QHash\<QString, QByteArray\> &serviceData)](#serviceDataChanged)
- [void servicesResolvedChanged(bool servicesResolved)](#servicesResolvedChanged)
- [void trustedChanged(bool trusted)](#trustedChanged)
- [void typeChanged(BluezQt::Device::Type type)](#typeChanged)
- [void uuidsChanged(const QStringList &uuids)](#uuidsChanged)

## Static Public Members

- [BluezQt::Device::Type stringToType(const QString &typeString)](#stringToType)
- [QString typeToString(BluezQt::Device::Type type)](#typeToString)

## Detailed Description {#details}

This class represents a Bluetooth device.

## Member Type Documentation {#member-type-documentation}

### enum Device::Type {#Type-enum}

Device types.

| Constant | Value | Description |
| --- | --- | --- |
| `BluezQt::Device::Phone` | `0` | The device is a phone. |
| `BluezQt::Device::Modem` | `1` | The device is a modem. |
| `BluezQt::Device::Computer` | `2` | The device is a computer. |
| `BluezQt::Device::Network` | `3` | The device is a computer. |
| `BluezQt::Device::Headset` | `4` | The device is a headset. |
| `BluezQt::Device::Headphones` | `5` | The device is a headphone. |
| `BluezQt::Device::AudioVideo` | `6` | The device is an uncategorized audio/video device. |
| `BluezQt::Device::Keyboard` | `7` | The device is a keyboard. |
| `BluezQt::Device::Mouse` | `8` | The device is a mouse. |
| `BluezQt::Device::Joypad` | `9` | The device is a joypad. |
| `BluezQt::Device::Tablet` | `10` | The device is a graphics tablet (input device). |
| `BluezQt::Device::Peripheral` | `11` | The device is an uncategorized peripheral device. |
| `BluezQt::Device::Camera` | `12` | The device is a camera. |
| `BluezQt::Device::Printer` | `13` | The device is a printer. |
| `BluezQt::Device::Imaging` | `14` | The device is an uncategorized imaging device. |
| `BluezQt::Device::Wearable` | `15` | The device is a wearable device. |
| `BluezQt::Device::Toy` | `16` | The device is a toy. |
| `BluezQt::Device::Health` | `17` | The device is a health device. |
| `BluezQt::Device::Uncategorized` | `18` | The device is not of any of the known types. |

## Property Documentation {#property-documentation}

### \[read-only\] adapter : AdapterPtr {#adapter-prop}

**Access functions:**

- `BluezQt::AdapterPtr` **[adapter](bluezqt-device.md#adapter)**() const

### \[read-only\] address : QString {#address-prop}

**Access functions:**

- `QString` **[address](bluezqt-device.md#address)**() const

**Notifier signal:**

- `void` **[addressChanged](bluezqt-device.md#addressChanged)**(const `QString` &*address*)

### \[read-only\] appearance : quint16 {#appearance-prop}

**Access functions:**

- `quint16` **[appearance](bluezqt-device.md#appearance)**() const

**Notifier signal:**

- `void` **[appearanceChanged](bluezqt-device.md#appearanceChanged)**(`quint16` *appearance*)

### \[read-only\] battery : BatteryPtr {#battery-prop}

**Access functions:**

- `BluezQt::BatteryPtr` **[battery](bluezqt-device.md#battery)**() const

**Notifier signal:**

- `void` **[batteryChanged](bluezqt-device.md#batteryChanged)**(`BluezQt::BatteryPtr` *battery*)

### blocked : bool {#blocked-prop}

**Access functions:**

- `bool` **[isBlocked](bluezqt-device.md#isBlocked)**() const
- `BluezQt::PendingCall` \***[setBlocked](bluezqt-device.md#setBlocked)**(`bool` *blocked*)

**Notifier signal:**

- `void` **[blockedChanged](bluezqt-device.md#blockedChanged)**(`bool` *blocked*)

### \[read-only\] connected : bool {#connected-prop}

**Access functions:**

- `bool` **[isConnected](bluezqt-device.md#isConnected)**() const

**Notifier signal:**

- `void` **[connectedChanged](bluezqt-device.md#connectedChanged)**(`bool` *connected*)

### \[read-only\] deviceClass : quint32 {#deviceClass-prop}

**Access functions:**

- `quint32` **[deviceClass](bluezqt-device.md#deviceClass)**() const

**Notifier signal:**

- `void` **[deviceClassChanged](bluezqt-device.md#deviceClassChanged)**(`quint32` *deviceClass*)

### \[read-only\] friendlyName : QString {#friendlyName-prop}

**Access functions:**

- `QString` **[friendlyName](bluezqt-device.md#friendlyName)**() const

**Notifier signal:**

- `void` **[friendlyNameChanged](bluezqt-device.md#friendlyNameChanged)**(const `QString` &*friendlyName*)

### \[read-only\] gattServices : QList\<GattServiceRemotePtr\> {#gattServices-prop}

**Access functions:**

- `QList`\<`BluezQt::GattServiceRemotePtr`\> **[gattServices](bluezqt-device.md#gattServices)**() const

**Notifier signal:**

- `void` **[gattServicesChanged](bluezqt-device.md#gattServicesChanged)**(`QList`\<`BluezQt::GattServiceRemotePtr`\> *services*)

### \[read-only\] icon : QString {#icon-prop}

**Access functions:**

- `QString` **[icon](bluezqt-device.md#icon)**() const

**Notifier signal:**

- `void` **[iconChanged](bluezqt-device.md#iconChanged)**(const `QString` &*icon*)

### \[read-only\] input : InputPtr {#input-prop}

**Access functions:**

- `BluezQt::InputPtr` **[input](bluezqt-device.md#input)**() const

**Notifier signal:**

- `void` **[inputChanged](bluezqt-device.md#inputChanged)**(`BluezQt::InputPtr` *input*)

### \[read-only\] legacyPairing : bool {#legacyPairing-prop}

**Access functions:**

- `bool` **[hasLegacyPairing](bluezqt-device.md#hasLegacyPairing)**() const

**Notifier signal:**

- `void` **[legacyPairingChanged](bluezqt-device.md#legacyPairingChanged)**(`bool` *legacyPairing*)

### \[read-only\] manufacturerData : ManData {#manufacturerData-prop}

**Access functions:**

- `BluezQt::ManData` **[manufacturerData](bluezqt-device.md#manufacturerData)**() const

**Notifier signal:**

- `void` **[manufacturerDataChanged](bluezqt-device.md#manufacturerDataChanged)**(`BluezQt::ManData` *man*)

### \[read-only\] mediaPlayer : MediaPlayerPtr {#mediaPlayer-prop}

**Access functions:**

- `BluezQt::MediaPlayerPtr` **[mediaPlayer](bluezqt-device.md#mediaPlayer)**() const

**Notifier signal:**

- `void` **[mediaPlayerChanged](bluezqt-device.md#mediaPlayerChanged)**(`BluezQt::MediaPlayerPtr` *mediaPlayer*)

### \[read-only\] mediaTransport : MediaTransportPtr {#mediaTransport-prop}

**Access functions:**

- `BluezQt::MediaTransportPtr` **[mediaTransport](bluezqt-device.md#mediaTransport)**() const

**Notifier signal:**

- `void` **[mediaTransportChanged](bluezqt-device.md#mediaTransportChanged)**(`BluezQt::MediaTransportPtr` *mediaTransport*)

### \[read-only\] modalias : QString {#modalias-prop}

**Access functions:**

- `QString` **[modalias](bluezqt-device.md#modalias)**() const

**Notifier signal:**

- `void` **[modaliasChanged](bluezqt-device.md#modaliasChanged)**(const `QString` &*modalias*)

### name : QString {#name-prop}

**Access functions:**

- `QString` **[name](bluezqt-device.md#name)**() const
- `BluezQt::PendingCall` \***[setName](bluezqt-device.md#setName)**(const `QString` &*name*)

**Notifier signal:**

- `void` **[nameChanged](bluezqt-device.md#nameChanged)**(const `QString` &*name*)

### \[read-only\] paired : bool {#paired-prop}

**Access functions:**

- `bool` **[isPaired](bluezqt-device.md#isPaired)**() const

**Notifier signal:**

- `void` **[pairedChanged](bluezqt-device.md#pairedChanged)**(`bool` *paired*)

### \[read-only\] remoteName : QString {#remoteName-prop}

**Access functions:**

- `QString` **[remoteName](bluezqt-device.md#remoteName)**() const

**Notifier signal:**

- `void` **[remoteNameChanged](bluezqt-device.md#remoteNameChanged)**(const `QString` &*remoteName*)

### \[read-only\] rssi : qint16 {#rssi-prop}

**Access functions:**

- `qint16` **[rssi](bluezqt-device.md#rssi)**() const

**Notifier signal:**

- `void` **[rssiChanged](bluezqt-device.md#rssiChanged)**(`qint16` *rssi*)

### \[read-only\] servicesResolved : bool {#servicesResolved-prop}

**Access functions:**

- `bool` **[isServicesResolved](bluezqt-device.md#isServicesResolved)**() const

**Notifier signal:**

- `void` **[servicesResolvedChanged](bluezqt-device.md#servicesResolvedChanged)**(`bool` *servicesResolved*)

### trusted : bool {#trusted-prop}

**Access functions:**

- `bool` **[isTrusted](bluezqt-device.md#isTrusted)**() const
- `BluezQt::PendingCall` \***[setTrusted](bluezqt-device.md#setTrusted)**(`bool` *trusted*)

**Notifier signal:**

- `void` **[trustedChanged](bluezqt-device.md#trustedChanged)**(`bool` *trusted*)

### \[read-only\] type : Type {#type-prop}

**Access functions:**

- `BluezQt::Device::Type` **[type](bluezqt-device.md#type)**() const

**Notifier signal:**

- `void` **[typeChanged](bluezqt-device.md#typeChanged)**(`BluezQt::Device::Type` *type*)

### \[read-only\] ubi : QString {#ubi-prop}

**Access functions:**

- `QString` **[ubi](bluezqt-device.md#ubi)**() const

### \[read-only\] uuids : QStringList {#uuids-prop}

**Access functions:**

- `QStringList` **[uuids](bluezqt-device.md#uuids)**() const

**Notifier signal:**

- `void` **[uuidsChanged](bluezqt-device.md#uuidsChanged)**(const `QStringList` &*uuids*)

## Member Function Documentation {#member-function-documentation}

### BluezQt::AdapterPtr Device::adapter() const {#adapter}

Returns the adapter that discovered this device.

> **Note:** Getter function for property [adapter](bluezqt-device.md#adapter-prop).

### QString Device::address() const {#address}

Returns the address of the device.

Example address: "40:79:6A:0C:39:75"

> **Note:** Getter function for property [address](bluezqt-device.md#address-prop).

### \[signal\] void Device::addressChanged(const QString &*address*) {#addressChanged}

Indicates that the device's address has changed.

> **Note:** Notifier signal for property [address](bluezqt-device.md#address-prop).

### quint16 Device::appearance() const {#appearance}

Returns the appearance of the device.

> **Note:** Getter function for property [appearance](bluezqt-device.md#appearance-prop).

### \[signal\] void Device::appearanceChanged(quint16 *appearance*) {#appearanceChanged}

Indicates that the device's appearance has changed.

> **Note:** Notifier signal for property [appearance](bluezqt-device.md#appearance-prop).

### BluezQt::BatteryPtr Device::battery() const {#battery}

Returns the battery interface for the device.

Returns null if device has no battery.

> **Note:** Getter function for property [battery](bluezqt-device.md#battery-prop).

### \[signal\] void Device::batteryChanged(BluezQt::BatteryPtr *battery*) {#batteryChanged}

Indicates that the device's battery has changed.

> **Note:** Notifier signal for property [battery](bluezqt-device.md#battery-prop).

### \[signal\] void Device::blockedChanged(bool *blocked*) {#blockedChanged}

Indicates that the device's blocked state has changed.

> **Note:** Notifier signal for property [blocked](bluezqt-device.md#blocked-prop).

### \[slot\] BluezQt::PendingCall \*Device::cancelPairing() {#cancelPairing}

Cancels a pairing with the device.

This method can be used to cancel pairing operation initiated with [pair](bluezqt-device.md#pair)().

Possible errors:

- [PendingCall::DoesNotExist](bluezqt-pendingcall.md#Error-enum)
- [PendingCall::Failed](bluezqt-pendingcall.md#Error-enum)

Returns void pending call.

### \[slot\] BluezQt::PendingCall \*Device::connectProfile(const QString &*uuid*) {#connectProfile}

Connects a specific profile of the device with the given service `uuid`.

Possible errors:

- [PendingCall::DoesNotExist](bluezqt-pendingcall.md#Error-enum)
- [PendingCall::AlreadyConnected](bluezqt-pendingcall.md#Error-enum)
- [PendingCall::ConnectFailed](bluezqt-pendingcall.md#Error-enum)

Returns void pending call.

### \[slot\] BluezQt::PendingCall \*Device::connectToDevice() {#connectToDevice}

Connects all auto-connectable profiles of the device.

This method indicates success if at least one profile was connected.

Possible errors:

- [PendingCall::NotReady](bluezqt-pendingcall.md#Error-enum)
- [PendingCall::Failed](bluezqt-pendingcall.md#Error-enum)
- [PendingCall::InProgress](bluezqt-pendingcall.md#Error-enum)
- [PendingCall::AlreadyConnected](bluezqt-pendingcall.md#Error-enum)

Returns void pending call.

### \[signal\] void Device::connectedChanged(bool *connected*) {#connectedChanged}

Indicates that the device's connected state has changed.

> **Note:** Notifier signal for property [connected](bluezqt-device.md#connected-prop).

### \[signal\] void Device::deviceChanged(BluezQt::DevicePtr *device*) {#deviceChanged}

Indicates that at least one of the device's properties has changed.

### quint32 Device::deviceClass() const {#deviceClass}

Returns the class of the device.

In case of Bluetooth Low Energy only devices, device class is invalid (0).

> **Note:** Getter function for property [deviceClass](bluezqt-device.md#deviceClass-prop).

*See also* [type](bluezqt-device.md#type)()

### \[signal\] void Device::deviceClassChanged(quint32 *deviceClass*) {#deviceClassChanged}

Indicates that the device's class has changed.

> **Note:** Notifier signal for property [deviceClass](bluezqt-device.md#deviceClass-prop).

### \[signal\] void Device::deviceRemoved(BluezQt::DevicePtr *device*) {#deviceRemoved}

Indicates that the device was removed.

### \[slot\] BluezQt::PendingCall \*Device::disconnectFromDevice() {#disconnectFromDevice}

Disconnects all connected profiles of the device.

This method can be used to cancel not-yet finished connectDevice() call.

Possible errors:

- [PendingCall::NotConnected](bluezqt-pendingcall.md#Error-enum)

Returns void pending call.

### \[slot\] BluezQt::PendingCall \*Device::disconnectProfile(const QString &*uuid*) {#disconnectProfile}

Disconnects a specific profile of the device with the given service `uuid`.

Possible errors:

- [PendingCall::DoesNotExist](bluezqt-pendingcall.md#Error-enum)
- [PendingCall::Failed](bluezqt-pendingcall.md#Error-enum)
- [PendingCall::NotConnected](bluezqt-pendingcall.md#Error-enum)
- [PendingCall::NotSupported](bluezqt-pendingcall.md#Error-enum)

Returns void pending call.

### QString Device::friendlyName() const {#friendlyName}

Returns the friendly name of the device.

Friendly name is a string "name ([remoteName](bluezqt-device.md#remoteName))". If the [remoteName](bluezqt-device.md#remoteName) is same as name, it returns just name.

> **Note:** Getter function for property [friendlyName](bluezqt-device.md#friendlyName-prop).

### \[signal\] void Device::friendlyNameChanged(const QString &*friendlyName*) {#friendlyNameChanged}

Indicates that the device's friendly name has changed.

> **Note:** Notifier signal for property [friendlyName](bluezqt-device.md#friendlyName-prop).

### \[signal\] void Device::gattServiceAdded(BluezQt::GattServiceRemotePtr *service*) {#gattServiceAdded}

Indicates that a new service was added (eg. found by connection).

### \[signal\] void Device::gattServiceChanged(BluezQt::GattServiceRemotePtr *service*) {#gattServiceChanged}

Indicates that at least one of the device's services has changed.

### \[signal\] void Device::gattServiceRemoved(BluezQt::GattServiceRemotePtr *service*) {#gattServiceRemoved}

Indicates that a service was removed.

### QList\<BluezQt::GattServiceRemotePtr\> Device::gattServices() const {#gattServices}

Returns a list of services known by the device.

> **Note:** Getter function for property [gattServices](bluezqt-device.md#gattServices-prop).

### \[signal\] void Device::gattServicesChanged(QList\<BluezQt::GattServiceRemotePtr\> *services*) {#gattServicesChanged}

Indicates that the device GATT services list has changed.

> **Note:** Notifier signal for property [gattServices](bluezqt-device.md#gattServices-prop).

### bool Device::hasLegacyPairing() const {#hasLegacyPairing}

Returns whether the device has legacy pairing.

> **Note:** Getter function for property [legacyPairing](bluezqt-device.md#legacyPairing-prop).

### QString Device::icon() const {#icon}

Returns the icon name of the device.

In case the icon is empty, "preferences-system-bluetooth" is returned.

> **Note:** Getter function for property [icon](bluezqt-device.md#icon-prop).

### \[signal\] void Device::iconChanged(const QString &*icon*) {#iconChanged}

Indicates that the device's icon has changed.

> **Note:** Notifier signal for property [icon](bluezqt-device.md#icon-prop).

### BluezQt::InputPtr Device::input() const {#input}

Returns the input interface for the device.

Only input devices will have valid input interface.

Returns null if device has no input.

> **Note:** Getter function for property [input](bluezqt-device.md#input-prop).

### \[signal\] void Device::inputChanged(BluezQt::InputPtr *input*) {#inputChanged}

Indicates that the device's input has changed.

> **Note:** Notifier signal for property [input](bluezqt-device.md#input-prop).

### bool Device::isBlocked() const {#isBlocked}

Returns whether the device is blocked.

> **Note:** Getter function for property [blocked](bluezqt-device.md#blocked-prop).

### bool Device::isConnected() const {#isConnected}

Returns whether the device is connected.

> **Note:** Getter function for property [connected](bluezqt-device.md#connected-prop).

### bool Device::isPaired() const {#isPaired}

Returns whether the device is paired.

> **Note:** Getter function for property [paired](bluezqt-device.md#paired-prop).

### bool Device::isServicesResolved() const {#isServicesResolved}

Returns whether or not service discovery has been resolved.

> **Note:** Getter function for property [servicesResolved](bluezqt-device.md#servicesResolved-prop).

### bool Device::isTrusted() const {#isTrusted}

Returns whether the device is trusted.

> **Note:** Getter function for property [trusted](bluezqt-device.md#trusted-prop).

### \[signal\] void Device::legacyPairingChanged(bool *legacyPairing*) {#legacyPairingChanged}

Indicates that the device's legacy pairing state has changed.

> **Note:** Notifier signal for property [legacyPairing](bluezqt-device.md#legacyPairing-prop).

### BluezQt::ManData Device::manufacturerData() const {#manufacturerData}

Returns manufacturer specific advertisement data.

> **Note:** Keys are 16 bits Manufacturer ID followed by its byte array value.

> **Note:** Getter function for property [manufacturerData](bluezqt-device.md#manufacturerData-prop).

### \[signal\] void Device::manufacturerDataChanged(BluezQt::ManData *man*) {#manufacturerDataChanged}

Indicates that the device's manufacturer data has changed.

> **Note:** Notifier signal for property [manufacturerData](bluezqt-device.md#manufacturerData-prop).

### BluezQt::MediaPlayerPtr Device::mediaPlayer() const {#mediaPlayer}

Returns the media player interface for the device.

Only devices with connected appropriate profile will have valid media player interface.

Returns null if device has no media player.

> **Note:** Getter function for property [mediaPlayer](bluezqt-device.md#mediaPlayer-prop).

### \[signal\] void Device::mediaPlayerChanged(BluezQt::MediaPlayerPtr *mediaPlayer*) {#mediaPlayerChanged}

Indicates that the device's media player has changed.

> **Note:** Notifier signal for property [mediaPlayer](bluezqt-device.md#mediaPlayer-prop).

### BluezQt::MediaTransportPtr Device::mediaTransport() const {#mediaTransport}

Returns the media transport interface for the device.

Only devices with connected appropriate profile will have valid media transport interface.

Returns null if device has no media transport.

> **Note:** Getter function for property [mediaTransport](bluezqt-device.md#mediaTransport-prop).

### \[signal\] void Device::mediaTransportChanged(BluezQt::MediaTransportPtr *mediaTransport*) {#mediaTransportChanged}

Indicates that the device's media transport has changed.

> **Note:** Notifier signal for property [mediaTransport](bluezqt-device.md#mediaTransport-prop).

### QString Device::modalias() const {#modalias}

Returns remote device ID in modalias format.

> **Note:** Getter function for property [modalias](bluezqt-device.md#modalias-prop).

### \[signal\] void Device::modaliasChanged(const QString &*modalias*) {#modaliasChanged}

Indicates that the device's modalias has changed.

> **Note:** Notifier signal for property [modalias](bluezqt-device.md#modalias-prop).

### QString Device::name() const {#name}

Returns the name of the device.

If the name of the device wasn't previously changed, [remoteName](bluezqt-device.md#remoteName) is returned.

> **Note:** Getter function for property [name](bluezqt-device.md#name-prop).

*See also* [setName](bluezqt-device.md#setName)()

### \[signal\] void Device::nameChanged(const QString &*name*) {#nameChanged}

Indicates that the device's name has changed.

> **Note:** Notifier signal for property [name](bluezqt-device.md#name-prop).

### \[slot\] BluezQt::PendingCall \*Device::pair() {#pair}

Initiates a pairing with the device.

Possible errors:

- [PendingCall::InvalidArguments](bluezqt-pendingcall.md#Error-enum)
- [PendingCall::Failed](bluezqt-pendingcall.md#Error-enum)
- [PendingCall::AlreadyExists](bluezqt-pendingcall.md#Error-enum)
- [PendingCall::AuthenticationCanceled](bluezqt-pendingcall.md#Error-enum)
- [PendingCall::AuthenticationFailed](bluezqt-pendingcall.md#Error-enum)
- [PendingCall::AuthenticationRejected](bluezqt-pendingcall.md#Error-enum)
- [PendingCall::AuthenticationTimeout](bluezqt-pendingcall.md#Error-enum)
- [PendingCall::ConnectionAttemptFailed](bluezqt-pendingcall.md#Error-enum)

Returns void pending call.

### \[signal\] void Device::pairedChanged(bool *paired*) {#pairedChanged}

Indicates that the device's paired state has changed.

> **Note:** Notifier signal for property [paired](bluezqt-device.md#paired-prop).

### QString Device::remoteName() const {#remoteName}

Returns the remote name of the device.

> **Note:** Getter function for property [remoteName](bluezqt-device.md#remoteName-prop).

### \[signal\] void Device::remoteNameChanged(const QString &*remoteName*) {#remoteNameChanged}

Indicates that the device's remote name has changed.

> **Note:** Notifier signal for property [remoteName](bluezqt-device.md#remoteName-prop).

### qint16 Device::rssi() const {#rssi}

Returns the Received Signal Strength Indicator of the device.

The bigger value indicates better signal strength.

> **Note:** RSSI is only updated during discovery.

> **Note:** Getter function for property [rssi](bluezqt-device.md#rssi-prop).

### \[signal\] void Device::rssiChanged(qint16 *rssi*) {#rssiChanged}

Indicates that the device's RSSI has changed.

> **Note:** Notifier signal for property [rssi](bluezqt-device.md#rssi-prop).

### QHash\<QString, QByteArray\> Device::serviceData() const {#serviceData}

Returns the service advertisement data.

Returns a hash with keys being the UUIDs in and values being the raw service data value.

### \[signal\] void Device::serviceDataChanged(const QHash\<QString, QByteArray\> &*serviceData*) {#serviceDataChanged}

Indicates that the device's service data has changed.

### \[signal\] void Device::servicesResolvedChanged(bool *servicesResolved*) {#servicesResolvedChanged}

Indicates that the device's [servicesResolved](bluezqt-device.md#servicesResolved-prop) state has changed.

> **Note:** Notifier signal for property [servicesResolved](bluezqt-device.md#servicesResolved-prop).

### BluezQt::PendingCall \*Device::setBlocked(bool *blocked*) {#setBlocked}

Sets the `blocked` state of the device.

Returns void pending call.

> **Note:** Setter function for property [blocked](bluezqt-device.md#blocked-prop).

*See also* [isBlocked](bluezqt-device.md#isBlocked)()

### BluezQt::PendingCall \*Device::setName(const QString &*name*) {#setName}

Sets the `name` of the device.

Returns a void pending call.

> **Note:** Setter function for property [name](bluezqt-device.md#name-prop).

*See also* [name](bluezqt-device.md#name)()

### BluezQt::PendingCall \*Device::setTrusted(bool *trusted*) {#setTrusted}

Sets the `trusted` state of the device.

Returns void pending call.

> **Note:** Setter function for property [trusted](bluezqt-device.md#trusted-prop).

*See also* [isTrusted](bluezqt-device.md#isTrusted)()

### \[static\] BluezQt::Device::Type Device::stringToType(const QString &*typeString*) {#stringToType}

Returns a string for the device type `typeString`.

### BluezQt::DevicePtr Device::toSharedPtr() const {#toSharedPtr}

Returns a shared pointer from this.

### \[signal\] void Device::trustedChanged(bool *trusted*) {#trustedChanged}

Indicates that the device's trusted state has changed.

> **Note:** Notifier signal for property [trusted](bluezqt-device.md#trusted-prop).

### BluezQt::Device::Type Device::type() const {#type}

Returns the type of the device.

Type of device is deduced from its class (for Bluetooth Classic devices) or its appearance (for Bluetooth Low Energy devices).

> **Note:** Getter function for property [type](bluezqt-device.md#type-prop).

*See also* [deviceClass](bluezqt-device.md#deviceClass)(), [appearance](bluezqt-device.md#appearance)()

### \[signal\] void Device::typeChanged(BluezQt::Device::Type *type*) {#typeChanged}

Indicates that the device's type has changed.

> **Note:** Notifier signal for property [type](bluezqt-device.md#type-prop).

### \[static\] QString Device::typeToString(BluezQt::Device::Type *type*) {#typeToString}

Returns a string of the device `type`.

### QString Device::ubi() const {#ubi}

Returns the UBI of the device.

Example UBI: "/org/bluez/hci0/dev\_40\_79\_6A\_0C\_39\_75"

> **Note:** Getter function for property [ubi](bluezqt-device.md#ubi-prop).

### QStringList Device::uuids() const {#uuids}

Returns UUIDs of services supported by the device.

UUIDs will always be returned in uppercase.

> **Note:** Getter function for property [uuids](bluezqt-device.md#uuids-prop).

### \[signal\] void Device::uuidsChanged(const QStringList &*uuids*) {#uuidsChanged}

Indicates that the device's UUIDs has changed.

> **Note:** Notifier signal for property [uuids](bluezqt-device.md#uuids-prop).
