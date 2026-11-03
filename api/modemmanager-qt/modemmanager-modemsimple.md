---
title: "ModemManager::ModemSimple Class"
description: "The ModemSimple class."
---

# ModemManager::ModemSimple Class

The [ModemSimple](modemmanager-modemsimple.md) class. [More...](#details)

- **Header:** `#include <ModemManagerQt/ModemSimple>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS ModemManagerQt)`  
  `target_link_libraries(mytarget PRIVATE KF6::ModemManagerQt)`
- **Inherits:** [ModemManager::Interface](modemmanager-interface.md)

[List of all members, including inherited members](modemmanager-modemsimple-members.md)

## Public Types

- [ModemSimple::List](#List-typedef)
- [ModemSimple::Ptr](#Ptr-typedef)

## Public Functions

- [ModemSimple(const QString &path, QObject \*parent = nullptr)](#ModemSimple)
- [QDBusPendingReply\<QDBusObjectPath\> connectModem(const QVariantMap &properties)](#connectModem)
- [QDBusPendingReply\<void\> disconnectAllModems()](#disconnectAllModems)
- [QDBusPendingReply\<void\> disconnectModem(const QString &bearer)](#disconnectModem)
- [QDBusPendingReply\<QVariantMap\> getStatus()](#getStatus)
- [void setTimeout(int timeout)](#setTimeout)
- [int timeout() const](#timeout)
- [QString uni() const](#uni)

## Detailed Description {#details}

The Simple interface allows controlling and querying the status of Modems.

## Member Type Documentation {#member-type-documentation}

### ModemSimple::List {#List-typedef}

### ModemSimple::Ptr {#Ptr-typedef}

## Member Function Documentation {#member-function-documentation}

### \[explicit\] ModemSimple::ModemSimple(const QString &*path*, QObject \**parent* = nullptr) {#ModemSimple}

### QDBusPendingReply\<QDBusObjectPath\> ModemSimple::connectModem(const QVariantMap &*properties*) {#connectModem}

Do everything needed to connect the modem using the given properties.

This method will attempt to find a matching packet data bearer and activate it if necessary, returning the bearer's IP details. If no matching bearer is found, a new bearer will be created and activated, but this operation may fail if no resources are available to complete this connection attempt (ie, if a conflicting bearer is already active).

This call may make a large number of changes to modem configuration based on properties passed in. For example, given a PIN-locked, disabled GSM/UMTS modem, this call may unlock the SIM PIN, alter the access technology preference, wait for network registration (or force registration to a specific provider), create a new packet data bearer using the given "apn", and connect that bearer.

Dictionary of properties needed to get the modem connected. Each implementation is free to add its own specific key-value pairs. The predefined common ones are:

`pin` SIM-PIN unlock code, given as a string value (signature "s").

`operator-id` ETSI MCC-MNC of a network to force registration with, given as a string value (signature "s").

`apn` For GSM/UMTS and LTE devices the APN to use, given as a string value (signature "s").

`ip-type` For GSM/UMTS and LTE devices the IP addressing type to use, given as a MMBearerIpFamily value (signature "u").

`allowed-auth` The authentication method to use, given as a MMBearerAllowedAuth value (signature "u"). Optional in 3GPP.

`user` User name (if any) required by the network, given as a string value (signature "s"). Optional in 3GPP.

`password` Password (if any) required by the network, given as a string value (signature "s"). Optional in 3GPP.

`number` For POTS devices the number to dial,, given as a string value (signature "s").

`allow-roaming` FALSE to allow only connections to home networks, given as a boolean value (signature "b").

`rm-protocol` For CDMA devices, the protocol of the Rm interface, given as a MMModemCdmaRmProtocol value (signature "u").

Returns On successful connect, returns the object path of the connected packet data bearer used for the connection attempt.

### QDBusPendingReply\<void\> ModemSimple::disconnectAllModems() {#disconnectAllModems}

Convenient method calling [disconnectModem](modemmanager-modemsimple.md#disconnectModem) with "/" to make [ModemManager](modemmanager.md) disconnect all modems

### QDBusPendingReply\<void\> ModemSimple::disconnectModem(const QString &*bearer*) {#disconnectModem}

Disconnect an active packet data connection.

### QDBusPendingReply\<QVariantMap\> ModemSimple::getStatus() {#getStatus}

Dictionary of properties. Each implementation is free to add it's own specific key-value pairs. The predefined common ones are:

`state` A MMModemState value specifying the overall state of the modem, given as an unsigned integer value (signature "u").

`signal-quality` Signal quality value, given only when registered, as an unsigned integer value (signature "u").

`current-bands` List of MMModemBand values, given only when registered, as a list of unsigned integer values (signature "au").

`access-technology` A MMModemAccessTechnology value, given only when registered, as an unsigned integer value (signature "u").

`m3gpp-registration-state` A MMModem3gppRegistrationState value specifying the state of the registration, given only when registered in a 3GPP network, as an unsigned integer value (signature "u").

`m3gpp-operator-code` Operator MCC-MNC, given only when registered in a 3GPP network, as a string value (signature "s").

`m3gpp-operator-name` Operator name, given only when registered in a 3GPP network, as a string value (signature "s").

`cdma-cdma1x-registration-state` A MMModemCdmaRegistrationState value specifying the state of the registration, given only when registered in a CDMA1x network, as an unsigned integer value (signature "u").

`cdma-evdo-registration-state` A MMModemCdmaRegistrationState value specifying the state of the registration, given only when registered in a EV-DO network, as an unsigned integer value (signature "u").

`cdma-sid` The System Identifier of the serving network, if registered in a CDMA1x network and if known. Given as an unsigned integer value (signature "u").

`cdma-nid` The Network Identifier of the serving network, if registered in a CDMA1x network and if known. Given as an unsigned integer value (signature "u").

### void ModemSimple::setTimeout(int *timeout*) {#setTimeout}

Sets the timeout in milliseconds for all async method DBus calls.

-1 means the default DBus timeout (usually 25 seconds).

*See also* [timeout](modemmanager-modemsimple.md#timeout)()

### int ModemSimple::timeout() const {#timeout}

Returns the current value of the DBus timeout in milliseconds.

-1 means the default DBus timeout (usually 25 seconds).

*See also* [setTimeout](modemmanager-modemsimple.md#setTimeout)()

### QString ModemSimple::uni() const {#uni}
