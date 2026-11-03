---
title: "ModemManager::Modem Class"
description: "The Modem class."
---

# ModemManager::Modem Class

The Modem class. [More...](#details)

- **Header:** `#include <ModemManagerQt/Modem>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS ModemManagerQt)`  
  `target_link_libraries(mytarget PRIVATE KF6::ModemManagerQt)`
- **Inherits:** [ModemManager::Interface](modemmanager-interface.md)

[List of all members, including inherited members](modemmanager-modem-members.md)

## Public Functions

- [Modem(const QString &path, QObject \*parent = nullptr)](#Modem)
- [ModemManager::Modem::AccessTechnologies accessTechnologies() const](#accessTechnologies)
- [QString carrierConfiguration() const](#carrierConfiguration) (since 6.24.0)
- [QString carrierConfigurationRevision() const](#carrierConfigurationRevision) (since 6.24.0)
- [QDBusPendingReply\<QString\> command(const QString &cmd, uint timeout)](#command)
- [QDBusPendingReply\<QDBusObjectPath\> createBearer(const ModemManager::BearerProperties &bearerProperties)](#createBearer)
- [QList\<MMModemBand\> currentBands() const](#currentBands)
- [ModemManager::Modem::Capabilities currentCapabilities() const](#currentCapabilities)
- [ModemManager::CurrentModesType currentModes() const](#currentModes)
- [QDBusPendingReply\<void\> deleteBearer(const QString &bearer)](#deleteBearer)
- [QString device() const](#device)
- [QString deviceIdentifier() const](#deviceIdentifier)
- [QStringList drivers() const](#drivers)
- [QString equipmentIdentifier() const](#equipmentIdentifier)
- [QDBusPendingReply\<void\> factoryReset(const QString &code)](#factoryReset)
- [ModemManager::Bearer::Ptr findBearer(const QString &bearer) const](#findBearer)
- [QDBusPendingReply\<ModemManager::QVariantMapList\> getCellInfo()](#getCellInfo) (since 6.24.0)
- [QString hardwareRevision() const](#hardwareRevision) (since 6.24.0)
- [bool isEnabled() const](#isEnabled)
- [bool isValid() const](#isValid)
- [ModemManager::Bearer::List listBearers() const](#listBearers)
- [QString manufacturer() const](#manufacturer)
- [uint maxActiveBearers() const](#maxActiveBearers)
- [uint maxActiveMultiplexedBearers() const](#maxActiveMultiplexedBearers) (since 6.24.0)
- [uint maxBearers() const](#maxBearers)
- [QString model() const](#model)
- [QStringList ownNumbers() const](#ownNumbers)
- [QString physdev() const](#physdev) (since 6.24.0)
- [QString plugin() const](#plugin)
- [ModemManager::PortList ports() const](#ports)
- [MMModemPowerState powerState() const](#powerState)
- [QString primaryPort() const](#primaryPort)
- [uint primarySimSlot() const](#primarySimSlot) (since 6.24.0)
- [QDBusPendingReply\<void\> reset()](#reset)
- [QString revision() const](#revision)
- [QDBusPendingReply\<void\> setCurrentBands(const QList\<MMModemBand\> &bands)](#setCurrentBands)
- [QDBusPendingReply\<void\> setCurrentCapabilities(ModemManager::Modem::Capabilities caps)](#setCurrentCapabilities)
- [QDBusPendingReply\<void\> setCurrentModes(const ModemManager::CurrentModesType &mode)](#setCurrentModes)
- [QDBusPendingReply\<void\> setEnabled(bool enable)](#setEnabled)
- [QDBusPendingReply\<void\> setPowerState(MMModemPowerState state)](#setPowerState)
- [QDBusPendingReply\<void\> setPrimarySimSlot(uint slot)](#setPrimarySimSlot) (since 6.24.0)
- [void setTimeout(int timeout)](#setTimeout)
- [ModemManager::SignalQualityPair signalQuality() const](#signalQuality)
- [QString simPath() const](#simPath)
- [ModemManager::UIntList simSlots() const](#simSlots) (since 6.24.0)
- [MMModemState state() const](#state)
- [MMModemStateFailedReason stateFailedReason() const](#stateFailedReason)
- [QList\<MMModemBand\> supportedBands() const](#supportedBands)
- [QList\<MMModemCapability\> supportedCapabilities() const](#supportedCapabilities)
- [ModemManager::Modem::IpBearerFamilies supportedIpFamilies() const](#supportedIpFamilies)
- [ModemManager::SupportedModesType supportedModes() const](#supportedModes)
- [int timeout() const](#timeout)
- [QString uni() const](#uni)
- [MMModemLock unlockRequired() const](#unlockRequired)
- [ModemManager::UnlockRetriesMap unlockRetries() const](#unlockRetries)

## Signals

- [void accessTechnologiesChanged(QFlags\<MMModemAccessTechnology\> accessTechnologies)](#accessTechnologiesChanged)
- [void bearerAdded(const QString &bearer)](#bearerAdded)
- [void bearerRemoved(const QString &bearer)](#bearerRemoved)
- [void bearersChanged()](#bearersChanged)
- [void carrierConfigurationChanged(const QString &carrierConfiguration)](#carrierConfigurationChanged) (since 6.24.0)
- [void carrierConfigurationRevisionChanged(const QString &carrierConfigurationRevision)](#carrierConfigurationRevisionChanged) (since 6.24.0)
- [void currentBandsChanged(const QList\<MMModemBand\> &supportedBands)](#currentBandsChanged)
- [void currentCapabilitiesChanged(const QFlags\<MMModemCapability\> &currentCapabilities)](#currentCapabilitiesChanged)
- [void currentModesChanged(ModemManager::CurrentModesType currentModes)](#currentModesChanged)
- [void deviceChanged(const QString &device)](#deviceChanged)
- [void deviceIdentifierChanged(const QString &deviceIdentifier)](#deviceIdentifierChanged)
- [void driversChanged(const QStringList &drivers)](#driversChanged)
- [void equipmentIdentifierChanged(const QString &equipmentIdentifier)](#equipmentIdentifierChanged)
- [void hardwareRevisionChanged(const QString &hardwareRevision)](#hardwareRevisionChanged) (since 6.24.0)
- [void manufacturerChanged(const QString &manufacturer)](#manufacturerChanged)
- [void maxActiveBearersChanged(uint maxActiveBearers)](#maxActiveBearersChanged)
- [void maxActiveMultiplexedBearersChanged(uint maxActiveMultiplexedBearers)](#maxActiveMultiplexedBearersChanged) (since 6.24.0)
- [void maxBearersChanged(uint maxBearers)](#maxBearersChanged)
- [void modelChanged(const QString &model)](#modelChanged)
- [void ownNumbersChanged(const QStringList &ownNumbers)](#ownNumbersChanged)
- [void physdevChanged(const QString &physdev)](#physdevChanged) (since 6.24.0)
- [void pluginChanged(const QString &plugin)](#pluginChanged)
- [void portsChanged(const ModemManager::PortList &ports)](#portsChanged)
- [void powerStateChanged(MMModemPowerState powerState)](#powerStateChanged)
- [void primaryPortChanged(const QString &primaryPort)](#primaryPortChanged)
- [void primarySimSlotChanged(uint slot)](#primarySimSlotChanged) (since 6.24.0)
- [void revisionChanged(const QString &revision)](#revisionChanged)
- [void signalQualityChanged(ModemManager::SignalQualityPair signalQuality)](#signalQualityChanged)
- [void simPathChanged(const QString &oldPath, const QString &newPath)](#simPathChanged)
- [void simSlotsChanged(const ModemManager::UIntList &simSlots)](#simSlotsChanged) (since 6.24.0)
- [void stateChanged(MMModemState oldState, MMModemState newState, MMModemStateChangeReason reason)](#stateChanged)
- [void stateFailedReasonChanged(MMModemStateFailedReason stateFailedReason)](#stateFailedReasonChanged)
- [void supportedBandsChanged(const QList\<MMModemBand\> &supportedBands)](#supportedBandsChanged)
- [void supportedCapabilitiesChanged(const QList\<MMModemCapability\> &supportedCapabilities)](#supportedCapabilitiesChanged)
- [void supportedIpFamiliesChanged(QFlags\<MMBearerIpFamily\> supportedIpFamilies)](#supportedIpFamiliesChanged)
- [void supportedModesChanged(ModemManager::SupportedModesType supportedModes)](#supportedModesChanged)
- [void unlockRequiredChanged(MMModemLock unlockRequired)](#unlockRequiredChanged)
- [void unlockRetriesChanged(const ModemManager::UnlockRetriesMap &unlockRetries)](#unlockRetriesChanged)

## Detailed Description {#details}

The Modem interface controls the status and actions in a given modem object.

## Member Function Documentation {#member-function-documentation}

### \[explicit\] Modem::Modem(const QString &*path*, QObject \**parent* = nullptr) {#Modem}

### ModemManager::Modem::AccessTechnologies Modem::accessTechnologies() const {#accessTechnologies}

Returns [QFlags](https://doc.qt.io/qt-6/qflags.html) of MMModemAccessTechnology values, specifying the current network access technologies used by the device to communicate with the network.

If the device's access technology cannot be determined, MM\_MODEM\_ACCESS\_TECHNOLOGY\_UNKNOWN will be reported.

### \[signal\] void Modem::accessTechnologiesChanged(QFlags\<MMModemAccessTechnology\> *accessTechnologies*) {#accessTechnologiesChanged}

### \[signal\] void Modem::bearerAdded(const QString &*bearer*) {#bearerAdded}

### \[signal\] void Modem::bearerRemoved(const QString &*bearer*) {#bearerRemoved}

### \[signal\] void Modem::bearersChanged() {#bearersChanged}

### \[since 6.24.0\] QString Modem::carrierConfiguration() const {#carrierConfiguration}

Returns the description of the carrier-specific configuration (MCFG) in use by the modem.

This function was introduced in Qt 6.24.0.

### \[signal, since 6.24.0\] void Modem::carrierConfigurationChanged(const QString &*carrierConfiguration*) {#carrierConfigurationChanged}

This function was introduced in Qt 6.24.0.

### \[since 6.24.0\] QString Modem::carrierConfigurationRevision() const {#carrierConfigurationRevision}

Returns the revision identification of the carrier-specific configuration (MCFG) in use by the modem.

This function was introduced in Qt 6.24.0.

### \[signal, since 6.24.0\] void Modem::carrierConfigurationRevisionChanged(const QString &*carrierConfigurationRevision*) {#carrierConfigurationRevisionChanged}

This function was introduced in Qt 6.24.0.

### QDBusPendingReply\<QString\> Modem::command(const QString &*cmd*, uint *timeout*) {#command}

Send an arbitrary AT command to a modem and get the response.

Note that using this interface call is only allowed when running [ModemManager](modemmanager.md) in debug mode or if the project was built using the with-at-command-via-dbus configure option.

`cmd` The command string, e.g. "AT+GCAP" or "+GCAP" (leading AT is inserted if necessary). `timeout` The number of seconds to wait for a response.

### QDBusPendingReply\<QDBusObjectPath\> Modem::createBearer(const ModemManager::BearerProperties &*bearerProperties*) {#createBearer}

Create a new packet data bearer using the given characteristics.

This request may fail if the modem does not support additional bearers, if too many bearers are already defined, or if properties are invalid.

### QList\<MMModemBand\> Modem::currentBands() const {#currentBands}

Returns List of MMModemBand values, specifying the radio frequency and technology bands the device is currently using when connecting to a network.

It must be a subset of [supportedBands](modemmanager-modem.md#supportedBands)()

*See also* [setCurrentBands](modemmanager-modem.md#setCurrentBands)()

### \[signal\] void Modem::currentBandsChanged(const QList\<MMModemBand\> &*supportedBands*) {#currentBandsChanged}

### ModemManager::Modem::Capabilities Modem::currentCapabilities() const {#currentCapabilities}

Returns [QFlags](https://doc.qt.io/qt-6/qflags.html) of MMModemCapability values, specifying the generic family of access technologies the modem currently supports without a firmware reload or reinitialization.

*See also* [setCurrentCapabilities](modemmanager-modem.md#setCurrentCapabilities)()

### \[signal\] void Modem::currentCapabilitiesChanged(const QFlags\<MMModemCapability\> &*currentCapabilities*) {#currentCapabilitiesChanged}

### ModemManager::CurrentModesType Modem::currentModes() const {#currentModes}

Returns A pair of MMModemMode values, where the first one is a bitmask specifying the access technologies (eg 2G/3G/4G) the device is currently allowed to use when connecting to a network, and the second one is the preferred mode of those specified as allowed.

The pair must be one of those specified in [supportedModes](modemmanager-modem.md#supportedModes)()

*See also* [setCurrentModes](modemmanager-modem.md#setCurrentModes)()

### \[signal\] void Modem::currentModesChanged(ModemManager::CurrentModesType *currentModes*) {#currentModesChanged}

### QDBusPendingReply\<void\> Modem::deleteBearer(const QString &*bearer*) {#deleteBearer}

Delete an existing packet data bearer.

If the bearer is currently active and providing packet data server, it will be disconnected and that packet data service will terminate.

`bearer` path to the bearer to delete

### QString Modem::device() const {#device}

Returns The physical modem device reference (ie, USB, PCI, PCMCIA device), which may be dependent upon the operating system.

In Linux for example, this points to a sysfs path of the usb\_device object.

### \[signal\] void Modem::deviceChanged(const QString &*device*) {#deviceChanged}

### QString Modem::deviceIdentifier() const {#deviceIdentifier}

Returns A best-effort device identifier based on various device information like model name, firmware revision, USB/PCI/PCMCIA IDs, and other properties.

This ID is not guaranteed to be unique and may be shared between identical devices with the same firmware, but is intended to be "unique enough" for use as a casual device identifier for various user experience operations.

This is not the device's IMEI or ESN since those may not be available before unlocking the device via a PIN.

### \[signal\] void Modem::deviceIdentifierChanged(const QString &*deviceIdentifier*) {#deviceIdentifierChanged}

### QStringList Modem::drivers() const {#drivers}

Returns The Operating System device drivers handling communication with the modem hardware.

### \[signal\] void Modem::driversChanged(const QStringList &*drivers*) {#driversChanged}

### QString Modem::equipmentIdentifier() const {#equipmentIdentifier}

Returns The identity of the device.

This will be the IMEI number for GSM devices and the hex-format ESN/MEID for CDMA devices.

### \[signal\] void Modem::equipmentIdentifierChanged(const QString &*equipmentIdentifier*) {#equipmentIdentifierChanged}

### QDBusPendingReply\<void\> Modem::factoryReset(const QString &*code*) {#factoryReset}

Clear the modem's configuration (including persistent configuration and state), and return the device to a factory-default state.

If not required by the modem, `code` may be ignored.

This command may or may not power-cycle the device.

`code` Carrier-supplied code required to reset the modem.

### ModemManager::Bearer::Ptr Modem::findBearer(const QString &*bearer*) const {#findBearer}

Returns the configured packet data bearer on given path

### \[since 6.24.0\] QDBusPendingReply\<ModemManager::QVariantMapList\> Modem::getCellInfo() {#getCellInfo}

Get information for available cells in different access technologies, either serving or neighboring along with radio frequency information.

Returns an array of dictionaries, where each dictionary reports information for one single cell. Each dictionary has mandatory keys "cell-type" (a MMCellType value) and "serving" (a boolean indicating whether this is a serving or neighboring cell). Additional keys depend on the cell type (CDMA, GSM, UMTS, TD-SCDMA, LTE, 5GNR).

This function was introduced in Qt 6.24.0.

### \[since 6.24.0\] QString Modem::hardwareRevision() const {#hardwareRevision}

Returns the revision identification of the hardware, as reported by the modem.

This function was introduced in Qt 6.24.0.

### \[signal, since 6.24.0\] void Modem::hardwareRevisionChanged(const QString &*hardwareRevision*) {#hardwareRevisionChanged}

This function was introduced in Qt 6.24.0.

### bool Modem::isEnabled() const {#isEnabled}

Returns `true` if the modem is fully functional, `false` when in low power mode or disabled

*See also* [setEnabled](modemmanager-modem.md#setEnabled)()

### bool Modem::isValid() const {#isValid}

### ModemManager::Bearer::List Modem::listBearers() const {#listBearers}

Returns the configured packet data bearers (EPS Bearers, PDP Contexts, or CDMA2000 Packet Data Sessions).

### QString Modem::manufacturer() const {#manufacturer}

Returns The equipment manufacturer, as reported by the modem.

### \[signal\] void Modem::manufacturerChanged(const QString &*manufacturer*) {#manufacturerChanged}

### uint Modem::maxActiveBearers() const {#maxActiveBearers}

Returns The maximum number of active packet data bearers the modem supports.

POTS and CDMA2000-only devices support one active bearer, while GSM/UMTS and LTE-capable devices (including LTE/CDMA devices) typically support at least two active bearers.

### \[signal\] void Modem::maxActiveBearersChanged(uint *maxActiveBearers*) {#maxActiveBearersChanged}

### \[since 6.24.0\] uint Modem::maxActiveMultiplexedBearers() const {#maxActiveMultiplexedBearers}

Returns the maximum number of active MM\_BEARER\_TYPE\_DEFAULT bearers that may be explicitly enabled by the user with multiplexing support on one single network interface.

If the modem doesn't support multiplexing of data sessions, a value of 0 will be reported.

This function was introduced in Qt 6.24.0.

### \[signal, since 6.24.0\] void Modem::maxActiveMultiplexedBearersChanged(uint *maxActiveMultiplexedBearers*) {#maxActiveMultiplexedBearersChanged}

This function was introduced in Qt 6.24.0.

### uint Modem::maxBearers() const {#maxBearers}

Returns The maximum number of defined packet data bearers the modem supports.

This is not the number of active/connected bearers the modem supports, but simply the number of bearers that may be defined at any given time. For example, POTS and CDMA2000-only devices support only one bearer, while GSM/UMTS devices typically support three or more, and any LTE-capable device (whether LTE-only, GSM/UMTS-capable, and/or CDMA2000-capable) also typically support three or more.

### \[signal\] void Modem::maxBearersChanged(uint *maxBearers*) {#maxBearersChanged}

### QString Modem::model() const {#model}

Returns The equipment model, as reported by the modem.

### \[signal\] void Modem::modelChanged(const QString &*model*) {#modelChanged}

### QStringList Modem::ownNumbers() const {#ownNumbers}

Returns List of numbers (e.g. MSISDN in 3GPP) being currently handled by this modem.

### \[signal\] void Modem::ownNumbersChanged(const QStringList &*ownNumbers*) {#ownNumbersChanged}

### \[since 6.24.0\] QString Modem::physdev() const {#physdev}

Returns the physical modem device path (ie, USB, PCI, PCMCIA device), which may be dependent upon the operating system.

In Linux for example, this points to a sysfs path of the usb\_device object.

This function was introduced in Qt 6.24.0.

### \[signal, since 6.24.0\] void Modem::physdevChanged(const QString &*physdev*) {#physdevChanged}

Emitted when the physical modem device path changes.

This function was introduced in Qt 6.24.0.

### QString Modem::plugin() const {#plugin}

Returns The name of the plugin handling this modem.

### \[signal\] void Modem::pluginChanged(const QString &*plugin*) {#pluginChanged}

### ModemManager::PortList Modem::ports() const {#ports}

Returns The list of ports in the modem, given as an array of string and unsigned integer pairs. The string is the port name or path, and the integer is the port type given as a MMModemPortType value.

### \[signal\] void Modem::portsChanged(const ModemManager::PortList &*ports*) {#portsChanged}

### MMModemPowerState Modem::powerState() const {#powerState}

Returns A MMModemPowerState value specifying the current power state of the modem.

*See also* [setPowerState](modemmanager-modem.md#setPowerState)()

### \[signal\] void Modem::powerStateChanged(MMModemPowerState *powerState*) {#powerStateChanged}

### QString Modem::primaryPort() const {#primaryPort}

Returns The name of the primary port using to control the modem.

### \[signal\] void Modem::primaryPortChanged(const QString &*primaryPort*) {#primaryPortChanged}

### \[since 6.24.0\] uint Modem::primarySimSlot() const {#primarySimSlot}

Returns the index of the primary active SIM slot in the [simSlots](modemmanager-modem.md#simSlots)() list, given in the \[1,N\] range.

If multiple SIM slots aren't supported, this property will report value 0.

In a Multi SIM Single Standby setup, this index identifies the only SIM that is currently active. In a Multi SIM Multi Standby setup, this index identifies the active SIM that is considered primary, i.e. the one that will be used when a data connection is setup.

This function was introduced in Qt 6.24.0.

*See also* [setPrimarySimSlot](modemmanager-modem.md#setPrimarySimSlot)()

### \[signal, since 6.24.0\] void Modem::primarySimSlotChanged(uint *slot*) {#primarySimSlotChanged}

This function was introduced in Qt 6.24.0.

### QDBusPendingReply\<void\> Modem::reset() {#reset}

Clear non-persistent configuration and state, and return the device to a newly-powered-on state.

This command may power-cycle the device.

### QString Modem::revision() const {#revision}

Returns The revision identification of the software, as reported by the modem.

### \[signal\] void Modem::revisionChanged(const QString &*revision*) {#revisionChanged}

### QDBusPendingReply\<void\> Modem::setCurrentBands(const QList\<MMModemBand\> &*bands*) {#setCurrentBands}

Set the radio frequency and technology bands the device is currently allowed to use when connecting to a network.

`bands` List of MMModemBand values, to specify the bands to be used.

*See also* [currentBands](modemmanager-modem.md#currentBands)()

### QDBusPendingReply\<void\> Modem::setCurrentCapabilities(ModemManager::Modem::Capabilities *caps*) {#setCurrentCapabilities}

Set the capabilities of the device. A restart of the modem may be required.

`caps` [QFlags](https://doc.qt.io/qt-6/qflags.html) of MMModemCapability values, to specify the capabilities to use.

*See also* [currentCapabilities](modemmanager-modem.md#currentCapabilities)()

### QDBusPendingReply\<void\> Modem::setCurrentModes(const ModemManager::CurrentModesType &*mode*) {#setCurrentModes}

Set the access technologies (e.g. 2G/3G/4G preference) the device is currently allowed to use when connecting to a network.

The given combination should be supported by the modem, as specified in [supportedModes](modemmanager-modem.md#supportedModes)()

*See also* [currentModes](modemmanager-modem.md#currentModes)()

### QDBusPendingReply\<void\> Modem::setEnabled(bool *enable*) {#setEnabled}

Enable or disable the modem.

When enabled, the modem's radio is powered on and data sessions, voice calls, location services, and Short Message Service may be available.

When disabled, the modem enters low-power state and no network-related operations are available.

*See also* [isEnabled](modemmanager-modem.md#isEnabled)()

### QDBusPendingReply\<void\> Modem::setPowerState(MMModemPowerState *state*) {#setPowerState}

Set the power `state` of the modem. This action can only be run when the modem is in MM\_MODEM\_STATE\_DISABLED state.

*See also* [powerState](modemmanager-modem.md#powerState)()

### \[since 6.24.0\] QDBusPendingReply\<void\> Modem::setPrimarySimSlot(uint *slot*) {#setPrimarySimSlot}

Selects which SIM slot to be considered as primary, on devices that expose multiple slots in the [simSlots](modemmanager-modem.md#simSlots)() property.

When the switch happens the modem may require a full device reprobe, so the modem object in DBus will get removed, and recreated once the selected SIM slot is in use.

There is no limitation on which SIM slot to select, so the user may also set as primary a slot that doesn't currently have any valid SIM card inserted.

`slot` SIM slot number to set as primary.

This function was introduced in Qt 6.24.0.

*See also* [primarySimSlot](modemmanager-modem.md#primarySimSlot)()

### void Modem::setTimeout(int *timeout*) {#setTimeout}

Sets the timeout in milliseconds for all async method DBus calls. -1 means the default DBus timeout (usually 25 seconds).

*See also* [timeout](modemmanager-modem.md#timeout)()

### ModemManager::SignalQualityPair Modem::signalQuality() const {#signalQuality}

Returns Signal quality in percent (0 - 100) of the dominant access technology the device is using to communicate with the network. Always 0 for POTS devices.

The additional boolean value indicates if the quality value given was recently taken.

### \[signal\] void Modem::signalQualityChanged(ModemManager::SignalQualityPair *signalQuality*) {#signalQualityChanged}

### QString Modem::simPath() const {#simPath}

Returns The path of the SIM object available in this device, if any.

### \[signal\] void Modem::simPathChanged(const QString &*oldPath*, const QString &*newPath*) {#simPathChanged}

### \[since 6.24.0\] ModemManager::UIntList Modem::simSlots() const {#simSlots}

Returns the list of SIM slots available in the system, including the SIM object paths if the cards are present. If a given SIM slot at a given index doesn't have a SIM card available, an empty object path will be given.

The length of this list will be equal to the amount of available SIM slots in the system, and the index in the list is the slot index.

This function was introduced in Qt 6.24.0.

### \[signal, since 6.24.0\] void Modem::simSlotsChanged(const ModemManager::UIntList &*simSlots*) {#simSlotsChanged}

This function was introduced in Qt 6.24.0.

### MMModemState Modem::state() const {#state}

Returns Overall state of the modem, given as a MMModemState value.

If the device's state cannot be determined, MM\_MODEM\_STATE\_UNKNOWN will be reported.

### \[signal\] void Modem::stateChanged(MMModemState *oldState*, MMModemState *newState*, MMModemStateChangeReason *reason*) {#stateChanged}

### MMModemStateFailedReason Modem::stateFailedReason() const {#stateFailedReason}

Returns Error specifying why the modem is in MM\_MODEM\_STATE\_FAILED state, given as a MMModemStateFailedReason value.

### \[signal\] void Modem::stateFailedReasonChanged(MMModemStateFailedReason *stateFailedReason*) {#stateFailedReasonChanged}

### QList\<MMModemBand\> Modem::supportedBands() const {#supportedBands}

Returns List of MMModemBand values, specifying the radio frequency and technology bands supported by the device.

For POTS devices, only the MM\_MODEM\_BAND\_ANY mode will be returned.

### \[signal\] void Modem::supportedBandsChanged(const QList\<MMModemBand\> &*supportedBands*) {#supportedBandsChanged}

### QList\<MMModemCapability\> Modem::supportedCapabilities() const {#supportedCapabilities}

Returns List of MMModemCapability values, specifying the combinations of generic family of access technologies the modem supports.

If the modem doesn't allow changing the current capabilities, a single entry with MM\_MODEM\_CAPABILITY\_ANY will be given.

### \[signal\] void Modem::supportedCapabilitiesChanged(const QList\<MMModemCapability\> &*supportedCapabilities*) {#supportedCapabilitiesChanged}

### ModemManager::Modem::IpBearerFamilies Modem::supportedIpFamilies() const {#supportedIpFamilies}

Returns [QFlags](https://doc.qt.io/qt-6/qflags.html) of MMBearerIpFamily values, specifying the IP families supported by the device.

### \[signal\] void Modem::supportedIpFamiliesChanged(QFlags\<MMBearerIpFamily\> *supportedIpFamilies*) {#supportedIpFamiliesChanged}

### ModemManager::SupportedModesType Modem::supportedModes() const {#supportedModes}

Returns This property exposes the supported mode combinations, given as an list of unsigned integer pairs, where: The first integer is a bitmask of MMModemMode values, specifying the allowed modes. The second integer is a single MMModemMode, which specifies the preferred access technology, among the ones defined in the allowed modes.

### \[signal\] void Modem::supportedModesChanged(ModemManager::SupportedModesType *supportedModes*) {#supportedModesChanged}

### int Modem::timeout() const {#timeout}

Returns the current value of the DBus timeout in milliseconds. -1 means the default DBus timeout (usually 25 seconds).

*See also* [setTimeout](modemmanager-modem.md#setTimeout)()

### QString Modem::uni() const {#uni}

### MMModemLock Modem::unlockRequired() const {#unlockRequired}

Returns Current lock state of the device, given as a MMModemLock value.

### \[signal\] void Modem::unlockRequiredChanged(MMModemLock *unlockRequired*) {#unlockRequiredChanged}

### ModemManager::UnlockRetriesMap Modem::unlockRetries() const {#unlockRetries}

Returns A dictionary in which the keys are MMModemLock flags, and the values are integers giving the number of PIN tries remaining before the code becomes blocked (requiring a PUK) or permanently blocked. Dictionary entries exist only for the codes for which the modem is able to report retry counts.

### \[signal\] void Modem::unlockRetriesChanged(const ModemManager::UnlockRetriesMap &*unlockRetries*) {#unlockRetriesChanged}
