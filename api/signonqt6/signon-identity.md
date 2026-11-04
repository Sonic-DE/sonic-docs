---
title: "SignOn::Identity Class"
description: "Represents a database entry for a single identity."
---

# SignOn::Identity Class

Represents a database entry for a single identity. [More...](#details)

- **Header:** `#include <SignOn/Identity>`
- **CMake:** `find_package(SignOnQt6 REQUIRED)`  
  `target_link_libraries(mytarget PRIVATE SignOnQt6::SignOnQt6)`
- **Inherits:** [QObject](https://doc.qt.io/qt-6/qobject.html)

[List of all members, including inherited members](signon-identity-members.md)  
[Deprecated members](signon-identity-obsolete.md)

## Public Functions

- [~Identity()](#dtor.Identity)
- [void addReference(const QString &reference = QString())](#addReference)
- [SignOn::AuthSessionP createSession(const QString &methodName)](#createSession)
- [void destroySession(const SignOn::AuthSessionP &session)](#destroySession)
- [quint32 id() const](#id)
- [void queryAvailableMethods()](#queryAvailableMethods)
- [void queryInfo()](#queryInfo)
- [void remove()](#remove)
- [void removeReference(const QString &reference = QString())](#removeReference)
- [void requestCredentialsUpdate(const QString &message = QString())](#requestCredentialsUpdate)
- [void signOut()](#signOut)
- [void storeCredentials(const SignOn::IdentityInfo &info = IdentityInfo())](#storeCredentials)
- [void verifySecret(const QString &secret)](#verifySecret)
- [void verifyUser(const QString &message = QString())](#verifyUser)
- [void verifyUser(const QVariantMap &params)](#verifyUser-1)

## Signals

- [void credentialsStored(const quint32 id)](#credentialsStored)
- [void error(const SignOn::Error &err)](#error)
- [void info(const SignOn::IdentityInfo &info)](#info)
- [void methodsAvailable(const QStringList &methods)](#methodsAvailable)
- [void referenceAdded()](#referenceAdded)
- [void referenceRemoved()](#referenceRemoved)
- [void removed()](#removed)
- [void secretVerified(const bool valid)](#secretVerified)
- [void signedOut()](#signedOut)
- [void userVerified(const bool valid)](#userVerified)

## Static Public Members

- [SignOn::Identity \*existingIdentity(const quint32 id, QObject \*parent = 0)](#existingIdentity)
- [SignOn::Identity \*newIdentity(const SignOn::IdentityInfo &info = IdentityInfo(), QObject \*parent = 0)](#newIdentity)

## Detailed Description {#details}

Identity is a client side presentation of a credential.

## Member Function Documentation {#member-function-documentation}

### \[virtual noexcept\] Identity::~Identity() {#dtor.Identity}

Destructor

### void Identity::addReference(const QString &*reference* = QString()) {#addReference}

Adds the named `reference` to identity into the database. On success, a signal [referenceAdded](signon-identity.md#referenceAdded)() is emitted If the operation fails, a signal [error](signon-identity.md#error)() is emitted. If referencing fails, [Error::type](signon-error.md#type)() is [Error::StoreFailed](signon-error.md#ErrorType-enum),

Untrusted clients may be blocked from performing this operation, subject to the security framework restrictions.

*See also* [referenceAdded](signon-identity.md#referenceAdded)(), [error](signon-identity.md#error)()

### SignOn::AuthSessionP Identity::createSession(const QString &*methodName*) {#createSession}

Creates a new session for authentication with the authentication method `methodName`. This creates a connection to authentication plugin. The Identity object is parent and owner of all created authentication sessions.

Returns the new authentication session, or NULL if not able to create it.

### \[signal\] void Identity::credentialsStored(const quint32 *id*) {#credentialsStored}

Emitted when credentials passed by [storeCredentials](signon-identity.md#storeCredentials)() method have been successfully stored on the service; `id` identifies the stored credentials.

### void Identity::destroySession(const SignOn::AuthSessionP &*session*) {#destroySession}

Destroys the authentication `session`.

### \[signal\] void Identity::error(const SignOn::Error &*err*) {#error}

Emitted when an error occurs while performing an operation; `err` is the error. Typical error types are generic errors, where [Error::type](signon-error.md#type)() \< [Error::AuthServiceErr](signon-error.md#ErrorType-enum) and Identity specific, where [Error::IdentityErr](signon-error.md#ErrorType-enum) \< [Error::type](signon-error.md#type)() \< [Error::AuthServiceErr](signon-error.md#ErrorType-enum)

*See also* [SignOn::Error](signon-error.md), [SignOn::Error::ErrorType](signon-error.md#ErrorType-enum)

### \[static\] SignOn::Identity \*Identity::existingIdentity(const quint32 *id*, QObject \**parent* = 0) {#existingIdentity}

Constructs an identity object associated with the existing identity record `id` on the service, with the given `parent`.

Returns a pointer to the identity object, or NULL if it fails to create it: it can return NULL if the client is untrusted.

### quint32 Identity::id() const {#id}

Returns the unique ID of the identity. For a new identity which is not stored, NEW\_IDENTITY is returned.

### \[signal\] void Identity::info(const SignOn::IdentityInfo &*info*) {#info}

Emitted with the credentials `info` stored on the service, in reply to [queryInfo](signon-identity.md#queryInfo)().

### \[signal\] void Identity::methodsAvailable(const QStringList &*methods*) {#methodsAvailable}

Emitted when the list of available `methods` has been obtained for identity.

### \[static\] SignOn::Identity \*Identity::newIdentity(const SignOn::IdentityInfo &*info* = IdentityInfo(), QObject \**parent* = 0) {#newIdentity}

Constructs a new identity object with the identity information `info` and the given `parent`.

Returns a pointer to the new identity object, or NULL if it fails to create it: it can return NULL if the client is untrusted.

### void Identity::queryAvailableMethods() {#queryAvailableMethods}

Query list of available authentication methods for given identity. List is returned by emitting signal [methodsAvailable](signon-identity.md#methodsAvailable)(). If the operation fails, a signal [error](signon-identity.md#error)() is emitted. If identity is not stored, [Error::type](signon-error.md#type)() is [Error::CredentialsNotAvailable](signon-error.md#ErrorType-enum), or [Error::IdentityNotFound](signon-error.md#ErrorType-enum).

*See also* [methodsAvailable](signon-identity.md#methodsAvailable)(), [error](signon-identity.md#error)()

### void Identity::queryInfo() {#queryInfo}

Query stored credential parameters for this authentication identity. On success, a signal [info](signon-identity.md#info)() is emitted with parameters in the service. If the operation fails, a signal [error](signon-identity.md#error)() is emitted. If query fails, [Error::type](signon-error.md#type)() is [Error::CredentialsNotAvailable](signon-error.md#ErrorType-enum),

Untrusted clients may be blocked from performing this operation, subject to the security framework restrictions.

*See also* [info](signon-identity.md#info)(), [error](signon-identity.md#error)()

### \[signal\] void Identity::referenceAdded() {#referenceAdded}

Emitted when references are added by [addReference](signon-identity.md#addReference)() method and change has been successfully stored on the service.

### \[signal\] void Identity::referenceRemoved() {#referenceRemoved}

Emitted when references are removed by [removeReference](signon-identity.md#removeReference)() method and change has been successfully stored on the service.

### void Identity::remove() {#remove}

Removes this identity from database. On success, a signal [removed](signon-identity.md#removed)() is emitted If the operation fails, a signal [error](signon-identity.md#error)() is emitted. If removing fails, [Error::type](signon-error.md#type)() is [Error::RemoveFailed](signon-error.md#ErrorType-enum),

Untrusted clients may be blocked from performing this operation, subject to the security framework restrictions.

*See also* [removed](signon-identity.md#removed)(), [error](signon-identity.md#error)()

### void Identity::removeReference(const QString &*reference* = QString()) {#removeReference}

Removes the named `reference` to identity from the database. On success, a signal [referenceRemoved](signon-identity.md#referenceRemoved)() is emitted If the operation fails, a signal [error](signon-identity.md#error)() is emitted. If dereferencing fails, [Error::type](signon-error.md#type)() is [Error::ReferenceNotFound](signon-error.md#ErrorType-enum),

Untrusted clients may be blocked from performing this operation, subject to the security framework restrictions.

*See also* [referenceRemoved](signon-identity.md#referenceRemoved)(), [error](signon-identity.md#error)()

### \[signal\] void Identity::removed() {#removed}

Emitted when the identity is removed.

### void Identity::requestCredentialsUpdate(const QString &*message* = QString()) {#requestCredentialsUpdate}

Requests the user to give a new secret into database, showing `message` to the user. Client can use requestCredentialsUpdate() to launch external dialog for asking new secret, that will be stored into database. On success, a signal [credentialsStored](signon-identity.md#credentialsStored)() is emitted. If the operation fails, a signal [error](signon-identity.md#error)() is emitted. If storing changes fails, [Error::type](signon-error.md#type)() is [Error::StoreFailed](signon-error.md#ErrorType-enum), If user cancels dialog, [Error::type](signon-error.md#type)() is [Error::IdentityOperationCanceled](signon-error.md#ErrorType-enum).

*See also* [credentialsStored](signon-identity.md#credentialsStored)(), [error](signon-identity.md#error)()

### \[signal\] void Identity::secretVerified(const bool *valid*) {#secretVerified}

Emitted when secret verification is completed; `valid` tells whether the given secret is the same as the stored one.

### void Identity::signOut() {#signOut}

\* Signs out Identity from all services. All authentication sessions using \* this Identity will be invalidated and all tokens cleared from cache. \* When sign out is completed, signal [signedOut](signon-identity.md#signedOut)() is emitted. \* If the operation fails, a signal [error](signon-identity.md#error)() is emitted. \* If signout fails, [Error::type](signon-error.md#type)() is \* [Error::SignOutFailed](signon-error.md#ErrorType-enum). \* \* All clients using same identity will receive [signedOut](signon-identity.md#signedOut) signal. \* \*

*See also* [signedOut](signon-identity.md#signedOut)(), [error](signon-identity.md#error)()

### \[signal\] void Identity::signedOut() {#signedOut}

Emitted when the identity is signed out.

### void Identity::storeCredentials(const SignOn::IdentityInfo &*info* = IdentityInfo()) {#storeCredentials}

Stores the credentials `info` for this authentication identity. [IdentityInfo](signon-identityinfo.md) contains restrictions on methods and mechanisms for given Identity. On success, a signal [credentialsStored](signon-identity.md#credentialsStored)() is emitted. If the operation fails, a signal [error](signon-identity.md#error)() is emitted. If storing changes fails, [Error::type](signon-error.md#type)() is [Error::StoreFailed](signon-error.md#ErrorType-enum),

Untrusted clients may be blocked from performing this operation, subject to the security framework restrictions.

If default value is used for the parameter the Identity object stores the internally stored information, e.g. the [IdentityInfo](signon-identityinfo.md) object used to create a new identity using [Identity::newIdentity](signon-identity.md#newIdentity)()

*See also* [credentialsStored](signon-identity.md#credentialsStored)(), [error](signon-identity.md#error)(), [IdentityInfo](signon-identityinfo.md)

### \[signal\] void Identity::userVerified(const bool *valid*) {#userVerified}

Emitted when the user verification is completed; `valid` tells whether the given secret is the same as the stored one.

### void Identity::verifySecret(const QString &*secret*) {#verifySecret}

Verifies if `secret` matches the stored secret. When verification is completed, a signal [secretVerified](signon-identity.md#secretVerified)() is emitted. If the operation fails, a signal [error](signon-identity.md#error)() is emitted. If the credentials are not stored, [Error::type](signon-error.md#type)() is [Error::CredentialsNotAvailable](signon-error.md#ErrorType-enum).

*See also* [secretVerified](signon-identity.md#secretVerified)(), [error](signon-identity.md#error)()

### void Identity::verifyUser(const QString &*message* = QString()) {#verifyUser}

Gets a secret verification from the user and compares it to the stored secret, showing `message` to the user. This launches an external dialog for asking secret. When verification is completed, signal [userVerified](signon-identity.md#userVerified)() is emitted. If the operation fails, a signal [error](signon-identity.md#error)() is emitted. If user selects "Forgot Password"-sequence, [Error::type](signon-error.md#type)() is [Error::ForgotPassword](signon-error.md#ErrorType-enum).

*See also* [userVerified](signon-identity.md#userVerified)(), [error](signon-identity.md#error)()

### void Identity::verifyUser(const QVariantMap &*params*) {#verifyUser-1}

Gets a secret verification from the user and compares it to the stored secret, with the dialog customization parameters `params`. This launches an external dialog for asking secret. When verification is completed, signal [userVerified](signon-identity.md#userVerified)() is emitted. If the operation fails, a signal [error](signon-identity.md#error)() is emitted. If user selects "Forgot Password"-sequence, [Error::type](signon-error.md#type)() is [Error::ForgotPassword](signon-error.md#ErrorType-enum).

This is an overloaded function.

*See also* [userVerified](signon-identity.md#userVerified)(), [error](signon-identity.md#error)()

## Related Non-Members {#related-non-members}

### AuthSessionP {#AuthSessionP-typedef}

A guarded pointer to an [AuthSession](signon-authsession.md).
