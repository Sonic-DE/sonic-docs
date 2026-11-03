---
title: "KUriFilterSearchProvider Class"
description: "Class that holds information about a search provider."
---

# KUriFilterSearchProvider Class

Class that holds information about a search provider. [More...](#details)

- **Header:** `#include <KUriFilter>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS KIO)`  
  `target_link_libraries(mytarget PRIVATE KIOGui)`

[List of all members, including inherited members](kurifiltersearchprovider-members.md)

## Public Functions

- [KUriFilterSearchProvider()](#KUriFilterSearchProvider)
- [KUriFilterSearchProvider(const KUriFilterSearchProvider &)](#KUriFilterSearchProvider-1)
- [QString defaultKey() const](#defaultKey)
- [QString desktopEntryName() const](#desktopEntryName)
- [QString iconName() const](#iconName)
- [QStringList keys() const](#keys)
- [QString name() const](#name)

## Protected Functions

- [void setDesktopEntryName(const QString &)](#setDesktopEntryName)
- [void setIconName(const QString &)](#setIconName)
- [void setKeys(const QStringList &)](#setKeys)
- [void setName(const QString &)](#setName)

## Detailed Description {#details}

## Member Function Documentation {#member-function-documentation}

### KUriFilterSearchProvider::KUriFilterSearchProvider() {#KUriFilterSearchProvider}

Default constructor.

### KUriFilterSearchProvider::KUriFilterSearchProvider(*const KUriFilterSearchProvider &*) {#KUriFilterSearchProvider-1}

Copy constructor.

### QString KUriFilterSearchProvider::defaultKey() const {#defaultKey}

Returns the default web shortcut key for this search provider.

Right now this is the same as doing [keys](kurifiltersearchprovider.md#keys)().first(), it might however change based on what the backend plugins do.

*See also* [keys](kurifiltersearchprovider.md#keys)

### QString KUriFilterSearchProvider::desktopEntryName() const {#desktopEntryName}

Returns the desktop filename of the search provider without any extension.

For example, if the desktop filename of the search provider was "foobar.desktop", this function will return "foobar".

*See also* [setDesktopEntryName](kurifiltersearchprovider.md#setDesktopEntryName)()

### \[virtual\] QString KUriFilterSearchProvider::iconName() const {#iconName}

Returns the icon name associated with the search provider when available.

*See also* [setIconName](kurifiltersearchprovider.md#setIconName)()

### QStringList KUriFilterSearchProvider::keys() const {#keys}

Returns all the web shortcut keys associated with this search provider.

*See also* [setKeys](kurifiltersearchprovider.md#setKeys)(), [defaultKey](kurifiltersearchprovider.md#defaultKey)

### QString KUriFilterSearchProvider::name() const {#name}

Returns the descriptive name of the search provider, e.g. "Google News".

This name comes from the "Name=" property entry in the desktop file that contains the search provider's information.

*See also* [setName](kurifiltersearchprovider.md#setName)()

### \[protected\] void KUriFilterSearchProvider::setDesktopEntryName(*const QString &*) {#setDesktopEntryName}

*See also* [desktopEntryName](kurifiltersearchprovider.md#desktopEntryName)()

### \[protected\] void KUriFilterSearchProvider::setIconName(*const QString &*) {#setIconName}

*See also* [iconName](kurifiltersearchprovider.md#iconName)()

### \[protected\] void KUriFilterSearchProvider::setKeys(*const QStringList &*) {#setKeys}

*See also* [keys](kurifiltersearchprovider.md#keys)()

### \[protected\] void KUriFilterSearchProvider::setName(*const QString &*) {#setName}

*See also* [name](kurifiltersearchprovider.md#name)()
