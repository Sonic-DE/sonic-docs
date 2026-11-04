---
title: "SignOn::IdentityInfo Class"
description: "Contains identity information."
---

# SignOn::IdentityInfo Class

Contains identity information. [More...](#details)

- **Header:** `#include <SignOn/IdentityInfo>`
- **CMake:** `find_package(SignOnQt6 REQUIRED)`  
  `target_link_libraries(mytarget PRIVATE SignOnQt6::SignOnQt6)`

[List of all members, including inherited members](signon-identityinfo-members.md)

## Public Types

- [enum IdentityInfo::CredentialsType](#CredentialsType-enum)

## Public Functions

- [IdentityInfo()](#IdentityInfo)
- [IdentityInfo(const QString &caption, const QString &userName, const QMap\<SignOn::MethodName, SignOn::MechanismsList\> &methods)](#IdentityInfo-2)
- [IdentityInfo(const SignOn::IdentityInfo &other)](#IdentityInfo-1)
- [~IdentityInfo()](#dtor.IdentityInfo)
- [QStringList accessControlList() const](#accessControlList)
- [SignOn::SecurityContextList accessControlListFull() const](#accessControlListFull)
- [const QString caption() const](#caption)
- [quint32 id() const](#id)
- [bool isStoringSecret() const](#isStoringSecret)
- [SignOn::MechanismsList mechanisms(const SignOn::MethodName &method) const](#mechanisms)
- [QList\<SignOn::MethodName\> methods() const](#methods)
- [QString owner() const](#owner)
- [QStringList realms() const](#realms)
- [qint32 refCount() const](#refCount)
- [void removeMethod(const SignOn::MethodName &method)](#removeMethod)
- [QString secret() const](#secret)
- [void setAccessControlList(const QStringList &accessControlList)](#setAccessControlList)
- [void setAccessControlList(const SignOn::SecurityContextList &accessControlList)](#setAccessControlList-1)
- [void setCaption(const QString &caption)](#setCaption)
- [void setId(const quint32 id)](#setId)
- [void setMethod(const SignOn::MethodName &method, const SignOn::MechanismsList &mechanismsList)](#setMethod)
- [void setOwner(const QString &ownerToken)](#setOwner)
- [void setRealms(const QStringList &realms)](#setRealms)
- [void setRefCount(qint32 refCount)](#setRefCount)
- [void setSecret(const QString &secret, const bool storeSecret = true)](#setSecret)
- [void setStoreSecret(const bool storeSecret)](#setStoreSecret)
- [void setType(SignOn::IdentityInfo::CredentialsType type)](#setType)
- [void setUserName(const QString &userName)](#setUserName)
- [SignOn::IdentityInfo::CredentialsType type() const](#type)
- [const QString userName() const](#userName)
- [SignOn::IdentityInfo &IdentityInfo::operator=(const SignOn::IdentityInfo &other)](#operator-eq)

## Detailed Description {#details}

This information is stored into database.

*See also* [AuthService::queryIdentities](signon-authservice.md#queryIdentities)()

## Member Type Documentation {#member-type-documentation}

### enum IdentityInfo::CredentialsType {#CredentialsType-enum}

Values used to describe the type of the identity

> **Note:** Mixed types, i.e Application\|Web are not yet supported. Just single types work for the time being.

| Constant | Value | Description |
| --- | --- | --- |
| `SignOn::IdentityInfo::Other` | `0` | Any other use. |
| `SignOn::IdentityInfo::Application` | `1 << 0` | An application. |
| `SignOn::IdentityInfo::Web` | `1 << 1` | A web site. |
| `SignOn::IdentityInfo::Network` | `1 << 2` | A network service. |

## Member Function Documentation {#member-function-documentation}

### IdentityInfo::IdentityInfo() {#IdentityInfo}

Creates a new empty [IdentityInfo](signon-identityinfo.md) object.

### IdentityInfo::IdentityInfo(const QString &*caption*, const QString &*userName*, const QMap\<SignOn::MethodName, SignOn::MechanismsList\> &*methods*) {#IdentityInfo-2}

Creates a new [IdentityInfo](signon-identityinfo.md) object with the description `caption` of the identity, the username `userName` and the `methods` allowed for the identity.

### IdentityInfo::IdentityInfo(const SignOn::IdentityInfo &*other*) {#IdentityInfo-1}

Copy constructor, copying `other`.

### \[noexcept\] IdentityInfo::~IdentityInfo() {#dtor.IdentityInfo}

Destructor

### QStringList IdentityInfo::accessControlList() const {#accessControlList}

Gets the list of access control system tokens defining the applications that are able to access this specific set of credentials.

> **Note:** This is accessible only to the owner application.

Returns the access control system tokens which defines the applications allowed to access this set of credentials.

*See also* [setAccessControlList](signon-identityinfo.md#setAccessControlList)()

### SignOn::SecurityContextList IdentityInfo::accessControlListFull() const {#accessControlListFull}

Gets the list of access control application tokens defining the applications that are able to access this specific set of credentials.

> **Note:** This is accessible only to the owner application.

Returns the access control tokens which defines the applications allowed to access this set of credentials.

### const QString IdentityInfo::caption() const {#caption}

Returns a human-readable representation of the identity.

*See also* [setCaption](signon-identityinfo.md#setCaption)()

### quint32 IdentityInfo::id() const {#id}

\* Returns the identity identifier.

*See also* [setId](signon-identityinfo.md#setId)()

### bool IdentityInfo::isStoringSecret() const {#isStoringSecret}

Returns whether the secret is being stored or not.

### SignOn::MechanismsList IdentityInfo::mechanisms(const SignOn::MethodName &*method*) const {#mechanisms}

Lists all the mechanisms for `method` in identity info.

### QList\<SignOn::MethodName\> IdentityInfo::methods() const {#methods}

Lists all methods in identity info.

### QString IdentityInfo::owner() const {#owner}

Gets the owner application token that is defining the applications that are able to modify this specific set of credentials.

> **Note:** This is accessible only to the owner application.

Returns the access control token which defines the applications allowed to modify this set of credentials.

*See also* [setOwner](signon-identityinfo.md#setOwner)()

### QStringList IdentityInfo::realms() const {#realms}

Gets the realms, e.g. URL's with which the Identity using this [IdentityInfo](signon-identityinfo.md) works with.

Returns the list of supported realms.

*See also* [setRealms](signon-identityinfo.md#setRealms)()

### qint32 IdentityInfo::refCount() const {#refCount}

Retrieves the refcount from identity info.

*See also* [setRefCount](signon-identityinfo.md#setRefCount)()

### void IdentityInfo::removeMethod(const SignOn::MethodName &*method*) {#removeMethod}

Removes the `method` from identity info.

### QString IdentityInfo::secret() const {#secret}

Gets the secret. If this object was retrieved from the database, the returned secret might be an empty string.

Returns the secret, when allowed, or an empty string.

*See also* [setSecret](signon-identityinfo.md#setSecret)()

### void IdentityInfo::setAccessControlList(const QStringList &*accessControlList*) {#setAccessControlList}

Sets the list of access control system tokens `accessControlList`, therefore defining the applications that will be able to access this specific set of credentials.

*See also* [accessControlList](signon-identityinfo.md#accessControlList)()

### void IdentityInfo::setAccessControlList(const SignOn::SecurityContextList &*accessControlList*) {#setAccessControlList-1}

Sets the list of access control tokens `accessControlList`, therefore defining the applications that will be able to access this specific set of credentials.

This is an overloaded function.

### void IdentityInfo::setCaption(const QString &*caption*) {#setCaption}

Sets a human readable `caption` of the identity

*See also* [caption](signon-identityinfo.md#caption)()

### void IdentityInfo::setId(const quint32 *id*) {#setId}

Sets the numeric identifier for the credentials record to `id`. Calling this method makes only sense when handling the [Identity::credentialsStored](signon-identity.md#credentialsStored)() signal.

*See also* [id](signon-identityinfo.md#id)()

### void IdentityInfo::setMethod(const SignOn::MethodName &*method*, const SignOn::MechanismsList &*mechanismsList*) {#setMethod}

Sets the `method` into identity info, with the list of mechanisms that are allowed, `mechanismsList`. If the given method is not included, a new one will be added. If it is already set, the mechanism list associated to it is updated. An empty list will clear the mechanisms. These values are used to limit Identity to use the specified methods and mechanisms.

### void IdentityInfo::setOwner(const QString &*ownerToken*) {#setOwner}

Sets the application token `ownerToken` that owns identity, therefore defining the applications that will be able to modify this specific set of credentials

*See also* [owner](signon-identityinfo.md#owner)()

### void IdentityInfo::setRealms(const QStringList &*realms*) {#setRealms}

Sets the `realms`, e.g. URL's with which the Identity using this [IdentityInfo](signon-identityinfo.md) shall work with.

*See also* [realms](signon-identityinfo.md#realms)()

### void IdentityInfo::setRefCount(qint32 *refCount*) {#setRefCount}

Sets the refcount into identity info to `refCount`. The type is used to generically identify where this identity is being used.

> **Note:** Server can restrict changes to differ +-1 from previous.

*See also* [refCount](signon-identityinfo.md#refCount)()

### void IdentityInfo::setSecret(const QString &*secret*, const bool *storeSecret* = true) {#setSecret}

Sets the `secret`. When performing a challenge on the owner Identity object, if the secret is set on its corresponding [IdentityInfo](signon-identityinfo.md), it will be added to the parameter list that is passed to the corresponding authentication plugin challenge implementation. By default a newly created [IdentityInfo](signon-identityinfo.md) does not contain a secret and has a policy of not storing any. If the secret is set the default policy will be to store it. This behaviour can also be set with [IdentityInfo::setStoreSecret](signon-identityinfo.md#setStoreSecret)().

`storeSecret` tells whether the secret is stored or not.

*See also* [secret](signon-identityinfo.md#secret)()

### void IdentityInfo::setStoreSecret(const bool *storeSecret*) {#setStoreSecret}

Sets whether the secret must be stored in the DB to `storeSecret`.

### void IdentityInfo::setType(SignOn::IdentityInfo::CredentialsType *type*) {#setType}

Sets the `type` into identity info. The type is used to generically identify where this identity is being used.

> **Note:** If this method is not called, the [IdentityInfo](signon-identityinfo.md) type will default to SignOn::OtherIdentity.

*See also* [type](signon-identityinfo.md#type)()

### void IdentityInfo::setUserName(const QString &*userName*) {#setUserName}

Sets the username to `userName`.

*See also* [userName](signon-identityinfo.md#userName)()

### SignOn::IdentityInfo::CredentialsType IdentityInfo::type() const {#type}

Retrieves the identity type from identity info.

*See also* [setType](signon-identityinfo.md#setType)()

### const QString IdentityInfo::userName() const {#userName}

Returns the username for the identity.

*See also* [setUserName](signon-identityinfo.md#setUserName)()

### SignOn::IdentityInfo &IdentityInfo::operator=(const SignOn::IdentityInfo &*other*) {#operator-eq}

Assignment operator, assigning `other`.

## Related Non-Members {#related-non-members}

### MechanismsList {#MechanismsList-typedef}

Defines a string list as a list of mechanisms.

### MethodName {#MethodName-typedef}

Defines a string as an authentication method.

### SecurityContextList {#SecurityContextList-typedef}

Defines a list of security contexts.
