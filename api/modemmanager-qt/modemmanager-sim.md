---
title: "ModemManager::Sim Class"
description: "The Sim class."
---

# ModemManager::Sim Class

The Sim class. [More...](#details)

- **Header:** `#include <ModemManagerQt/Sim>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS ModemManagerQt)`  
  `target_link_libraries(mytarget PRIVATE KF6::ModemManagerQt)`
- **Inherits:** [QObject](https://doc.qt.io/qt-6/qobject.html)

[List of all members, including inherited members](modemmanager-sim-members.md)

## Public Types

- [Sim::List](#List-typedef)
- [Sim::Ptr](#Ptr-typedef)

## Public Functions

- [Sim(const QString &path, QObject \*parent = nullptr)](#Sim)
- [bool active() const](#active)
- [QDBusPendingReply\<\> changePin(const QString &oldPin, const QString &newPin)](#changePin)
- [QString eid() const](#eid)
- [QStringList emergencyNumbers() const](#emergencyNumbers)
- [QDBusPendingReply\<\> enablePin(const QString &pin, bool enabled)](#enablePin)
- [MMSimEsimStatus esimStatus() const](#esimStatus)
- [QByteArray gid1() const](#gid1)
- [QByteArray gid2() const](#gid2)
- [QString imsi() const](#imsi)
- [QString operatorIdentifier() const](#operatorIdentifier)
- [QString operatorName() const](#operatorName)
- [QVariantMap preferredNetworks() const](#preferredNetworks)
- [MMSimRemovability removability() const](#removability)
- [QDBusPendingReply\<\> sendPin(const QString &pin)](#sendPin)
- [QDBusPendingReply\<\> sendPuk(const QString &puk, const QString &pin)](#sendPuk)
- [QDBusPendingReply\<\> setPreferredNetworks(QVariantMap preferredNetworks)](#setPreferredNetworks)
- [void setTimeout(int timeout)](#setTimeout)
- [QString simIdentifier() const](#simIdentifier)
- [MMSimType simType() const](#simType)
- [int timeout() const](#timeout)
- [QString uni() const](#uni)

## Signals

- [void activeChanged(bool active)](#activeChanged)
- [void eidChanged(const QString &eid)](#eidChanged)
- [void emergencyNumbersChanged(const QStringList &emergencyNumbers)](#emergencyNumbersChanged)
- [void esimStatusChanged(MMSimEsimStatus esimStatus)](#esimStatusChanged)
- [void gid1Changed(const QByteArray &gid1)](#gid1Changed)
- [void gid2Changed(const QByteArray &gid2)](#gid2Changed)
- [void imsiChanged(const QString &imsi)](#imsiChanged)
- [void operatorIdentifierChanged(const QString &identifier)](#operatorIdentifierChanged)
- [void operatorNameChanged(const QString &name)](#operatorNameChanged)
- [void preferredNetworksChanged(const QVariantMap &preferredNetworks)](#preferredNetworksChanged)
- [void removabilityChanged(MMSimRemovability removability)](#removabilityChanged)
- [void simIdentifierChanged(const QString &identifier)](#simIdentifierChanged)
- [void simTypeChanged(MMSimType simType)](#simTypeChanged)

## Detailed Description {#details}

The SIM class handles communication with SIM, USIM, and RUIM (CDMA SIM) cards.

## Member Type Documentation {#member-type-documentation}

### Sim::List {#List-typedef}

### Sim::Ptr {#Ptr-typedef}

## Member Function Documentation {#member-function-documentation}

### \[explicit\] Sim::Sim(const QString &*path*, QObject \**parent* = nullptr) {#Sim}

### bool Sim::active() const {#active}

\* Returns Boolean indicating whether the SIM is currently active. \* \* On systems that support Multi SIM Single Standby, only one SIM may be \* active at any given time, which will be the one considered primary.

\* On systems that support Multi SIM Multi Standby, more than one SIM may \* be active at any given time, but only one of them is considered primary.

### \[signal\] void Sim::activeChanged(bool *active*) {#activeChanged}

### QDBusPendingReply\<\> Sim::changePin(const QString &*oldPin*, const QString &*newPin*) {#changePin}

Change the PIN code.

`oldPin` A string containing the current PIN code.

`newPin` A string containing the new PIN code.

### QString Sim::eid() const {#eid}

Returns The EID of the SIM card, if any.

### \[signal\] void Sim::eidChanged(const QString &*eid*) {#eidChanged}

### QStringList Sim::emergencyNumbers() const {#emergencyNumbers}

Returns List of emergency numbers programmed in the SIM card.

These numbers should be treated as numbers for emergency calls in addition to 112 and 911.

### \[signal\] void Sim::emergencyNumbersChanged(const QStringList &*emergencyNumbers*) {#emergencyNumbersChanged}

### QDBusPendingReply\<\> Sim::enablePin(const QString &*pin*, bool *enabled*) {#enablePin}

Enable or disable the PIN checking.

`pin` A string containing the PIN code.

`enabled` TRUE to enable PIN checking, FALSE otherwise.

### MMSimEsimStatus Sim::esimStatus() const {#esimStatus}

Returns If current SIM is ESIM then this indicates whether there is a profile or not.

### \[signal\] void Sim::esimStatusChanged(MMSimEsimStatus *esimStatus*) {#esimStatusChanged}

### QByteArray Sim::gid1() const {#gid1}

Returns Group identifier 1evel 1.

### QByteArray Sim::gid2() const {#gid2}

Returns Group identifier 1evel 2.

### \[signal\] void Sim::gid1Changed(const QByteArray &*gid1*) {#gid1Changed}

### \[signal\] void Sim::gid2Changed(const QByteArray &*gid2*) {#gid2Changed}

### QString Sim::imsi() const {#imsi}

Returns The IMSI of the SIM card, if any.

### \[signal\] void Sim::imsiChanged(const QString &*imsi*) {#imsiChanged}

### QString Sim::operatorIdentifier() const {#operatorIdentifier}

Returns The ID of the network operator, as given by the SIM card, if known.

### \[signal\] void Sim::operatorIdentifierChanged(const QString &*identifier*) {#operatorIdentifierChanged}

### QString Sim::operatorName() const {#operatorName}

Returns The name of the network operator, as given by the SIM card, if known.

### \[signal\] void Sim::operatorNameChanged(const QString &*name*) {#operatorNameChanged}

### QVariantMap Sim::preferredNetworks() const {#preferredNetworks}

Returns Map of preferred networks with access technologies configured in the SIM card.

Each entry contains an operator id string key "MCCMNC" consisting of 5 or 6 digits, to an MMModemAccessTechnology mask value. If the SIM card does not support access technology storage, the mask will be set to MM\_MODEM\_ACCESS\_TECHNOLOGY\_UNKNOWN.

*See also* [setPreferredNetworks](modemmanager-sim.md#setPreferredNetworks)()

### \[signal\] void Sim::preferredNetworksChanged(const QVariantMap &*preferredNetworks*) {#preferredNetworksChanged}

### MMSimRemovability Sim::removability() const {#removability}

Returns Indicates whether the current SIM is a removable SIM or not.

### \[signal\] void Sim::removabilityChanged(MMSimRemovability *removability*) {#removabilityChanged}

### QDBusPendingReply\<\> Sim::sendPin(const QString &*pin*) {#sendPin}

Send the PIN to unlock the SIM card.

`pin` A string containing the PIN code.

### QDBusPendingReply\<\> Sim::sendPuk(const QString &*puk*, const QString &*pin*) {#sendPuk}

Send the PUK and a new PIN to unlock the SIM card.

`puk` A string containing the PUK code.

`pin` A string containing the PIN code.

### QDBusPendingReply\<\> Sim::setPreferredNetworks(QVariantMap *preferredNetworks*) {#setPreferredNetworks}

`preferred_plmns` List of preferred networks.

Stores the provided preferred network list to the SIM card. Each entry contains an operator id string ("MCCMNC") consisting of 5 or 6 digits, and an MMModemAccessTechnology mask to store to SIM card if supported.

This method removes any pre-existing entries of the preferred network list. Note that even if this operation fails, the preferred network list on the SIM card may have changed.

*See also* [preferredNetworks](modemmanager-sim.md#preferredNetworks)()

### void Sim::setTimeout(int *timeout*) {#setTimeout}

Sets the timeout in milliseconds for all async method DBus calls. -1 means the default DBus timeout (usually 25 seconds).

*See also* [timeout](modemmanager-sim.md#timeout)()

### QString Sim::simIdentifier() const {#simIdentifier}

Returns The ICCID of the SIM card.

This may be available before the PIN has been entered depending on the device itself.

### \[signal\] void Sim::simIdentifierChanged(const QString &*identifier*) {#simIdentifierChanged}

### MMSimType Sim::simType() const {#simType}

Returns Indicates whether the current primary SIM is a ESIM or a physical SIM.

### \[signal\] void Sim::simTypeChanged(MMSimType *simType*) {#simTypeChanged}

### int Sim::timeout() const {#timeout}

Returns the current value of the DBus timeout in milliseconds. -1 means the default DBus timeout (usually 25 seconds).

*See also* [setTimeout](modemmanager-sim.md#setTimeout)()

### QString Sim::uni() const {#uni}
