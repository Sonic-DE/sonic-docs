---
title: "SignOn::SecurityContext Class"
description: "Contains access security context information."
---

# SignOn::SecurityContext Class

Contains access security context information. [More...](#details)

- **Header:** `#include <SignOn/SecurityContext>`
- **CMake:** `find_package(SignOnQt6 REQUIRED)`  
  `target_link_libraries(mytarget PRIVATE SignOnQt6::SignOnQt6)`

[List of all members, including inherited members](signon-securitycontext-members.md)

## Public Functions

- [SecurityContext()](#SecurityContext)
- [SecurityContext(const QString &systemContext, const QString &applicationContext)](#SecurityContext-1)
- [QString applicationContext() const](#applicationContext)
- [void setApplicationContext(const QString &applicationContext)](#setApplicationContext)
- [void setSystemContext(const QString &systemContext)](#setSystemContext)
- [QString systemContext() const](#systemContext)

## Detailed Description {#details}

*See also* [IdentityInfo::accessControlListFull](signon-identityinfo.md#accessControlListFull)()

## Member Function Documentation {#member-function-documentation}

### SecurityContext::SecurityContext() {#SecurityContext}

Creates a new [SecurityContext](signon-securitycontext.md) object.

### SecurityContext::SecurityContext(const QString &*systemContext*, const QString &*applicationContext*) {#SecurityContext-1}

Creates a new [SecurityContext](signon-securitycontext.md) object with the `systemContext` and the `applicationContext`.

### QString SecurityContext::applicationContext() const {#applicationContext}

Gets the application context, or an empty string.

*See also* [setApplicationContext](signon-securitycontext.md#setApplicationContext)()

### void SecurityContext::setApplicationContext(const QString &*applicationContext*) {#setApplicationContext}

Sets the application context to `applicationContext`.

*See also* [applicationContext](signon-securitycontext.md#applicationContext)()

### void SecurityContext::setSystemContext(const QString &*systemContext*) {#setSystemContext}

Sets the system context to `systemContext`.

*See also* [systemContext](signon-securitycontext.md#systemContext)()

### QString SecurityContext::systemContext() const {#systemContext}

Gets the system context, or an empty string.

*See also* [setSystemContext](signon-securitycontext.md#setSystemContext)()
