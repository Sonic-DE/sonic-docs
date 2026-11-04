---
title: "SignOn::AbstractKeyManager Class"
description: "Base class for KeyManager implementations."
---

# SignOn::AbstractKeyManager Class

Base class for KeyManager implementations. [More...](#details)

- **Header:** `#include <SignOn/AbstractKeyManager>`
- **Inherits:** [QObject](https://doc.qt.io/qt-6/qobject.html)

[List of all members, including inherited members](signon-abstractkeymanager-members.md)  
[Deprecated members](signon-abstractkeymanager-obsolete.md)

## Public Functions

- [AbstractKeyManager(QObject \*parent = 0)](#AbstractKeyManager)
- [~AbstractKeyManager()](#dtor.AbstractKeyManager)
- [QString describeKey(const SignOn::Key &key)](#describeKey)
- [void queryKeys()](#queryKeys)
- [void setup()](#setup)

## Signals

- [void keyDisabled(const SignOn::Key key)](#keyDisabled)
- [void keyInserted(const SignOn::Key key)](#keyInserted)
- [void keyRemoved(const SignOn::Key key)](#keyRemoved)

## Detailed Description {#details}

The [AbstractKeyManager](signon-abstractkeymanager.md) is the base class for implementing signond key managers. A key manager is an object which signond uses to get the keys needed to access the encrypted storage. It emits signals whenever new keys exist, when keys are disabled or removed. For example, a simple password based key manager would:

- query the user for the password when [queryKeys](signon-abstractkeymanager.md#queryKeys)() is called.
- emit [keyInserted](signon-abstractkeymanager.md#keyInserted)() whenever the user enters the password.
- if the password automatically expires after some time, emit [keyDisabled](signon-abstractkeymanager.md#keyDisabled)()
- if the user changes the password, emit [keyInserted](signon-abstractkeymanager.md#keyInserted)() with the new password, and [keyRemoved](signon-abstractkeymanager.md#keyRemoved)() for the old one.

## Member Function Documentation {#member-function-documentation}

### \[explicit\] AbstractKeyManager::AbstractKeyManager(QObject \**parent* = 0) {#AbstractKeyManager}

Constructor, with the given `parent`.

### \[virtual noexcept\] AbstractKeyManager::~AbstractKeyManager() {#dtor.AbstractKeyManager}

Destructor

### \[virtual\] QString AbstractKeyManager::describeKey(const SignOn::Key &*key*) {#describeKey}

Gets a description for `key`.

Returns a description or name that could be shown to the user to identify the key

### \[signal\] void AbstractKeyManager::keyDisabled(const SignOn::Key *key*) {#keyDisabled}

Emitted when `key` is disabled. For instance, this signal can be emitted when a password expires or when a hardware key is removed.

### \[signal\] void AbstractKeyManager::keyInserted(const SignOn::Key *key*) {#keyInserted}

Emitted when the new `key` is available. If the key is not yet known to signond, signond will call authorizeKey on the key managers before accepting it.

### \[signal\] void AbstractKeyManager::keyRemoved(const SignOn::Key *key*) {#keyRemoved}

Emitted when `key` is to be removed. This means that the key will never be used again to access the secure storage; if it will be inserted again, it will have to be re-authenticated. It is not necessary to emit [keyDisabled](signon-abstractkeymanager.md#keyDisabled)() before keyRemoved(): the key will be disabled anyway when keyRemoved is emitted.

### \[virtual\] void AbstractKeyManager::queryKeys() {#queryKeys}

Signond calls this method when there are no active keys. This might happen when signond is just starting, or when all existing keys have been disabled (which would cause the secure storage to be unmounted). The key manager *must* emit [keyInserted](signon-abstractkeymanager.md#keyInserted)() in response to this call, either with a valid key or with an empty one.

### \[pure virtual\] void AbstractKeyManager::setup() {#setup}

This method initializes the key manager. Implementations can start emitting signals during this method's execution.

## Related Non-Members {#related-non-members}

### Key {#Key-typedef}

A key to the secure storage.
