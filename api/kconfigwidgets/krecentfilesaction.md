---
title: "KRecentFilesAction Class"
description: "Recent files action."
---

# KRecentFilesAction Class

Recent files action. [More...](#details)

- **Header:** `#include <KRecentFilesAction>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS ConfigWidgets)`  
  `target_link_libraries(mytarget PRIVATE KF6::ConfigWidgets)`
- **Inherits:** [KSelectAction](../kwidgetsaddons/kselectaction.md)

[List of all members, including inherited members](krecentfilesaction-members.md)

## Public Functions

- [KRecentFilesAction(QObject \*parent)](#KRecentFilesAction)
- [KRecentFilesAction(const QString &text, QObject \*parent)](#KRecentFilesAction-1)
- [KRecentFilesAction(const QIcon &icon, const QString &text, QObject \*parent)](#KRecentFilesAction-2)
- [void addAction(QAction \*action, const QUrl &url, const QString &name, const QMimeType &mimeType = QMimeType())](#addAction)
- [void addUrl(const QUrl &url, const QString &name = QString())](#addUrl)
- [void addUrl(const QUrl &url, const QString &name, const QString &mimeType)](#addUrl-1) (since 6.9)
- [void loadEntries(const KConfigGroup &config)](#loadEntries)
- [int maxItems() const](#maxItems)
- [void removeUrl(const QUrl &url)](#removeUrl)
- [void saveEntries(const KConfigGroup &config)](#saveEntries)
- [void setMaxItems(int maxItems)](#setMaxItems)
- [QList\<QUrl\> urls() const](#urls)

## Public Slots

- [void clear()](#clear)

## Signals

- [void recentListCleared()](#recentListCleared)
- [void urlSelected(const QUrl &url)](#urlSelected)

## Detailed Description {#details}

This class is an action to handle a recent files submenu. The best way to create the action is to use [KStandardAction::openRecent](kstandardaction.md#openRecent). Then you simply need to call [loadEntries](krecentfilesaction.md#loadEntries) on startup, [saveEntries](krecentfilesaction.md#saveEntries) on shutdown, addURL when your application loads/saves a file.

## Member Function Documentation {#member-function-documentation}

### \[explicit\] KRecentFilesAction::KRecentFilesAction(QObject \**parent*) {#KRecentFilesAction}

Constructs an action with the specified parent.

`parent` The parent of this action.

### KRecentFilesAction::KRecentFilesAction(const QString &*text*, QObject \**parent*) {#KRecentFilesAction-1}

Constructs an action with text; a shortcut may be specified by the ampersand character (e.g. "&Option" creates a shortcut with key `O` )

This is the most common KAction used when you do not have a corresponding icon (note that it won't appear in the current version of the "Edit ToolBar" dialog, because an action needs an icon to be plugged in a toolbar...).

`text` The text that will be displayed.

`parent` The parent of this action.

### KRecentFilesAction::KRecentFilesAction(const QIcon &*icon*, const QString &*text*, QObject \**parent*) {#KRecentFilesAction-2}

Constructs an action with text and an icon; a shortcut may be specified by the ampersand character (e.g. "&Option" creates a shortcut with key `O` )

This is the other common KAction used. Use it when you `do` have a corresponding icon.

`icon` The icon to display.

`text` The text that will be displayed.

`parent` The parent of this action.

### void KRecentFilesAction::addAction(QAction \**action*, const QUrl &*url*, const QString &*name*, const QMimeType &*mimeType* = QMimeType()) {#addAction}

Adds `action` to the list of URLs, with `url` and title `name`.

Do not use addAction([QAction](https://doc.qt.io/qt-6/qaction.html)\*), as no url will be associated, and consequently [urlSelected](krecentfilesaction.md#urlSelected)() will not be emitted when `action` is selected.

### void KRecentFilesAction::addUrl(const QUrl &*url*, const QString &*name* = QString()) {#addUrl}

Add URL to the recent files list. This will enable this action.

`url` The URL of the file

`name` The user visible pretty name that appears before the URL

> **Note:** URLs corresponding to local files in the temporary directory (see [QDir::tempPath](https://doc.qt.io/qt-6/qdir.html#tempPath)()) are automatically ignored by this method.

### \[since 6.9\] void KRecentFilesAction::addUrl(const QUrl &*url*, const QString &*name*, const QString &*mimeType*) {#addUrl-1}

Add URL to the recent files list. This will enable this action.

`url` The URL of the file

`name` The user visible pretty name that appears before the URL

`mimeType` Specify the mimeType of the file

> **Note:** URLs corresponding to local files in the temporary directory (see [QDir::tempPath](https://doc.qt.io/qt-6/qdir.html#tempPath)()) are automatically ignored by this method.

This function was introduced in Qt 6.9.

### \[virtual slot\] void KRecentFilesAction::clear() {#clear}

Clears the recent files list. Note that there is also an action shown to the user for clearing the list.

### void KRecentFilesAction::loadEntries(const KConfigGroup &*config*) {#loadEntries}

Loads the recent files entries from a given [KConfigGroup](../kconfigcore/kconfiggroup.md) object. You can provide the name of the group used to load the entries. If the groupname is empty, entries are loaded from a group called 'RecentFiles'. Local file entries that do not exist anymore are not restored.

### int KRecentFilesAction::maxItems() const {#maxItems}

Returns the maximum of items in the recent files list.

> **Note:** Getter function for property maxItems.

*See also* [setMaxItems](krecentfilesaction.md#setMaxItems)()

### \[signal\] void KRecentFilesAction::recentListCleared() {#recentListCleared}

This signal gets emitted when the user clear list. So when user store url in specific config file it can saveEntry.

### void KRecentFilesAction::removeUrl(const QUrl &*url*) {#removeUrl}

Remove an URL from the recent files list.

`url` The URL of the file

### void KRecentFilesAction::saveEntries(const KConfigGroup &*config*) {#saveEntries}

Saves the current recent files entries to a given [KConfigGroup](../kconfigcore/kconfiggroup.md) object. You can provide the name of the group used to load the entries. If the groupname is empty, entries are saved to a group called 'RecentFiles'.

### void KRecentFilesAction::setMaxItems(int *maxItems*) {#setMaxItems}

Sets the maximum of items in the recent files list. The default for this value is 10 set in the constructor.

If this value is lesser than the number of items currently in the recent files list the last items are deleted until the number of items are equal to the new maximum.

Negative values will be normalized to 0.

> **Note:** Setter function for property maxItems.

*See also* [maxItems](krecentfilesaction.md#maxItems)()

### \[signal\] void KRecentFilesAction::urlSelected(const QUrl &*url*) {#urlSelected}

This signal gets emitted when the user selects an URL.

`url` The URL that the user selected.

### QList\<QUrl\> KRecentFilesAction::urls() const {#urls}

Retrieve a list of all URLs in the recent files list.
