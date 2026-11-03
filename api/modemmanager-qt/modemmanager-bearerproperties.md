---
title: "ModemManager::BearerProperties Class"
description: "This class represents bearer properties used for creating of new bearers."
---

# ModemManager::BearerProperties Class

This class represents bearer properties used for creating of new bearers. [More...](#details)

- **Header:** `#include <ModemManagerQt/Modem>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS ModemManagerQt)`  
  `target_link_libraries(mytarget PRIVATE KF6::ModemManagerQt)`

[List of all members, including inherited members](modemmanager-bearerproperties-members.md)

## Public Functions

- [BearerProperties()](#BearerProperties)
- [BearerProperties(const ModemManager::BearerProperties &other)](#BearerProperties-1)
- [~BearerProperties()](#dtor.BearerProperties)
- [bool allowRoaming() const](#allowRoaming)
- [MMBearerAllowedAuth allowedAuthentication() const](#allowedAuthentication)
- [QString apn() const](#apn)
- [MMBearerIpFamily ipType() const](#ipType)
- [QString number() const](#number)
- [QString password() const](#password)
- [MMModemCdmaRmProtocol rmProtocol() const](#rmProtocol)
- [void setAllowRoaming(bool allow)](#setAllowRoaming)
- [void setAllowedAuthentication(MMBearerAllowedAuth allowedAuth)](#setAllowedAuthentication)
- [void setApn(const QString &apn)](#setApn)
- [void setIpType(MMBearerIpFamily ipType)](#setIpType)
- [void setNumber(const QString &number)](#setNumber)
- [void setPassword(const QString &password)](#setPassword)
- [void setRmProtocol(MMModemCdmaRmProtocol rmProtocol)](#setRmProtocol)
- [void setUser(const QString &user)](#setUser)
- [QString user() const](#user)
- [ModemManager::BearerProperties &BearerProperties::operator=(const ModemManager::BearerProperties &other)](#operator-eq)

## Detailed Description {#details}

## Member Function Documentation {#member-function-documentation}

### BearerProperties::BearerProperties() {#BearerProperties}

Constructs an empty [BearerProperties](modemmanager-bearerproperties.md) object

### BearerProperties::BearerProperties(const ModemManager::BearerProperties &*other*) {#BearerProperties-1}

Constructs a [BearerProperties](modemmanager-bearerproperties.md) object that is a copy of the object `other`.

### \[noexcept\] BearerProperties::~BearerProperties() {#dtor.BearerProperties}

Destroys this [BearerProperties](modemmanager-bearerproperties.md) object.

### bool BearerProperties::allowRoaming() const {#allowRoaming}

Returns whether connection is allowed during roaming

*See also* [setAllowRoaming](modemmanager-bearerproperties.md#setAllowRoaming)()

### MMBearerAllowedAuth BearerProperties::allowedAuthentication() const {#allowedAuthentication}

Returns used authentication method

*See also* [setAllowedAuthentication](modemmanager-bearerproperties.md#setAllowedAuthentication)()

### QString BearerProperties::apn() const {#apn}

Returns Access Point Name

*See also* [setApn](modemmanager-bearerproperties.md#setApn)()

### MMBearerIpFamily BearerProperties::ipType() const {#ipType}

Returns addressing type

*See also* [setIpType](modemmanager-bearerproperties.md#setIpType)()

### QString BearerProperties::number() const {#number}

Returns telephone number to dial

*See also* [setNumber](modemmanager-bearerproperties.md#setNumber)()

### QString BearerProperties::password() const {#password}

Returns password

*See also* [setPassword](modemmanager-bearerproperties.md#setPassword)()

### MMModemCdmaRmProtocol BearerProperties::rmProtocol() const {#rmProtocol}

Returns protocol of the Rm interface

*See also* [setRmProtocol](modemmanager-bearerproperties.md#setRmProtocol)()

### void BearerProperties::setAllowRoaming(bool *allow*) {#setAllowRoaming}

Sets whether connection is allowed during roaming

*See also* [allowRoaming](modemmanager-bearerproperties.md#allowRoaming)()

### void BearerProperties::setAllowedAuthentication(MMBearerAllowedAuth *allowedAuth*) {#setAllowedAuthentication}

Sets the authentication method to use

*See also* [allowedAuthentication](modemmanager-bearerproperties.md#allowedAuthentication)()

### void BearerProperties::setApn(const QString &*apn*) {#setApn}

Sets Access Point Name

*See also* [apn](modemmanager-bearerproperties.md#apn)()

### void BearerProperties::setIpType(MMBearerIpFamily *ipType*) {#setIpType}

Sets addressing type

*See also* [ipType](modemmanager-bearerproperties.md#ipType)()

### void BearerProperties::setNumber(const QString &*number*) {#setNumber}

Sets telephone number to dial

*See also* [number](modemmanager-bearerproperties.md#number)()

### void BearerProperties::setPassword(const QString &*password*) {#setPassword}

Sets password

*See also* [password](modemmanager-bearerproperties.md#password)()

### void BearerProperties::setRmProtocol(MMModemCdmaRmProtocol *rmProtocol*) {#setRmProtocol}

Sets protocol of the Rm interface

*See also* [rmProtocol](modemmanager-bearerproperties.md#rmProtocol)()

### void BearerProperties::setUser(const QString &*user*) {#setUser}

Sets user name

*See also* [user](modemmanager-bearerproperties.md#user)()

### QString BearerProperties::user() const {#user}

Returns user name

*See also* [setUser](modemmanager-bearerproperties.md#setUser)()

### ModemManager::BearerProperties &BearerProperties::operator=(const ModemManager::BearerProperties &*other*) {#operator-eq}

Makes a copy of the [IpConfig](modemmanager-ipconfig.md) object `other`.
