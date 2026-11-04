---
title: "SignOn Namespace"
description: "The interface of signond extensions."
---

# SignOn Namespace

The interface of signond extensions.

## Classes {#classes}

### class [AbstractAccessControlManager](signon-abstractaccesscontrolmanager.md)

Helps filtering incoming Signon Daemon requests, based on security privileges of the client processes.

### class [AbstractCryptoManager](signon-abstractcryptomanager.md)

Manages the credentials storage file system encryption.

### class [AbstractKeyAuthorizer](signon-abstractkeyauthorizer.md)

Object holding the keys to the secure storage.

### class [AbstractKeyManager](signon-abstractkeymanager.md)

Base class for KeyManager implementations.

### class [AbstractSecretsStorage](signon-abstractsecretsstorage.md)

Interface for secrets storage implementations.

### class [AccessReply](signon-accessreply.md)

The asynchronous reply to an [AccessRequest](signon-accessrequest.md).

### class [AccessRequest](signon-accessrequest.md)

A client's request to access an identity.

### class [CredentialsDBError](signon-credentialsdberror.md)

An error of the secrets storage.

### class [ExtensionInterface2](signon-extensioninterface2.md)

Interface definition for signond extensions, version 2.

### class [ExtensionInterface3](signon-extensioninterface3.md)

Interface definition for signond extensions, version 3.

### class [ExtensionInterface](signon-extensioninterface.md)

Interface definition for signond extensions.

### class [KeyHandler](signon-keyhandler.md)

Object holding the keys to the secure storage.

## Type Documentation {#type-documentation}

### Key {#Key-typedef}

A key to the secure storage.

### KeyManagersList {#KeyManagersList-typedef}

A list of key managers.
