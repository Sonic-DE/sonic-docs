---
title: "SignOn::SessionData Class"
description: "Data container to hold values for authentication session."
---

# SignOn::SessionData Class

Data container to hold values for authentication session. [More...](#details)

- **Header:** `#include <SignOn/SessionData>`
- **CMake:** `find_package(SignOnQt6 REQUIRED)`  
  `target_link_libraries(mytarget PRIVATE SignOnQt6::SignOnQt6)`

[List of all members, including inherited members](signon-sessiondata-members.md)

## Public Functions

- [SessionData(const QVariantMap &data = QVariantMap())](#SessionData)
- [SessionData(const SignOn::SessionData &other)](#SessionData-1)
- [template \<typename T\> T data() const](#data)
- [QStringList getAccessControlTokens() const](#getAccessControlTokens)
- [const QVariant getProperty(const QString &propertyName) const](#getProperty)
- [const QStringList propertyNames() const](#propertyNames)
- [void setCaption(const QString &value)](#setCaption)
- [QString Caption() const](#Caption)
- [void setNetworkProxy(const QString &value)](#setNetworkProxy)
- [QString NetworkProxy() const](#NetworkProxy)
- [void setNetworkTimeout(const quint32 &value)](#setNetworkTimeout)
- [quint32 NetworkTimeout() const](#NetworkTimeout)
- [void setRealm(const QString &value)](#setRealm)
- [QString Realm() const](#Realm)
- [void setRenewToken(const bool &value)](#setRenewToken)
- [bool RenewToken() const](#RenewToken)
- [void setSecret(const QString &value)](#setSecret)
- [QString Secret() const](#Secret)
- [void setUiPolicy(const int &value)](#setUiPolicy)
- [int UiPolicy() const](#UiPolicy)
- [void setUserName(const QString &value)](#setUserName)
- [QString UserName() const](#UserName)
- [void setWindowId(const quint32 &value)](#setWindowId)
- [quint32 WindowId() const](#WindowId)
- [QVariantMap toMap() const](#toMap)
- [SignOn::SessionData &SessionData::operator+=(const SignOn::SessionData &other)](#operator-2b-eq)
- [SignOn::SessionData &SessionData::operator=(const SignOn::SessionData &other)](#operator-eq)

## Detailed Description {#details}

Inherit this class if you want to extend the property range.

> **Warning:** All this class' definitions must be inline.

## Member Function Documentation {#member-function-documentation}

### SessionData::SessionData(const QVariantMap &*data* = QVariantMap()) {#SessionData}

Constructor. Creates a [SessionData](signon-sessiondata.md) containing `data`.

> **Note:** Internal use only recommended. As a SSO client application developer use setters/getters for specific [SessionData](signon-sessiondata.md) properties.

### SessionData::SessionData(const SignOn::SessionData &*other*) {#SessionData-1}

Copy constructor, copying `other` to this instance.

### template \<typename T\> T SessionData::data() const {#data}

Creates an instance of type T, which must be derived from [SessionData](signon-sessiondata.md). The instance will contain the data of this instance.

### QStringList SessionData::getAccessControlTokens() const {#getAccessControlTokens}

Gets the access control tokens that the requesting application has.

> **Note:** To be used by the plugins developers only.

### const QVariant SessionData::getProperty(const QString &*propertyName*) const {#getProperty}

Access the property `propertyName` of the [SessionData](signon-sessiondata.md). Returns the property's value, or an empty variant if the property does not exist at runtime.

### const QStringList SessionData::propertyNames() const {#propertyNames}

Access the list of runtime existing properties of the [SessionData](signon-sessiondata.md). Returns the property names.

### void SessionData::setCaption(const QString &*value*) {#setCaption}

### QString SessionData::Caption() const {#Caption}

The property Caption. Caption is to tell user which application/credentials/provider is requesting signon-ui.

> **Note:** Caption is taken from database if not defined by application or authentication plugin.

### void SessionData::setNetworkProxy(const QString &*value*) {#setNetworkProxy}

### QString SessionData::NetworkProxy() const {#NetworkProxy}

The property [NetworkProxy](signon-sessiondata.md#NetworkProxy): the network proxy to be used instead of system default.

### void SessionData::setNetworkTimeout(const quint32 &*value*) {#setNetworkTimeout}

### quint32 SessionData::NetworkTimeout() const {#NetworkTimeout}

The property [NetworkTimeout](signon-sessiondata.md#NetworkTimeout): the timeout for network related operations in milliseconds. To be used when a remote service does not reply in a reasonable amount of time.

### void SessionData::setRealm(const QString &*value*) {#setRealm}

### QString SessionData::Realm() const {#Realm}

The property Realm: the realm that is used for authentication.

### void SessionData::setRenewToken(const bool &*value*) {#setRenewToken}

### bool SessionData::RenewToken() const {#RenewToken}

The property [RenewToken](signon-sessiondata.md#RenewToken). This is used by a signon plugin to check whether the access token has to be renewed. When this property is set, the signon plugin will remove the old set of access tokens and get a new set.

### void SessionData::setSecret(const QString &*value*) {#setSecret}

### QString SessionData::Secret() const {#Secret}

The property Secret: the secret.

### void SessionData::setUiPolicy(const int &*value*) {#setUiPolicy}

### int SessionData::UiPolicy() const {#UiPolicy}

The property [UiPolicy](signon-sessiondata.md#UiPolicy). Use [UiPolicy](signon-sessiondata.md#UiPolicy) to define how plugin interacts with the user.

*See also* [SignOn::SignonUiPolicy](signon-sessiondata.md#SignonUiPolicy-enum)

### void SessionData::setUserName(const QString &*value*) {#setUserName}

### QString SessionData::UserName() const {#UserName}

The property [UserName](signon-sessiondata.md#UserName): the username.

### void SessionData::setWindowId(const quint32 &*value*) {#setWindowId}

### quint32 SessionData::WindowId() const {#WindowId}

The property [WindowId](signon-sessiondata.md#WindowId). This is to be used for setting signon-ui dialog application modal.

### QVariantMap SessionData::toMap() const {#toMap}

Gets the [QVariantMap](https://doc.qt.io/qt-6/qvariant.html#QVariantMap-typedef) of session parameters.

### SignOn::SessionData &SessionData::operator+=(const SignOn::SessionData &*other*) {#operator-2b-eq}

Addition operator, adding `other` to this instance. Returns a reference to this object.

### SignOn::SessionData &SessionData::operator=(const SignOn::SessionData &*other*) {#operator-eq}

Assignment operator, assigning `other` to this instance. Returns a reference to this object.

## Related Non-Members {#related-non-members}

### enum SignonUiPolicy {#SignonUiPolicy-enum}

Policy to define how the plugin interacts with the user. This is a hint for plugin how to handle user interaction. NoUserInteractionPolicy does not allow any ui interaction to happen and plugin will get error reply QUERY\_ERROR\_FORBIDDEN.

| Constant | Value | Description |
| --- | --- | --- |
| `SignOn::SessionData::DefaultPolicy` | `0` | Plugin can decide when to show ui. |
| `SignOn::SessionData::RequestPasswordPolicy` | `1` | Force user to enter password. |
| `SignOn::SessionData::NoUserInteractionPolicy` | `2` | No ui elements are shown to user. |
| `SignOn::SessionData::ValidationPolicy` | `3` | UI elements can be shown to the user only when captcha-like security measures are required |

*See also* [SessionData::UiPolicy](signon-sessiondata.md#UiPolicy)()

## Macro Documentation {#macro-documentation}

### SIGNON\_SESSION\_DECLARE\_PROPERTY(*type\_*, *name\_*) {#SIGNON_SESSION_DECLARE_PROPERTY}

A macro to create declarations for parameter setter and getter: set`name_`() and `name_()`, for a property of type `type_`. This supports the same types as [QVariant](https://doc.qt.io/qt-6/qvariant.html). For user specified types see [QMetaType](https://doc.qt.io/qt-6/qmetatype.html).

### SSO\_ACCESS\_CONTROL\_TOKENS {#SSO_ACCESS_CONTROL_TOKENS}

Property which holds the access control tokens that the requesting application has.

> **Note:** To be used by the plugins developers only.
