---
title: "SignOn::AuthService Class"
description: "Represents signon for client application."
---

# SignOn::AuthService Class

Represents signon for client application. [More...](#details)

- **Header:** `#include <SignOn/AuthService>`
- **CMake:** `find_package(SignOnQt6 REQUIRED)`  
  `target_link_libraries(mytarget PRIVATE SignOnQt6::SignOnQt6)`
- **Inherits:** [QObject](https://doc.qt.io/qt-6/qobject.html)

[List of all members, including inherited members](signon-authservice-members.md)  
[Deprecated members](signon-authservice-obsolete.md)

## Public Types

- [AuthService::IdentityFilter](#IdentityFilter-typedef)
- [enum AuthService::IdentityFilterCriteria](#IdentityFilterCriteria-enum)

## Public Functions

- [AuthService(QObject \*parent = 0)](#AuthService)
- [~AuthService()](#dtor.AuthService)
- [void clear()](#clear)
- [void queryIdentities(const SignOn::AuthService::IdentityFilter &filter = IdentityFilter())](#queryIdentities)
- [void queryMechanisms(const QString &method)](#queryMechanisms)
- [void queryMethods()](#queryMethods)

## Signals

- [void cleared()](#cleared)
- [void error(const SignOn::Error &err)](#error)
- [void identities(const QList\<SignOn::IdentityInfo\> &identityList)](#identities)
- [void mechanismsAvailable(const QString &method, const QStringList &mechanisms)](#mechanismsAvailable)
- [void methodsAvailable(const QStringList &methods)](#methodsAvailable)

## Detailed Description {#details}

The class is for managing identities. Most applications can use this by using widgets from libSignOnUI.

## Member Type Documentation {#member-type-documentation}

### AuthService::IdentityFilter {#IdentityFilter-typedef}

Map to hold different filtering options.

### enum AuthService::IdentityFilterCriteria {#IdentityFilterCriteria-enum}

Criteria for identity query filtering.

| Constant | Value | Description |
| --- | --- | --- |
| `SignOn::AuthService::AuthMethod` | `0` | The authentication method. |
| `SignOn::AuthService::Username` | `1` | The username. |
| `SignOn::AuthService::Realm` | `2` | The realm. |
| `SignOn::AuthService::Caption` | `3` | The caption. |

*See also* [queryIdentities](signon-authservice.md#queryIdentities)()

## Member Function Documentation {#member-function-documentation}

### AuthService::AuthService(QObject \**parent* = 0) {#AuthService}

Basic constructor, with the given `parent`.

### \[virtual noexcept\] AuthService::~AuthService() {#dtor.AuthService}

Destructor

### void AuthService::clear() {#clear}

Clears credentials database. All identity entries are removed from database. Signal [cleared](signon-authservice.md#cleared)() is emitted when operation is completed. Error is reported by emitting signal [error](signon-authservice.md#error)(). If the application does not have keychain-access credential, [Error::type](signon-error.md#type)() is [Error::PermissionDenied](signon-error.md#ErrorType-enum).

Needs the keychain-access credential: only a key-chain application can clear the database.

*See also* [cleared](signon-authservice.md#cleared)(), [error](signon-authservice.md#error)()

### \[signal\] void AuthService::cleared() {#cleared}

Database is cleared and reset to initial state. This signal is emitted in response to [clear](signon-authservice.md#clear)().

### \[signal\] void AuthService::error(const SignOn::Error &*err*) {#error}

Emitted when an error occurs while using the [AuthService](signon-authservice.md); `err` is the error. Typical error types are generic errors, where [Error::type](signon-error.md#type)() \< [Error::AuthServiceErr](signon-error.md#ErrorType-enum) and [AuthService](signon-authservice.md) specific, where [Error::AuthServiceErr](signon-error.md#ErrorType-enum) \< [Error::type](signon-error.md#type)() \< [Error::IdentityErr](signon-error.md#ErrorType-enum)

*See also* [SignOn::Error](signon-error.md), [SignOn::Error::ErrorType](signon-error.md#ErrorType-enum)

### \[signal\] void AuthService::identities(const QList\<SignOn::IdentityInfo\> &*identityList*) {#identities}

Lists identities available on the server matching query parameters; `identityList` holds their information. This signal is emitted in response to [queryIdentities](signon-authservice.md#queryIdentities)().

### \[signal\] void AuthService::mechanismsAvailable(const QString &*method*, const QStringList &*mechanisms*) {#mechanismsAvailable}

Emitted when the list of available `mechanisms` have been obtained from the service for the queried authentication `method`.

### \[signal\] void AuthService::methodsAvailable(const QStringList &*methods*) {#methodsAvailable}

Emitted when the list of available authentication methods have been obtained from the service; `methods` are their names.

### void AuthService::queryIdentities(const SignOn::AuthService::IdentityFilter &*filter* = IdentityFilter()) {#queryIdentities}

Requests information on identities which are stored. The list of identities retrieved from the service is emitted with signal [identities](signon-authservice.md#identities)(). Error is reported by emitting signal [error](signon-authservice.md#error)(). If `filter` is not valid, [Error::type](signon-error.md#type)() is [Error::InvalidQuery](signon-error.md#ErrorType-enum). If the application does not have keychain-access credential, [Error::type](signon-error.md#type)() is [Error::PermissionDenied](signon-error.md#ErrorType-enum).

`filter` shows only identities specified in filter - filtering not implemented for the moment. If the default parameter is passed, all the identities are returned.

Needs the keychain-access credential: only a key-chain application can access the list of identities.

*See also* [identities](signon-authservice.md#identities)(), [error](signon-authservice.md#error)()

### void AuthService::queryMechanisms(const QString &*method*) {#queryMechanisms}

Requests the information on mechanisms which are available for the authentication `method`. The list of mechanisms retrieved from the service is emitted with signal [mechanismsAvailable](signon-authservice.md#mechanismsAvailable)(). Error is reported by emitting signal [error](signon-authservice.md#error)(). If `method` is not a valid method, [Error::type](signon-error.md#type)() is [Error::MethodNotKnown](signon-error.md#ErrorType-enum).

*See also* [mechanismsAvailable](signon-authservice.md#mechanismsAvailable)(), [error](signon-authservice.md#error)()

### void AuthService::queryMethods() {#queryMethods}

Requests the information on available authentication methods. The list of service types retrieved is emitted with signal [methodsAvailable](signon-authservice.md#methodsAvailable)(). Error is reported by emitting signal [error](signon-authservice.md#error)().

*See also* [methodsAvailable](signon-authservice.md#methodsAvailable)(), [error](signon-authservice.md#error)()
