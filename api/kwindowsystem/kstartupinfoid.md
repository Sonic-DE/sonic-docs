---
title: "KStartupInfoId Class"
description: "Class representing an identification of application startup notification."
---

# KStartupInfoId Class

Class representing an identification of application startup notification. [More...](#details)

- **Header:** `#include <KStartupInfo>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS KWindowSystem)`  
  `target_link_libraries(mytarget PRIVATE KF6::KWindowSystem)`

[List of all members, including inherited members](kstartupinfoid-members.md)

## Public Functions

- [KStartupInfoId()](#KStartupInfoId)
- [KStartupInfoId(const KStartupInfoId &data)](#KStartupInfoId-1)
- [const QByteArray &id() const](#id)
- [void initId(const QByteArray &id = "")](#initId)
- [bool isNull() const](#isNull)
- [bool setupStartupEnv() const](#setupStartupEnv)
- [unsigned long timestamp() const](#timestamp)
- [bool KStartupInfoId::operator!=(const KStartupInfoId &id) const](#operator-not-eq)
- [bool KStartupInfoId::operator==(const KStartupInfoId &id) const](#operator-eq-eq)

## Detailed Description {#details}

Every existing notification about a starting application has its own unique identification, that's used to identify and manipulate the notification.

*See also* [KStartupInfo](kstartupinfo.md), [KStartupInfoData](kstartupinfodata.md)

## Member Function Documentation {#member-function-documentation}

### KStartupInfoId::KStartupInfoId() {#KStartupInfoId}

Creates an empty identification

### KStartupInfoId::KStartupInfoId(const KStartupInfoId &*data*) {#KStartupInfoId-1}

Copy constructor.

### const QByteArray &KStartupInfoId::id() const {#id}

Returns the notification identifier as string.

### void KStartupInfoId::initId(const QByteArray &*id* = "") {#initId}

Initializes this object with the given identification (which may be also "0" for no notification), or if "" is given, tries to read it from the startup notification environment variable, and if it's not set, creates a new one.

`id` The new identification, "0" for no notification or "" to read the environment variable.

### bool KStartupInfoId::isNull() const {#isNull}

Checks whether the identifier is valid.

Returns true if this object doesn't represent a valid notification identification.

### bool KStartupInfoId::setupStartupEnv() const {#setupStartupEnv}

Sets the startup notification environment variable to this identification.

Returns `true` if successful, `false` otherwise.

### unsigned long KStartupInfoId::timestamp() const {#timestamp}

Returns the user timestamp for the startup notification, or 0 if no timestamp is set.

### bool KStartupInfoId::operator!=(const KStartupInfoId &*id*) const {#operator-not-eq}

Overloaded operator.

Returns `true` if the given notification `id` is different.

### bool KStartupInfoId::operator==(const KStartupInfoId &*id*) const {#operator-eq-eq}

Overloaded operator.

Returns `true` if the given notification `id` is the same.
