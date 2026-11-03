---
title: "KSambaShare Class"
description: "This class lists Samba user shares and monitors them for addition, update and removal."
---

# KSambaShare Class

This class lists Samba user shares and monitors them for addition, update and removal. [More...](#details)

- **Header:** `#include <KSambaShare>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS KIO)`  
  `target_link_libraries(mytarget PRIVATE KF6::KIOCore)`
- **Inherits:** [QObject](https://doc.qt.io/qt-6/qobject.html)

[List of all members, including inherited members](ksambashare-members.md)

## Public Functions

- [bool areGuestsAllowed() const](#areGuestsAllowed)
- [KSambaShareData getShareByName(const QString &name) const](#getShareByName)
- [QList\<KSambaShareData\> getSharesByPath(const QString &path) const](#getSharesByPath)
- [bool isDirectoryShared(const QString &path) const](#isDirectoryShared)
- [bool isShareNameAvailable(const QString &name) const](#isShareNameAvailable)
- [QString lastSystemErrorString() const](#lastSystemErrorString)
- [QStringList shareNames() const](#shareNames)
- [QStringList sharedDirectories() const](#sharedDirectories)

## Signals

- [void changed()](#changed)

## Static Public Members

- [KSambaShare \*instance()](#instance)

## Detailed Description {#details}

Singleton class, call [instance](ksambashare.md#instance)() to get an instance.

## Member Function Documentation {#member-function-documentation}

### bool KSambaShare::areGuestsAllowed() const {#areGuestsAllowed}

Check whether usershares may enable guests. System-level configuration may disable usershare guests and prevent saving [KSambaShareData](ksambasharedata.md) with UserGuestPermission set.

Returns `true` when usershares may allow guest access

### \[signal\] void KSambaShare::changed() {#changed}

Emitted when a share is updated, added or removed

### KSambaShareData KSambaShare::getShareByName(const QString &*name*) const {#getShareByName}

Returns the [KSambaShareData](ksambasharedata.md) object of the share name.

`name` the share name.

Returns the [KSambaShareData](ksambasharedata.md) object that matches the name or an empty [KSambaShareData](ksambasharedata.md) object if there is no match for the name.

### QList\<KSambaShareData\> KSambaShare::getSharesByPath(const QString &*path*) const {#getSharesByPath}

Returns a list of [KSambaShareData](ksambasharedata.md) matching the path.

`path` the path that wants to get [KSambaShareData](ksambasharedata.md) object.

Returns the [QList](https://doc.qt.io/qt-6/qlist.html) of [KSambaShareData](ksambasharedata.md) objects that matches the path or an empty [QList](https://doc.qt.io/qt-6/qlist.html) if there aren't matches for the given path.

### \[static\] KSambaShare \*KSambaShare::instance() {#instance}

Returns the one and only instance of [KSambaShare](ksambashare.md).

### bool KSambaShare::isDirectoryShared(const QString &*path*) const {#isDirectoryShared}

Whether or not the given path is shared by Samba.

`path` the path to check if it is shared by Samba.

### bool KSambaShare::isShareNameAvailable(const QString &*name*) const {#isShareNameAvailable}

Tests that a share name is valid and does not conflict with system users names or shares.

`name` the share name.

Returns whether the given name is already being used or not.

### QString KSambaShare::lastSystemErrorString() const {#lastSystemErrorString}

Used to obtain UserShareSystemError error strings. This is usually the verbatim stderr of internal helper commands and may contain newlines. Do not use this to obtain error strings for other error types!

Returns [QString](https://doc.qt.io/qt-6/qstring.html) containing the most relevant last stderr

### QStringList KSambaShare::shareNames() const {#shareNames}

Returns the list of available shares.

Returns a [QStringList](https://doc.qt.io/qt-6/qstringlist.html) containing the user shares names or empty list if there aren't user shared directories.

### QStringList KSambaShare::sharedDirectories() const {#sharedDirectories}

Returns a list of all directories shared by local users in Samba. The resulting list is not sorted.
