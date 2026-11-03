---
title: "ModemManager::ModemCdma Class"
description: "The ModemCdma class."
---

# ModemManager::ModemCdma Class

The [ModemCdma](modemmanager-modemcdma.md) class. [More...](#details)

- **Header:** `#include <ModemManagerQt/ModemCdma>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS ModemManagerQt)`  
  `target_link_libraries(mytarget PRIVATE KF6::ModemManagerQt)`
- **Inherits:** [ModemManager::Interface](modemmanager-interface.md)

[List of all members, including inherited members](modemmanager-modemcdma-members.md)

## Public Types

- [ModemCdma::List](#List-typedef)
- [ModemCdma::Ptr](#Ptr-typedef)

## Public Functions

- [ModemCdma(const QString &path, QObject \*parent = nullptr)](#ModemCdma)
- [QDBusPendingReply\<void\> activate(const QString &carrierCode)](#activate)
- [QDBusPendingReply\<void\> activateManual(const QVariantMap &properties)](#activateManual)
- [MMModemCdmaActivationState activationState() const](#activationState)
- [MMModemCdmaRegistrationState cdma1xRegistrationState() const](#cdma1xRegistrationState)
- [QString esn() const](#esn)
- [MMModemCdmaRegistrationState evdoRegistrationState() const](#evdoRegistrationState)
- [QString meid() const](#meid)
- [uint nid() const](#nid)
- [void setTimeout(int timeout)](#setTimeout)
- [uint sid() const](#sid)
- [int timeout() const](#timeout)

## Signals

- [void activationStateChanged(MMModemCdmaActivationState state, MMCdmaActivationError error, const QVariantMap &status\_changes)](#activationStateChanged)
- [void cdma1xRegistrationStateChanged(MMModemCdmaRegistrationState cdma1xRegistrationState)](#cdma1xRegistrationStateChanged)
- [void esnChanged(const QString &esn)](#esnChanged)
- [void evdoRegistrationStateChanged(MMModemCdmaRegistrationState evdoRegistrationState)](#evdoRegistrationStateChanged)
- [void meidChanged(const QString &meid)](#meidChanged)
- [void nidChanged(uint nid)](#nidChanged)
- [void sidChanged(uint sid)](#sidChanged)

## Detailed Description {#details}

This class provides access to specific actions that may be performed in modems with CDMA capabilities.

## Member Type Documentation {#member-type-documentation}

### ModemCdma::List {#List-typedef}

### ModemCdma::Ptr {#Ptr-typedef}

## Member Function Documentation {#member-function-documentation}

### \[explicit\] ModemCdma::ModemCdma(const QString &*path*, QObject \**parent* = nullptr) {#ModemCdma}

### QDBusPendingReply\<void\> ModemCdma::activate(const QString &*carrierCode*) {#activate}

Provisions the modem for use with a given carrier using the modem's Over-The-Air (OTA) activation functionality, if any.

Some modems will reboot after this call is made.

`carrierCode` name of carrier, or carrier-specific code

### QDBusPendingReply\<void\> ModemCdma::activateManual(const QVariantMap &*properties*) {#activateManual}

Sets the modem provisioning data directly, without contacting the carrier over the air.

Some modems will reboot after this call is made.

`properties` [QVariantMap](https://doc.qt.io/qt-6/qvariant.html#QVariantMap-typedef) consisting of:

"spc": The Service Programming Code, given as a string of exactly 6 digit characters. Mandatory parameter. "sid": The System Identification Number, given as a 16-bit unsigned integer (signature "q"). Mandatory parameter. "mdn": The Mobile Directory Number, given as a string of maximum 15 characters. Mandatory parameter. "min": The Mobile Identification Number, given as a string of maximum 15 characters. Mandatory parameter. "mn-ha-key": The MN-HA key, given as a string of maximum 16 characters. "mn-aaa-key": The MN-AAA key, given as a string of maximum 16 characters. "prl": The Preferred Roaming List, given as an array of maximum 16384 bytes.

### MMModemCdmaActivationState ModemCdma::activationState() const {#activationState}

Returns a MMModemCdmaActivationState value specifying the state of the activation in the 3GPP2 network.

### \[signal\] void ModemCdma::activationStateChanged(MMModemCdmaActivationState *state*, MMCdmaActivationError *error*, const QVariantMap &*status\_changes*) {#activationStateChanged}

This signal is emitted when the activation info this network changes

`state` current activation state, given as a MMModemCdmaActivationState.

`error` carrier-specific error code, given as a MMCdmaActivationError.

`status_changes` properties that have changed as a result of this activation state change, including "mdn" and "min". The map may be empty if the changed properties are unknown.

### MMModemCdmaRegistrationState ModemCdma::cdma1xRegistrationState() const {#cdma1xRegistrationState}

Returns a MMModemCdmaRegistrationState value specifying the CDMA 1x registration state.

### \[signal\] void ModemCdma::cdma1xRegistrationStateChanged(MMModemCdmaRegistrationState *cdma1xRegistrationState*) {#cdma1xRegistrationStateChanged}

### QString ModemCdma::esn() const {#esn}

Returns the modem's Electronic Serial Number (superseded by MEID but still used by older devices).

### \[signal\] void ModemCdma::esnChanged(const QString &*esn*) {#esnChanged}

### MMModemCdmaRegistrationState ModemCdma::evdoRegistrationState() const {#evdoRegistrationState}

Returns a MMModemCdmaRegistrationState value specifying the EVDO registration state.

### \[signal\] void ModemCdma::evdoRegistrationStateChanged(MMModemCdmaRegistrationState *evdoRegistrationState*) {#evdoRegistrationStateChanged}

### QString ModemCdma::meid() const {#meid}

Returns the modem's Mobile Equipment Identifier.

### \[signal\] void ModemCdma::meidChanged(const QString &*meid*) {#meidChanged}

### uint ModemCdma::nid() const {#nid}

Returns the Network Identifier of the serving CDMA 1x network, if known, and if the modem is registered with a CDMA 1x network.

### \[signal\] void ModemCdma::nidChanged(uint *nid*) {#nidChanged}

### void ModemCdma::setTimeout(int *timeout*) {#setTimeout}

Sets the timeout in milliseconds for all async method DBus calls. -1 means the default DBus timeout (usually 25 seconds).

*See also* [timeout](modemmanager-modemcdma.md#timeout)()

### uint ModemCdma::sid() const {#sid}

Returns the System Identifier of the serving CDMA 1x network, if known, and if the modem is registered with a CDMA 1x network.

*See also* [http://ifast.org](http://ifast.org), or, the, mobile, broadband, provider, database, for, mappings, of, SIDs, to, network, providers

### \[signal\] void ModemCdma::sidChanged(uint *sid*) {#sidChanged}

### int ModemCdma::timeout() const {#timeout}

Returns the current value of the DBus timeout in milliseconds. -1 means the default DBus timeout (usually 25 seconds).

*See also* [setTimeout](modemmanager-modemcdma.md#setTimeout)()
