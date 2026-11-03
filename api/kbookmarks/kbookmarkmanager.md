---
title: "KBookmarkManager Class"
description: "This class implements the reading/writing of bookmarks in XML."
---

# KBookmarkManager Class

This class implements the reading/writing of bookmarks in XML. [More...](#details)

- **Header:** `#include <KBookmarkManager>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS Bookmarks)`  
  `target_link_libraries(mytarget PRIVATE KF6::Bookmarks)`
- **Inherits:** [QObject](https://doc.qt.io/qt-6/qobject.html)

[List of all members, including inherited members](kbookmarkmanager-members.md)

## Public Functions

- [KBookmarkManager(const QString &bookmarksFile, QObject \*parent = nullptr)](#KBookmarkManager) (since 6.0)
- [~KBookmarkManager()](#dtor.KBookmarkManager)
- [void emitChanged()](#emitChanged)
- [void emitChanged(const KBookmarkGroup &group)](#emitChanged-1)
- [KBookmark findByAddress(const QString &address)](#findByAddress)
- [KBookmarkGroup root() const](#root)
- [bool save(bool toolbarCache = true) const](#save)
- [bool saveAs(const QString &filename, bool toolbarCache = true) const](#saveAs)
- [KBookmarkGroup toolbar()](#toolbar)
- [bool updateAccessMetadata(const QString &url)](#updateAccessMetadata)

## Signals

- [void changed(const QString &groupAddress)](#changed)
- [void error(const QString &errorMessage)](#error)

## Detailed Description {#details}

The bookmarks file is read and written using the XBEL standard (http://pyxml.sourceforge.net/topics/xbel/)

A sample file looks like this:

```cpp
<xbel>
  <bookmark href="http://techbase.kde.org"><title>Developer Web Site</title></bookmark>
  <folder folded="no">
    <title>Title of this folder</title>
    <bookmark icon="kde" href="http://www.kde.org"><title>KDE Web Site</title></bookmark>
    <folder toolbar="yes">
      <title>My own bookmarks</title>
      <bookmark href="http://www.koffice.org"><title>KOffice Web Site</title></bookmark>
      <separator/>
      <bookmark href="http://www.kdevelop.org"><title>KDevelop Web Site</title></bookmark>
    </folder>
  </folder>
</xbel>
```

## Member Function Documentation {#member-function-documentation}

### \[explicit, since 6.0\] KBookmarkManager::KBookmarkManager(const QString &*bookmarksFile*, QObject \**parent* = nullptr) {#KBookmarkManager}

Create a [KBookmarkManager](kbookmarkmanager.md) responsible for the given `bookmarksFile`.

The manager watches the file for change detection.

`bookmarksFile` full path to the bookmarks file, Use ~/.kde/share/apps/konqueror/bookmarks.xml for the konqueror bookmarks

This function was introduced in Qt 6.0.

### \[override virtual noexcept\] KBookmarkManager::~KBookmarkManager() {#dtor.KBookmarkManager}

Destructor

### \[signal\] void KBookmarkManager::changed(const QString &*groupAddress*) {#changed}

Signals that the group (or any of its children) with the address `groupAddress` (e.g. "/4/5") has been modified. connect to this

### void KBookmarkManager::emitChanged() {#emitChanged}

Saves the bookmark file and notifies everyone.

### void KBookmarkManager::emitChanged(const KBookmarkGroup &*group*) {#emitChanged-1}

Saves the bookmark file and notifies everyone.

`group` the parent of all changed bookmarks

### \[signal\] void KBookmarkManager::error(const QString &*errorMessage*) {#error}

Emitted when an error occurs. Contains the translated error message.

### KBookmark KBookmarkManager::findByAddress(const QString &*address*) {#findByAddress}

Returns the bookmark designated by `address`

`address` the address belonging to the bookmark you're looking for

`tolerate` when true tries to find the most tolerable bookmark position

*See also* [KBookmark::address](kbookmark.md#address)

### KBookmarkGroup KBookmarkManager::root() const {#root}

This will return the root bookmark. It is used to iterate through the bookmarks manually. It is mostly used internally.

Returns the root (top-level) bookmark

### bool KBookmarkManager::save(bool *toolbarCache* = true) const {#save}

Save the bookmarks to an XML file on disk. You should use [emitChanged](kbookmarkmanager.md#emitChanged)() instead of this function, it saves and notifies everyone that the file has changed. Only use this if you don't want the [emitChanged](kbookmarkmanager.md#emitChanged) signal.

`toolbarCache` iff true save a cache of the toolbar folder, too

Returns true if saving was successful

### bool KBookmarkManager::saveAs(const QString &*filename*, bool *toolbarCache* = true) const {#saveAs}

Save the bookmarks to the given XML file on disk.

`filename` full path to the desired bookmarks file location

`toolbarCache` iff true save a cache of the toolbar folder, too

Returns true if saving was successful

### KBookmarkGroup KBookmarkManager::toolbar() {#toolbar}

This returns the root of the toolbar menu. In the XML, this is the group with the attribute toolbar=yes

Returns the toolbar group

### bool KBookmarkManager::updateAccessMetadata(const QString &*url*) {#updateAccessMetadata}

Update access time stamps for a given url.

`url` the viewed url

Return true if any metadata was modified (bookmarks file is not saved automatically)
