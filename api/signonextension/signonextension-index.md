---
title: "SignOn Extension Development"
description: "The interface of signond extensions."
---

# SignOn Extension Development

The interface of signond extensions.

signond loads extensions that replace parts of its behavior: how secrets are stored and encrypted, which keys unlock the storage, and which applications may access which credentials.

- [SignOn::ExtensionInterface](signon-extensioninterface.md) (and its newer versions): what an extension provides.
- [SignOn::AbstractSecretsStorage](signon-abstractsecretsstorage.md), [SignOn::AbstractCryptoManager](signon-abstractcryptomanager.md), [SignOn::AbstractKeyManager](signon-abstractkeymanager.md), [SignOn::AbstractKeyAuthorizer](signon-abstractkeyauthorizer.md) and [SignOn::AbstractAccessControlManager](signon-abstractaccesscontrolmanager.md): the parts an extension can replace.

## Using the Module {#using-the-module}

The library ships with a pkg-config file, `SignOnExtension.pc`; its `plugindir` variable is where signond loads extensions from.

## API Reference {#api-reference}

- [SignOn Extension C++ Classes](signonextension-module.md)
