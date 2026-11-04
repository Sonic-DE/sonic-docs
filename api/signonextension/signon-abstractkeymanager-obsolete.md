---
title: "Obsolete Members for SignOn::AbstractKeyManager"
description: "Deprecated members of SignOn::AbstractKeyManager."
parent: "signonextension/signon-abstractkeymanager"
---

# Obsolete Members for SignOn::AbstractKeyManager

**The following members of class [AbstractKeyManager](signon-abstractkeymanager.md) are deprecated.** We strongly advise against using them in new code.

## Public Functions

- [void authorizeKey(const SignOn::Key &key, const QString &message = QString())](#authorizeKey)
- [bool supportsKeyAuthorization() const](#supportsKeyAuthorization)

## Signals

- [void keyAuthorized(const SignOn::Key key, bool authorized)](#keyAuthorized)

## Obsolete Member Function Documentation {#obsolete-member-function-documentation}

### \[virtual, deprecated\] void AbstractKeyManager::authorizeKey(const SignOn::Key &*key*, const QString &*message* = QString()) {#authorizeKey}

This function is deprecated. We strongly advise against using it in new code.

Signond calls this method if a key (typically a new key emitted with the [keyInserted](signon-abstractkeymanager.md#keyInserted)() signal) needs to be authorized. Authorizing a key means allowing the key to be used to mount the secure storage. The base implementation of this method just emits the [keyAuthorized](signon-abstractkeymanager-obsolete.md#keyAuthorized)() signal denying the authorization, but specific implementations could delegate the authorization to the user.

`key` is the key that needs authorization, and `message` an optional message that might be shown to the user.

This method is deprecated and should not be used or implemented in subclasses.

### \[signal, deprecated\] void AbstractKeyManager::keyAuthorized(const SignOn::Key *key*, bool *authorized*) {#keyAuthorized}

This function is deprecated. We strongly advise against using it in new code.

The key manager emits this when it has decided whether to authorize `key`; `authorized` is the result. If more than one key manager is installed, signond will authorize the key as soon as the first key manager emits this signal with authorized set to true.

This signal is deprecated and should not be used or emitted in subclasses.

### \[virtual, deprecated\] bool AbstractKeyManager::supportsKeyAuthorization() const {#supportsKeyAuthorization}

This function is deprecated. We strongly advise against using it in new code.

Returns whether the extension is able to authorize keys or not. The default implementation just returns false.

This method is deprecated and should not be used or implemented in subclasses.
