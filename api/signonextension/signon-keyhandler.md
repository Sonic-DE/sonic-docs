---
title: "SignOn::KeyHandler Class"
description: "Object holding the keys to the secure storage."
---

# SignOn::KeyHandler Class

Object holding the keys to the secure storage. [More...](#details)

- **Header:** `#include <SignOn/KeyHandler>`
- **Inherits:** [QObject](https://doc.qt.io/qt-6/qobject.html)

[List of all members, including inherited members](signon-keyhandler-members.md)

## Public Types

- [enum KeyHandler::Authorizations](#Authorizations-enum)

## Public Functions

- [KeyHandler(QObject \*parent = 0)](#KeyHandler)
- [~KeyHandler()](#dtor.KeyHandler)
- [bool authorizeKey(const SignOn::Key &key, SignOn::KeyHandler::AuthorizeFlags flags = None)](#authorizeKey)
- [bool canAddKeyAuthorization() const](#canAddKeyAuthorization)
- [SignOn::AbstractCryptoManager \*cryptoManager() const](#cryptoManager)
- [void initialize(SignOn::AbstractCryptoManager \*cryptoManager, const SignOn::KeyManagersList &keyManagers)](#initialize)
- [QSet\<SignOn::Key\> insertedKeys() const](#insertedKeys)
- [bool isReady() const](#isReady)
- [bool keyIsAuthorized(const SignOn::Key &key) const](#keyIsAuthorized)
- [bool revokeKeyAuthorization(const SignOn::Key &key)](#revokeKeyAuthorization)

## Signals

- [void keyAuthorizationRevoked(const SignOn::Key key)](#keyAuthorizationRevoked)
- [void keyAuthorized(const SignOn::Key key)](#keyAuthorized)
- [void keyDisabled(const SignOn::Key key)](#keyDisabled)
- [void keyInserted(const SignOn::Key key)](#keyInserted)
- [void keyRemoved(const SignOn::Key key)](#keyRemoved)
- [void lastAuthorizedKeyRemoved(const SignOn::Key key)](#lastAuthorizedKeyRemoved)
- [void ready()](#ready)

## Detailed Description {#details}

The [KeyHandler](signon-keyhandler.md) is where all keys to the secure storage are held. It provides signals to notify when keys are inserted, authorized, removed, disabled, as well as methods to authorize and unauthorize keys.

## Member Type Documentation {#member-type-documentation}

### enum KeyHandler::Authorizations {#Authorizations-enum}

**flags KeyHandler::AuthorizeFlags**

Options for [authorizeKey](signon-keyhandler.md#authorizeKey)().

| Constant | Value | Description |
| --- | --- | --- |
| `SignOn::KeyHandler::None` | `0` | No options. |
| `SignOn::KeyHandler::FormatStorage` | `1 << 0` | Formats the secure storage |

The `AuthorizeFlags` type is a typedef for `QFlags<Authorizations>. `It stores an OR combination of `Authorizations` values.

## Member Function Documentation {#member-function-documentation}

### \[explicit\] KeyHandler::KeyHandler(QObject \**parent* = 0) {#KeyHandler}

Constructor, with the given `parent`.

### \[virtual noexcept\] KeyHandler::~KeyHandler() {#dtor.KeyHandler}

Destructor

### bool KeyHandler::authorizeKey(const SignOn::Key &*key*, SignOn::KeyHandler::AuthorizeFlags *flags* = None) {#authorizeKey}

Add `key` to the list of keys which can be used to access the secure storage, with the options `flags`. If the [KeyHandler](signon-keyhandler.md) is empty, this method will fail.

Returns true if the operation was successful.

*See also* [keyAuthorized](signon-keyhandler.md#keyAuthorized)()

### bool KeyHandler::canAddKeyAuthorization() const {#canAddKeyAuthorization}

Returns true if a new key can be authorized by calling [authorizeKey](signon-keyhandler.md#authorizeKey)() without specifying the [FormatStorage](signon-keyhandler.md#Authorizations-enum) flag (that is, if the [KeyHandler](signon-keyhandler.md) knows other keys which can open the storage).

### SignOn::AbstractCryptoManager \*KeyHandler::cryptoManager() const {#cryptoManager}

Returns the CryptoManager.

### void KeyHandler::initialize(SignOn::AbstractCryptoManager \**cryptoManager*, const SignOn::KeyManagersList &*keyManagers*) {#initialize}

This method initializes the key managers `keyManagers`, with the `cryptoManager`.

### QSet\<SignOn::Key\> KeyHandler::insertedKeys() const {#insertedKeys}

Returns the currently inserted keys.

### bool KeyHandler::isReady() const {#isReady}

True if all key managers have been initialized and have started reporting their inserted keys.

### \[signal\] void KeyHandler::keyAuthorizationRevoked(const SignOn::Key *key*) {#keyAuthorizationRevoked}

Emitted when the authorization of `key` has been revoked.

### \[signal\] void KeyHandler::keyAuthorized(const SignOn::Key *key*) {#keyAuthorized}

Emitted when `key` has been authorized.

### \[signal\] void KeyHandler::keyDisabled(const SignOn::Key *key*) {#keyDisabled}

Emitted when `key` is disabled. For instance, this signal can be emitted when a password expires or when a hardware key is removed. This signal will be emitted before the action is processed by the [KeyHandler](signon-keyhandler.md); this means that if for instance `key` was an authorized key, calling [keyIsAuthorized](signon-keyhandler.md#keyIsAuthorized)() from this signal's handler will still return true.

### \[signal\] void KeyHandler::keyInserted(const SignOn::Key *key*) {#keyInserted}

Emitted when the new `key` is available. If the key is not yet known to signond, signond will call [authorizeKey](signon-keyhandler.md#authorizeKey) on the key managers before accepting it.

### bool KeyHandler::keyIsAuthorized(const SignOn::Key &*key*) const {#keyIsAuthorized}

Returns true if `key` is an authorized key.

### \[signal\] void KeyHandler::keyRemoved(const SignOn::Key *key*) {#keyRemoved}

One of the key managers has asked that `key` be removed. This means that the key manager will never provide the same key again, so its authorization to open the secure storage can be revoked. The [keyDisabled](signon-keyhandler.md#keyDisabled)() signal will always be emitted prior to this one.

### \[signal\] void KeyHandler::lastAuthorizedKeyRemoved(const SignOn::Key *key*) {#lastAuthorizedKeyRemoved}

Emitted when the last authorized key, `key`, has been removed.

### \[signal\] void KeyHandler::ready() {#ready}

Emitted after all key managers have been initialized and have reported about their inserted keys.

### bool KeyHandler::revokeKeyAuthorization(const SignOn::Key &*key*) {#revokeKeyAuthorization}

Remove `key` from the list of keys which can be used to access the secure storage. If the [KeyHandler](signon-keyhandler.md) is empty, this method will fail.

Returns true if the operation was successful.

*See also* [keyAuthorizationRevoked](signon-keyhandler.md#keyAuthorizationRevoked)()

## Related Non-Members {#related-non-members}

### KeyManagersList {#KeyManagersList-typedef}

A list of key managers.
