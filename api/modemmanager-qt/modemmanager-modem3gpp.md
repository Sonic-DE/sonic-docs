---
title: "ModemManager::Modem3gpp Class"
description: "The Modem3gpp class."
---

# ModemManager::Modem3gpp Class

The Modem3gpp class. [More...](#details)

- **Header:** `#include <ModemManagerQt/Modem3gpp>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS ModemManagerQt)`  
  `target_link_libraries(mytarget PRIVATE KF6::ModemManagerQt)`
- **Inherits:** [ModemManager::Interface](modemmanager-interface.md)

[List of all members, including inherited members](modemmanager-modem3gpp-members.md)

## Public Types

- [Modem3gpp::List](#List-typedef)
- [Modem3gpp::Ptr](#Ptr-typedef)

## Public Functions

- [Modem3gpp(const QString &path, QObject \*parent = nullptr)](#Modem3gpp)
- [QString countryCode() const](#countryCode)
- [ModemManager::Modem3gpp::FacilityLocks enabledFacilityLocks() const](#enabledFacilityLocks)
- [QString imei() const](#imei)
- [QString operatorCode() const](#operatorCode)
- [QString operatorName() const](#operatorName)
- [void registerToNetwork(const QString &networkId = QString())](#registerToNetwork)
- [MMModem3gppRegistrationState registrationState() const](#registrationState)
- [QDBusPendingReply\<ModemManager::QVariantMapList\> scan()](#scan)
- [void setTimeout(int timeout)](#setTimeout)
- [MMModem3gppSubscriptionState subscriptionState() const](#subscriptionState)
- [int timeout() const](#timeout)

## Signals

- [void countryCodeChanged(const QString &countryCode)](#countryCodeChanged)
- [void enabledFacilityLocksChanged(QFlags\<MMModem3gppFacility\> locks)](#enabledFacilityLocksChanged)
- [void imeiChanged(const QString &imei)](#imeiChanged)
- [void operatorCodeChanged(const QString &operatorCode)](#operatorCodeChanged)
- [void operatorNameChanged(const QString &operatorName)](#operatorNameChanged)
- [void registrationStateChanged(MMModem3gppRegistrationState registrationState)](#registrationStateChanged)
- [void subscriptionStateChanged(MMModem3gppSubscriptionState subscriptionState)](#subscriptionStateChanged)

## Detailed Description {#details}

This class provides access to specific actions that may be performed in modems with 3GPP capabilities.

## Member Type Documentation {#member-type-documentation}

### Modem3gpp::List {#List-typedef}

### Modem3gpp::Ptr {#Ptr-typedef}

## Member Function Documentation {#member-function-documentation}

### \[explicit\] Modem3gpp::Modem3gpp(const QString &*path*, QObject \**parent* = nullptr) {#Modem3gpp}

### QString Modem3gpp::countryCode() const {#countryCode}

Returns country code of the operator to which the mobile is currently registered.

Returned in the format "ISO 3166-1 alpha-2" according to the MMC mapping from Wikipedia. Country Code is the two-letter country codes defined in ISO 3166-1, part of the ISO 3166 standard, e.g. "RU" or "FI".

If the MCC is not known or the mobile is not registered to a mobile network, this property will be an empty string.

### \[signal\] void Modem3gpp::countryCodeChanged(const QString &*countryCode*) {#countryCodeChanged}

### ModemManager::Modem3gpp::FacilityLocks Modem3gpp::enabledFacilityLocks() const {#enabledFacilityLocks}

Returns [QFlags](https://doc.qt.io/qt-6/qflags.html) of MMModem3gppFacility values for which PIN locking is enabled

### \[signal\] void Modem3gpp::enabledFacilityLocksChanged(QFlags\<MMModem3gppFacility\> *locks*) {#enabledFacilityLocksChanged}

### QString Modem3gpp::imei() const {#imei}

Returns the IMEI of the device

### \[signal\] void Modem3gpp::imeiChanged(const QString &*imei*) {#imeiChanged}

### QString Modem3gpp::operatorCode() const {#operatorCode}

Returns code of the operator to which the mobile is currently registered.

Returned in the format "MCCMNC", where MCC is the three-digit ITU E.212 Mobile Country Code and MNC is the two- or three-digit GSM Mobile Network Code. e.g. e"31026" or "310260".

If the MCC and MNC are not known or the mobile is not registered to a mobile network, this property will be an empty string.

### \[signal\] void Modem3gpp::operatorCodeChanged(const QString &*operatorCode*) {#operatorCodeChanged}

### QString Modem3gpp::operatorName() const {#operatorName}

Returns name of the operator to which the mobile is currently registered.

If the operator name is not known or the mobile is not registered to a mobile network, this property will be an empty string.

### \[signal\] void Modem3gpp::operatorNameChanged(const QString &*operatorName*) {#operatorNameChanged}

### void Modem3gpp::registerToNetwork(const QString &*networkId* = QString()) {#registerToNetwork}

Register the device to network.

`networkId` The operator ID (ie, "MCCMNC", like "310260") to register. An empty string can be used to register to the home network.

### MMModem3gppRegistrationState Modem3gpp::registrationState() const {#registrationState}

Returns mobile registration status as defined in 3GPP TS 27.007 section 10.1.19

### \[signal\] void Modem3gpp::registrationStateChanged(MMModem3gppRegistrationState *registrationState*) {#registrationStateChanged}

### QDBusPendingReply\<ModemManager::QVariantMapList\> Modem3gpp::scan() {#scan}

Scan for available networks.

Returns a [QList](https://doc.qt.io/qt-6/qlist.html)\<[QVariantMap](https://doc.qt.io/qt-6/qvariant.html#QVariantMap-typedef)\> with the results, where each map may contain these values:

"status": A MMModem3gppNetworkAvailability value representing network availability status, given as an unsigned integer (signature "u"). This key will always be present.

"operator-long": Long-format name of operator, given as a string value (signature "s"). If the name is unknown, this field should not be present.

"operator-short": Short-format name of operator, given as a string value (signature "s"). If the name is unknown, this field should not be present.

"operator-code": Mobile code of the operator, given as a string value (signature "s"). Returned in the format "MCCMNC", where MCC is the three-digit ITU E.212 Mobile Country Code and MNC is the two- or three-digit GSM Mobile Network Code. e.g. "31026" or "310260".

"access-technology": A MMModemAccessTechnology value representing the generic access technology used by this mobile network, given as an unsigned integer (signature "u").

### void Modem3gpp::setTimeout(int *timeout*) {#setTimeout}

Sets the timeout in milliseconds for all async method DBus calls. -1 means the default DBus timeout (usually 25 seconds).

*See also* [timeout](modemmanager-modem3gpp.md#timeout)()

### MMModem3gppSubscriptionState Modem3gpp::subscriptionState() const {#subscriptionState}

Returns Value representing the subscription status of the account and whether there is any data remaining.

### \[signal\] void Modem3gpp::subscriptionStateChanged(MMModem3gppSubscriptionState *subscriptionState*) {#subscriptionStateChanged}

### int Modem3gpp::timeout() const {#timeout}

Returns the current value of the DBus timeout in milliseconds. -1 means the default DBus timeout (usually 25 seconds).

*See also* [setTimeout](modemmanager-modem3gpp.md#setTimeout)()
