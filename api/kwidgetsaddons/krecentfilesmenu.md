---
title: "KRecentFilesMenu Class"
description: "A menu that offers a set of recent files."
---

# KRecentFilesMenu Class

A menu that offers a set of recent files. [More...](#details)

- **Header:** `#include <KRecentFilesMenu>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS WidgetsAddons)`  
  `target_link_libraries(mytarget PRIVATE KF6::WidgetsAddons)`
- **Inherits:** [QMenu](https://doc.qt.io/qt-6/qmenu.html)

[List of all members, including inherited members](krecentfilesmenu-members.md)

## Public Functions

- [KRecentFilesMenu(QWidget \*parent = nullptr)](#KRecentFilesMenu)
- [KRecentFilesMenu(const QString &title, QWidget \*parent = nullptr)](#KRecentFilesMenu-1)
- [void addUrl(const QUrl &url, const QString &name = QString())](#addUrl)
- [QString group() const](#group)
- [int maximumItems() const](#maximumItems)
- [QList\<QUrl\> recentFiles() const](#recentFiles)
- [void removeUrl(const QUrl &url)](#removeUrl)
- [void setGroup(const QString &group)](#setGroup)
- [void setMaximumItems(size\_t maximumItems)](#setMaximumItems)

## Public Slots

- [void clearRecentFiles()](#clearRecentFiles)

## Signals

- [void recentFilesChanged()](#recentFilesChanged)
- [void urlTriggered(const QUrl &url)](#urlTriggered)

## Detailed Description {#details}

## Member Function Documentation {#member-function-documentation}

### \[explicit\] KRecentFilesMenu::KRecentFilesMenu(QWidget \**parent* = nullptr) {#KRecentFilesMenu}

### \[explicit\] KRecentFilesMenu::KRecentFilesMenu(const QString &*title*, QWidget \**parent* = nullptr) {#KRecentFilesMenu-1}

### void KRecentFilesMenu::addUrl(const QUrl &*url*, const QString &*name* = QString()) {#addUrl}

Add URL to recent files list. This will enable this action.

`url` The URL of the file

`name` The user visible pretty name that appears before the URL

### \[slot\] void KRecentFilesMenu::clearRecentFiles() {#clearRecentFiles}

Clear recent files list.

*See also* [recentFiles](krecentfilesmenu.md#recentFiles)(), [recentFilesChanged](krecentfilesmenu.md#recentFilesChanged)()

### QString KRecentFilesMenu::group() const {#group}

The group the URLs are saved to/read from. Unless a group is specified by [setGroup](krecentfilesmenu.md#setGroup) "RecentFiles" is used.

*See also* [setGroup](krecentfilesmenu.md#setGroup)()

### int KRecentFilesMenu::maximumItems() const {#maximumItems}

The maximum number of files this menu can hold.

When the maximum url count is reached and a new URL is added the oldest will be replaced.

By default maximum 10 URLs are shown.

*See also* [setMaximumItems](krecentfilesmenu.md#setMaximumItems)()

### QList\<QUrl\> KRecentFilesMenu::recentFiles() const {#recentFiles}

List of URLs of recent files.

*See also* [clearRecentFiles](krecentfilesmenu.md#clearRecentFiles)(), [recentFilesChanged](krecentfilesmenu.md#recentFilesChanged)()

### \[signal\] void KRecentFilesMenu::recentFilesChanged() {#recentFilesChanged}

Emitted when the recent files list has been changed.

*See also* [recentFiles](krecentfilesmenu.md#recentFiles)(), [clearRecentFiles](krecentfilesmenu.md#clearRecentFiles)()

### void KRecentFilesMenu::removeUrl(const QUrl &*url*) {#removeUrl}

Remove a URL from the recent files list.

`url` The URL of the file

### void KRecentFilesMenu::setGroup(const QString &*group*) {#setGroup}

Specify a group for storing the URLs. This allows e.g. storing multiple types of recent files.

By default the group "RecentFiles" is used.

`group` the name of the group.

*See also* [group](krecentfilesmenu.md#group)()

### void KRecentFilesMenu::setMaximumItems(size\_t *maximumItems*) {#setMaximumItems}

Set the maximum URL count.

*See also* [maximumItems](krecentfilesmenu.md#maximumItems)()

### \[signal\] void KRecentFilesMenu::urlTriggered(const QUrl &*url*) {#urlTriggered}

Emitted when the user clicks on a file action.

Usually this should result in the specified URL being opened.

`url` The url associated with the triggered action.
