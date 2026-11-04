---
title: "SignOn::ExtensionInterface3 Class"
description: "Interface definition for signond extensions, version 3."
---

# SignOn::ExtensionInterface3 Class

Interface definition for signond extensions, version 3. [More...](#details)

- **Header:** `#include <SignOn/ExtensionInterface>`
- **Inherits:** [SignOn::ExtensionInterface2](signon-extensioninterface2.md)

[List of all members, including inherited members](signon-extensioninterface3-members.md)

## Public Functions

- [SignOn::AbstractAccessControlManager \*accessControlManager(QObject \*parent = 0) const](#accessControlManager)
- [SignOn::AbstractCryptoManager \*cryptoManager(QObject \*parent = 0) const](#cryptoManager)
- [SignOn::AbstractSecretsStorage \*secretsStorage(QObject \*parent = 0) const](#secretsStorage)

## Detailed Description {#details}

## Member Function Documentation {#member-function-documentation}

### \[virtual\] SignOn::AbstractAccessControlManager \*ExtensionInterface3::accessControlManager(QObject \**parent* = 0) const {#accessControlManager}

Gets the [AbstractAccessControlManager](signon-abstractaccesscontrolmanager.md) object, with the given `parent`, which will be used to check accesses to the credential database. This object is instantiated only if the value of the "AccessControlManager" setting in the signond configuration matches the plugin's [QObject::objectName](https://doc.qt.io/qt-6/qobject.html#objectName-prop)().

Returns an [AbstractAccessControlManager](signon-abstractaccesscontrolmanager.md) object, or 0 if none is provided by this plugin

### \[virtual\] SignOn::AbstractCryptoManager \*ExtensionInterface3::cryptoManager(QObject \**parent* = 0) const {#cryptoManager}

Gets the CryptoManager object, with the given `parent`, which will be used to setup the file system for the credentials storage. This object is instantiated only if the value of the "CryptoManager" setting in the signond configuration matches the plugin's [QObject::objectName](https://doc.qt.io/qt-6/qobject.html#objectName-prop)().

Returns a CryptoManager object, or 0 if none is provided by this plugin

### \[virtual\] SignOn::AbstractSecretsStorage \*ExtensionInterface3::secretsStorage(QObject \**parent* = 0) const {#secretsStorage}

Gets the SecretsStorage object, with the given `parent`, which is used to save and load the user's secrets, as well as authentication plugins' data. This object is instantiated only if the value of the "SecretsStorage" setting in the signond configuration matches the plugin's [QObject::objectName](https://doc.qt.io/qt-6/qobject.html#objectName-prop)().

Returns a SecretsStorage object, or 0 if none is provided by this plugin.
