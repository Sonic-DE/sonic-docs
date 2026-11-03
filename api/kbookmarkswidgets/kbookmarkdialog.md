---
title: "KBookmarkDialog Class"
description: "This class provides a Dialog for editing properties, adding Bookmarks and creating new folders."
---

# KBookmarkDialog Class

This class provides a Dialog for editing properties, adding Bookmarks and creating new folders. [More...](#details)

- **Header:** `#include <KBookmarkDialog>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS Bookmarks)`  
  `target_link_libraries(mytarget PRIVATE KF6::BookmarksWidgets)`

[List of all members, including inherited members](kbookmarkdialog-members.md)

## Public Functions

- [KBookmarkDialog(KBookmarkManager \*manager, QWidget \*parent = nullptr)](#KBookmarkDialog)
- [KBookmark addBookmark(const QString &title, const QUrl &url, const QString &icon, KBookmark parent = KBookmark())](#addBookmark)
- [KBookmarkGroup addBookmarks(const QList\<KBookmarkOwner::FutureBookmark\> &list, const QString &name = QString(), KBookmarkGroup parent = KBookmarkGroup())](#addBookmarks)
- [KBookmarkGroup createNewFolder(const QString &name, KBookmark parent = KBookmark())](#createNewFolder)
- [KBookmark editBookmark(const KBookmark &bm)](#editBookmark)
- [KBookmarkGroup selectFolder(KBookmark start = KBookmark())](#selectFolder)

## Public Slots

- [void newFolderButton()](#newFolderButton)

## Detailed Description {#details}

It can be used to show dialogs for common tasks with bookmarks.

It is used by [KBookmarkMenu](kbookmarkmenu.md) to show a dialog for "Properties", "Add Bookmark" and "Create New Folder". If you want to customize those dialogs, derive from [KBookmarkOwner](../kbookmarks/kbookmarkowner.md) and reimplement bookmarkDialog(), return a [KBookmarkDialog](kbookmarkdialog.md) subclass and reimplement initLayout(), aboutToShow() and save().

## Member Function Documentation {#member-function-documentation}

### KBookmarkDialog::KBookmarkDialog(KBookmarkManager \**manager*, QWidget \**parent* = nullptr) {#KBookmarkDialog}

Creates a [KBookmarkDialog](kbookmarkdialog.md) instance

### KBookmark KBookmarkDialog::addBookmark(const QString &*title*, const QUrl &*url*, const QString &*icon*, KBookmark *parent* = KBookmark()) {#addBookmark}

Shows a "Add Bookmark" dialog

> **Note:** this updates the bookmark and calls [KBookmarkManager::emitChanged](../kbookmarks/kbookmarkmanager.md#emitChanged)

### KBookmarkGroup KBookmarkDialog::addBookmarks(const QList\<KBookmarkOwner::FutureBookmark\> &*list*, const QString &*name* = QString(), KBookmarkGroup *parent* = KBookmarkGroup()) {#addBookmarks}

Creates a folder from a list of bookmarks

> **Note:** this updates the bookmark and calls [KBookmarkManager::emitChanged](../kbookmarks/kbookmarkmanager.md#emitChanged)

### KBookmarkGroup KBookmarkDialog::createNewFolder(const QString &*name*, KBookmark *parent* = KBookmark()) {#createNewFolder}

Shows a dialog to create a new folder.

### KBookmark KBookmarkDialog::editBookmark(const KBookmark &*bm*) {#editBookmark}

Shows a properties dialog

> **Note:** this updates the bookmark and calls [KBookmarkManager::emitChanged](../kbookmarks/kbookmarkmanager.md#emitChanged)

### \[protected slot\] void KBookmarkDialog::newFolderButton() {#newFolderButton}

### KBookmarkGroup KBookmarkDialog::selectFolder(KBookmark *start* = KBookmark()) {#selectFolder}

Shows a dialog to select a folder.
