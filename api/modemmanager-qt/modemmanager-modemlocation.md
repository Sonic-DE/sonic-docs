---
title: "ModemManager::ModemLocation Class"
description: "The ModemLocation class."
---

# ModemManager::ModemLocation Class

The [ModemLocation](modemmanager-modemlocation.md) class. [More...](#details)

- **Header:** `#include <ModemManagerQt/ModemLocation>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS ModemManagerQt)`  
  `target_link_libraries(mytarget PRIVATE KF6::ModemManagerQt)`
- **Inherits:** [ModemManager::Interface](modemmanager-interface.md)

[List of all members, including inherited members](modemmanager-modemlocation-members.md)

## Public Types

- [ModemLocation::List](#List-typedef)
- [ModemLocation::Ptr](#Ptr-typedef)

## Public Functions

- [ModemLocation(const QString &path, QObject \*parent = nullptr)](#ModemLocation)
- [QStringList assistanceDataServers() const](#assistanceDataServers) (since 6.24.0)
- [ModemManager::ModemLocation::LocationSources capabilities() const](#capabilities)
- [ModemManager::ModemLocation::LocationSources enabledCapabilities() const](#enabledCapabilities)
- [QDBusPendingReply\<ModemManager::LocationInformationMap\> getLocation()](#getLocation)
- [uint gpsRefreshRate() const](#gpsRefreshRate) (since 6.24.0)
- [QDBusPendingReply\<void\> injectAssistanceData(const QByteArray &data)](#injectAssistanceData) (since 6.24.0)
- [bool isEnabled() const](#isEnabled)
- [ModemManager::LocationInformationMap location() const](#location)
- [QDBusPendingReply\<void\> setGpsRefreshRate(uint rate)](#setGpsRefreshRate) (since 6.24.0)
- [QDBusPendingReply\<void\> setSuplServer(const QString &server)](#setSuplServer) (since 6.24.0)
- [void setTimeout(int timeout)](#setTimeout)
- [QDBusPendingReply\<void\> setup(ModemManager::ModemLocation::LocationSources sources, bool signalLocation)](#setup)
- [bool signalsLocation() const](#signalsLocation)
- [QString suplServer() const](#suplServer) (since 6.24.0)
- [ModemManager::ModemLocation::AssistanceDataTypes supportedAssistanceData() const](#supportedAssistanceData) (since 6.24.0)
- [int timeout() const](#timeout)

## Signals

- [void assistanceDataServersChanged(const QStringList &servers)](#assistanceDataServersChanged) (since 6.24.0)
- [void capabilitiesChanged(QFlags\<MMModemLocationSource\> capabilities)](#capabilitiesChanged)
- [void enabledCapabilitiesChanged(QFlags\<MMModemLocationSource\> capabilities)](#enabledCapabilitiesChanged)
- [void gpsRefreshRateChanged(uint rate)](#gpsRefreshRateChanged) (since 6.24.0)
- [void locationChanged(const ModemManager::LocationInformationMap &location)](#locationChanged)
- [void signalsLocationChanged(bool signalsLocation)](#signalsLocationChanged)
- [void suplServerChanged(const QString &server)](#suplServerChanged) (since 6.24.0)
- [void supportedAssistanceDataChanged(QFlags\<MMModemLocationAssistanceDataType\> supported)](#supportedAssistanceDataChanged) (since 6.24.0)

## Detailed Description {#details}

The Location class allows devices to provide location information to client applications. Not all devices can provide this information, or even if they do, they may not be able to provide it while a data session is active.

## Member Type Documentation {#member-type-documentation}

### ModemLocation::List {#List-typedef}

### ModemLocation::Ptr {#Ptr-typedef}

## Member Function Documentation {#member-function-documentation}

### \[explicit\] ModemLocation::ModemLocation(const QString &*path*, QObject \**parent* = nullptr) {#ModemLocation}

### \[since 6.24.0\] QStringList ModemLocation::assistanceDataServers() const {#assistanceDataServers}

Returns the list of assistance data servers.

This function was introduced in Qt 6.24.0.

### \[signal, since 6.24.0\] void ModemLocation::assistanceDataServersChanged(const QStringList &*servers*) {#assistanceDataServersChanged}

This function was introduced in Qt 6.24.0.

### ModemManager::ModemLocation::LocationSources ModemLocation::capabilities() const {#capabilities}

Returns [QFlags](https://doc.qt.io/qt-6/qflags.html) of MMModemLocationSource values, specifying the supported location sources.

### \[signal\] void ModemLocation::capabilitiesChanged(QFlags\<MMModemLocationSource\> *capabilities*) {#capabilitiesChanged}

### ModemManager::ModemLocation::LocationSources ModemLocation::enabledCapabilities() const {#enabledCapabilities}

Returns [QFlags](https://doc.qt.io/qt-6/qflags.html) specifying which of the supported MMModemLocationSource location sources is currently enabled in the device.

### \[signal\] void ModemLocation::enabledCapabilitiesChanged(QFlags\<MMModemLocationSource\> *capabilities*) {#enabledCapabilitiesChanged}

### QDBusPendingReply\<ModemManager::LocationInformationMap\> ModemLocation::getLocation() {#getLocation}

Returns current location information, if any. If the modem supports multiple location types it may return more than one. See the "Location" property for more information on the dictionary returned at location.

This method may require the client to authenticate itself.

### \[since 6.24.0\] uint ModemLocation::gpsRefreshRate() const {#gpsRefreshRate}

Returns the GPS refresh rate in seconds.

This function was introduced in Qt 6.24.0.

*See also* [setGpsRefreshRate](modemmanager-modemlocation.md#setGpsRefreshRate)()

### \[signal, since 6.24.0\] void ModemLocation::gpsRefreshRateChanged(uint *rate*) {#gpsRefreshRateChanged}

This function was introduced in Qt 6.24.0.

### \[since 6.24.0\] QDBusPendingReply\<void\> ModemLocation::injectAssistanceData(const QByteArray &*data*) {#injectAssistanceData}

Inject assistance data into the modem.

This function was introduced in Qt 6.24.0.

### bool ModemLocation::isEnabled() const {#isEnabled}

Returns whether the device has any location capabilities

### ModemManager::LocationInformationMap ModemLocation::location() const {#location}

Returns Dictionary of available location information when location information gathering is enabled. If the modem supports multiple location types it may return more than one here. Note that if the device was told not to emit updated location information when location information gathering was initially enabled, this property may not return any location information for security reasons.

### \[signal\] void ModemLocation::locationChanged(const ModemManager::LocationInformationMap &*location*) {#locationChanged}

Emitted when the location has changed

### \[since 6.24.0\] QDBusPendingReply\<void\> ModemLocation::setGpsRefreshRate(uint *rate*) {#setGpsRefreshRate}

Set the refresh rate for the GPS engine.

This function was introduced in Qt 6.24.0.

*See also* [gpsRefreshRate](modemmanager-modemlocation.md#gpsRefreshRate)()

### \[since 6.24.0\] QDBusPendingReply\<void\> ModemLocation::setSuplServer(const QString &*server*) {#setSuplServer}

Set the SUPL server to use for A-GPS.

This function was introduced in Qt 6.24.0.

*See also* [suplServer](modemmanager-modemlocation.md#suplServer)()

### void ModemLocation::setTimeout(int *timeout*) {#setTimeout}

Sets the timeout in milliseconds for all async method DBus calls. -1 means the default DBus timeout (usually 25 seconds).

*See also* [timeout](modemmanager-modemlocation.md#timeout)()

### QDBusPendingReply\<void\> ModemLocation::setup(ModemManager::ModemLocation::LocationSources *sources*, bool *signalLocation*) {#setup}

Configure the location sources to use when gathering location information. Also enable or disable location information gathering. This method may require the client to authenticate itself.

When signals are emitted, any client application (including malicious ones!) can listen for location updates unless D-Bus permissions restrict these signals from certain users. If further security is desired, the `signLocation` argument can be set to FALSE to disable location updates via the [locationChanged](modemmanager-modemlocation.md#locationChanged)() signal and require applications to call authenticated APIs (like GetLocation() ) to get location information.

### bool ModemLocation::signalsLocation() const {#signalsLocation}

Returns TRUE if location updates will be emitted via the [locationChanged](modemmanager-modemlocation.md#locationChanged)() signal, FALSE if location updates will not be emitted.

See the [setup](modemmanager-modemlocation.md#setup)() method for more information.

### \[signal\] void ModemLocation::signalsLocationChanged(bool *signalsLocation*) {#signalsLocationChanged}

### \[since 6.24.0\] QString ModemLocation::suplServer() const {#suplServer}

Returns the configured SUPL server.

This function was introduced in Qt 6.24.0.

*See also* [setSuplServer](modemmanager-modemlocation.md#setSuplServer)()

### \[signal, since 6.24.0\] void ModemLocation::suplServerChanged(const QString &*server*) {#suplServerChanged}

This function was introduced in Qt 6.24.0.

### \[since 6.24.0\] ModemManager::ModemLocation::AssistanceDataTypes ModemLocation::supportedAssistanceData() const {#supportedAssistanceData}

Returns supported assistance data types.

This function was introduced in Qt 6.24.0.

### \[signal, since 6.24.0\] void ModemLocation::supportedAssistanceDataChanged(QFlags\<MMModemLocationAssistanceDataType\> *supported*) {#supportedAssistanceDataChanged}

This function was introduced in Qt 6.24.0.

### int ModemLocation::timeout() const {#timeout}

Returns the current value of the DBus timeout in milliseconds. -1 means the default DBus timeout (usually 25 seconds).

*See also* [setTimeout](modemmanager-modemlocation.md#setTimeout)()
