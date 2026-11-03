---
title: "ModemManager Namespace"
description: "Qt wrapper for modemmanager API."
---

# ModemManager Namespace

Qt wrapper for modemmanager API. [More...](#details)

- Header: ModemManager
- CMake: find\_package(KF6 REQUIRED COMPONENTS ModemManagerQt) target\_link\_libraries(mytarget PRIVATE KF6::ModemManagerQt)

## Detailed Description {#details}

This namespace allows to query the underlying system to discover the available modem interfaces responsibility to notify when a modem interface or a modem appears or disappears.

Note that it's implemented as a singleton and encapsulates the backend logic.

## Classes {#classes}

### class [Bearer](modemmanager-bearer.md)

The Bearer class.

### class [BearerProperties](modemmanager-bearerproperties.md)

This class represents bearer properties used for creating of new bearers.

### class [Call](modemmanager-call.md)

Provides an interface to manipulate and control a call.

### class [Cbm](modemmanager-cbm.md)

Provides an interface to access a cell broadcast message.

### class [Interface](modemmanager-interface.md)

### class [IpConfig](modemmanager-ipconfig.md)

This class represents IP configuration.

### class [Modem](modemmanager-modem.md)

The Modem class.

### class [Modem3gpp](modemmanager-modem3gpp.md)

The Modem3gpp class.

### class [Modem3gppUssd](modemmanager-modem3gppussd.md)

The [Modem3gppUssd](modemmanager-modem3gppussd.md) class.

### class [ModemCdma](modemmanager-modemcdma.md)

The [ModemCdma](modemmanager-modemcdma.md) class.

### class [ModemCellBroadcast](modemmanager-modemcellbroadcast.md)

The [ModemCellBroadcast](modemmanager-modemcellbroadcast.md) class.

### class [ModemDevice](modemmanager-modemdevice.md)

### class [ModemFirmware](modemmanager-modemfirmware.md)

The [ModemFirmware](modemmanager-modemfirmware.md) class.

### class [ModemLocation](modemmanager-modemlocation.md)

The [ModemLocation](modemmanager-modemlocation.md) class.

### class [ModemMessaging](modemmanager-modemmessaging.md)

The [ModemMessaging](modemmanager-modemmessaging.md) class.

### class [ModemOma](modemmanager-modemoma.md)

The [ModemManager](modemmanager.md) Open Mobile Alliance interface.

### class [ModemSignal](modemmanager-modemsignal.md)

The [ModemSignal](modemmanager-modemsignal.md) class.

### class [ModemSimple](modemmanager-modemsimple.md)

The [ModemSimple](modemmanager-modemsimple.md) class.

### class [ModemTime](modemmanager-modemtime.md)

The [ModemTime](modemmanager-modemtime.md) class.

### class [ModemVoice](modemmanager-modemvoice.md)

The [ModemVoice](modemmanager-modemvoice.md) class.

### class [NetworkTimezone](modemmanager-networktimezone.md)

This class represents the timezone data provided by the network.

### class [Notifier](modemmanager-notifier.md)

### class [Sim](modemmanager-sim.md)

The Sim class.

### class [Sms](modemmanager-sms.md)

Provides an interface to manipulate and control an SMS.

## Type Documentation {#type-documentation}

### ModemManager::CellBroadcastChannelRange {#CellBroadcastChannelRange-typedef}

### ModemManager::CellBroadcastChannelRangeList {#CellBroadcastChannelRangeList-typedef}

### ModemManager::ConnectionError {#ConnectionError-typedef}

### ModemManager::CurrentModesType {#CurrentModesType-typedef}

### ModemManager::DBUSManagerStruct {#DBUSManagerStruct-typedef}

### ModemManager::FacilityLock {#FacilityLock-typedef}

### ModemManager::FirmwareUpdateSettings {#FirmwareUpdateSettings-typedef}

### ModemManager::LocationInformationMap {#LocationInformationMap-typedef}

### ModemManager::MMVariantMapMap {#MMVariantMapMap-typedef}

### ModemManager::OmaSessionType {#OmaSessionType-typedef}

### ModemManager::OmaSessionTypes {#OmaSessionTypes-typedef}

### ModemManager::PcoInfo {#PcoInfo-typedef}

### ModemManager::PcoInfoList {#PcoInfoList-typedef}

### ModemManager::Port {#Port-typedef}

### ModemManager::PortList {#PortList-typedef}

### ModemManager::QVariantMapList {#QVariantMapList-typedef}

### ModemManager::SignalQualityPair {#SignalQualityPair-typedef}

### ModemManager::SupportedModesType {#SupportedModesType-typedef}

### ModemManager::UIntList {#UIntList-typedef}

### ModemManager::UIntListList {#UIntListList-typedef}

### ModemManager::UnlockRetriesMap {#UnlockRetriesMap-typedef}

### ModemManager::ValidityPair {#ValidityPair-typedef}

## Function Documentation {#function-documentation}

### ModemDevice::Ptr ModemManager::findModemDevice(const QString &*uni*) {#findModemDevice}

Find a new ModemManagerInterface object given its UDI.

> **Note:** only Modem-inherited objects are returned (not SMS, SIM or Bearer objects)

`uni` the identifier of the modem interface to find Returns a valid Modem object if there's a device having the given UDI, an invalid one otherwise

### \[since 6.31\] QDBusPendingReply\<\> ModemManager::inhibitDevice(const QString &*uid*, bool *inhibit*) {#inhibitDevice}

Inhibit or uninhibit the device.

When the modem is inhibited, [ModemManager](modemmanager.md) will close all its ports and unexport it from the bus, so that users of the interface are no longer able to operate with it.

The inhibition request is bound to the caller's existence on the DBus bus. If the caller disappears, the inhibition is automatically removed.

`uid` the unique ID of the physical device, as given in the org.freedesktop.ModemManager1.Modem Device property. `inhibit` `true` to inhibit the modem, `false` to uninhibit it.

This function was introduced in Qt 6.31.

### ModemDevice::List ModemManager::modemDevices() {#modemDevices}

Retrieves the list of all modem interfaces Unique Device Identifiers (UDIs) in the system. This method is the equivalent of enumerateDevices described in Modem Manager specification.

> **Note:** only HW modems are returned (Gsm or Cdma)

Returns the list of modem interfaces available in this system

### ModemManager::Notifier \*ModemManager::notifier() {#notifier}

### \[since 6.31\] QDBusPendingReply\<\> ModemManager::reportKernelEvent(const QVariantMap &*properties*) {#reportKernelEvent}

Reports a kernel event to [ModemManager](modemmanager.md).

This method is only available if udev is not being used to report kernel events.

`properties` event properties dictionary. Mandatory keys are: "action" (string: "add" or "remove"), "name" (string: device name), "subsystem" (string: device subsystem). Optional key: "uid" (string: unique ID of the physical device; if not given, the sysfs path is used).

This function was introduced in Qt 6.31.

### void ModemManager::scanDevices() {#scanDevices}

Start a new scan for connected modem devices.

### \[since 6.31\] QDBusPendingReply\<\> ModemManager::setLogging(const QString &*level*) {#setLogging}

Set logging verbosity.

`level` one of "ERR", "WARN", "MSG" (since [ModemManager](modemmanager.md) 1.22), "INFO", "DEBUG".

This function was introduced in Qt 6.31.

### \[since 6.31\] QString ModemManager::version() {#version}

Returns the runtime version of the [ModemManager](modemmanager.md) daemon.

This function was introduced in Qt 6.31.
