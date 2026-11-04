---
title: "SignOn Extension C++ Classes"
description: "The interface of signond extensions."
---

# SignOn Extension C++ Classes

The interface of signond extensions. [More...](#details)

## Classes {#classes}

- [SignOn::AbstractAccessControlManager](signon-abstractaccesscontrolmanager.md): Helps filtering incoming Signon Daemon requests, based on security privileges of the client processes.
- [SignOn::AbstractCryptoManager](signon-abstractcryptomanager.md): Manages the credentials storage file system encryption.
- [SignOn::AbstractKeyAuthorizer](signon-abstractkeyauthorizer.md): Object holding the keys to the secure storage
- [SignOn::AbstractKeyManager](signon-abstractkeymanager.md): Base class for KeyManager implementations.
- [SignOn::AbstractSecretsStorage](signon-abstractsecretsstorage.md): Interface for secrets storage implementations.
- [SignOn::AccessReply](signon-accessreply.md): The asynchronous reply to an AccessRequest.
- [SignOn::AccessRequest](signon-accessrequest.md): A client's request to access an identity.
- [SignOn::CredentialsDBError](signon-credentialsdberror.md): An error of the secrets storage.
- [SignOn::ExtensionInterface](signon-extensioninterface.md): Interface definition for signond extensions.
- [SignOn::ExtensionInterface2](signon-extensioninterface2.md): Interface definition for signond extensions, version 2.
- [SignOn::ExtensionInterface3](signon-extensioninterface3.md): Interface definition for signond extensions, version 3.
- [SignOn::KeyHandler](signon-keyhandler.md): Object holding the keys to the secure storage

## Detailed Description {#details}
