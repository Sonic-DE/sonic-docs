---
title: "KBookmarkMenu Class"
description: "This class provides a bookmark menu."
---

# KBookmarkMenu Class

This class provides a bookmark menu. [More...](#details)

- **Header:** `#include <KBookmarkMenu>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS Bookmarks)`  
  `target_link_libraries(mytarget PRIVATE KF6::BookmarksWidgets)`
- **Inherits:** [QObject](https://doc.qt.io/qt-6/qobject.html)

[List of all members, including inherited members](kbookmarkmenu-members.md)

## Public Functions

- [KBookmarkMenu(KBookmarkManager \*manager, KBookmarkOwner \*owner, QMenu \*parentMenu)](#KBookmarkMenu)
- [KBookmarkMenu(KBookmarkManager \*mgr, KBookmarkOwner \*owner, QMenu \*parentMenu, const QString &parentAddress)](#KBookmarkMenu-1)
- [QAction \*addBookmarkAction() const](#addBookmarkAction)
- [QAction \*bookmarkTabsAsFolderAction() const](#bookmarkTabsAsFolderAction)
- [bool browserMode() const](#browserMode) (since 6.0)
- [QAction \*editBookmarksAction() const](#editBookmarksAction)
- [void ensureUpToDate()](#ensureUpToDate)
- [QAction \*newBookmarkFolderAction() const](#newBookmarkFolderAction)
- [void setBrowserMode(bool browserMode)](#setBrowserMode) (since 6.0)

## Protected Functions

- [KBookmarkManager \*manager() const](#manager)
- [KBookmarkOwner \*owner() const](#owner)
- [QString parentAddress() const](#parentAddress)
- [QMenu \*parentMenu() const](#parentMenu)

## Detailed Description {#details}

It is typically used in cooperation with [KActionMenu](../kwidgetsaddons/kactionmenu.md) but doesn't have to be.

If you use this class by itself, then it will use KDE defaults for everything – the bookmark path, bookmark editor, bookmark launcher.. everything. These defaults reside in the classes [KBookmarkOwner](../kbookmarks/kbookmarkowner.md) (editing bookmarks) and [KBookmarkManager](../kbookmarks/kbookmarkmanager.md) (almost everything else). If you wish to change the defaults in any way, you must reimplement either this class or [KBookmarkOwner](../kbookmarks/kbookmarkowner.md).

Using this class is very simple:

1) Create a popup menu (either [KActionMenu](../kwidgetsaddons/kactionmenu.md) or QMenu will do) 2) Instantiate a new [KBookmarkMenu](kbookmarkmenu.md) object using the above popup menu as a parameter 3) Insert your (now full) popup menu wherever you wish

The functionality of this class can be disabled with the "action/bookmarks" Kiosk action (see the KAuthorized namespace).

## Member Function Documentation {#member-function-documentation}

### KBookmarkMenu::KBookmarkMenu(KBookmarkManager \**manager*, KBookmarkOwner \**owner*, QMenu \**parentMenu*) {#KBookmarkMenu}

Fills a bookmark menu (one instance of [KBookmarkMenu](kbookmarkmenu.md) is created for the toplevel menu, but also one per submenu).

`manager` the bookmark manager to use (i.e. for reading and writing)

`owner` implementation of the [KBookmarkOwner](../kbookmarks/kbookmarkowner.md) callback interface.

> **Note:** If you pass a null [KBookmarkOwner](../kbookmarks/kbookmarkowner.md) to the constructor, the openBookmark signal is not emitted, instead QDesktopServices::openUrl is used to open the bookmark.

`parentMenu` menu to be filled

### KBookmarkMenu::KBookmarkMenu(KBookmarkManager \**mgr*, KBookmarkOwner \**owner*, QMenu \**parentMenu*, const QString &*parentAddress*) {#KBookmarkMenu-1}

Creates a bookmark submenu

Currently this is a [QObject](https://doc.qt.io/qt-6/qobject.html) without a parent, use setParent to benefit from automatic deletion.

### QAction \*KBookmarkMenu::addBookmarkAction() const {#addBookmarkAction}

Returns the action for adding a bookmark. If you are using KXmlGui, you can add it to your action collection.

```cpp
KBookmarkMenu *menu = new KBookmarkMenu(manager, owner, parentMenu);
QAction *addAction = menu->addBookmarkAction();
actionCollection()->addAction(addAction->objectName(), addAction);
```

Returns the action for adding a bookmark.

### QAction \*KBookmarkMenu::bookmarkTabsAsFolderAction() const {#bookmarkTabsAsFolderAction}

Returns the action for adding all current tabs as bookmarks. If you are using KXmlGui, you can add it to your action collection.

```cpp
KBookmarkMenu *menu = new KBookmarkMenu(manager, owner, parentMenu);
QAction *bookmarkTabsAction = menu->bookmarkTabsAsFolderAction();
actionCollection()->addAction(bookmarkTabsAction->objectName(), bookmarkTabsAction);
```

Returns the action for adding all current tabs as bookmarks.

### \[since 6.0\] bool KBookmarkMenu::browserMode() const {#browserMode}

Whether any "Edit Bookmarks" dialog shows UI elements that are specific to browsers.

This function was introduced in Qt 6.0.

*See also* [setBrowserMode](kbookmarkmenu.md#setBrowserMode)()

### QAction \*KBookmarkMenu::editBookmarksAction() const {#editBookmarksAction}

Returns the action for editing bookmarks. If you are using KXmlGui, you can add it to your action collection.

```cpp
KBookmarkMenu *menu = new KBookmarkMenu(manager, owner, parentMenu);
QAction *editAction = menu->editBookmarksAction();
actionCollection()->addAction(editAction->objectName(), editAction);
```

Returns the action for editing bookmarks.

### void KBookmarkMenu::ensureUpToDate() {#ensureUpToDate}

Call ensureUpToDate() if you need [KBookmarkMenu](kbookmarkmenu.md) to adjust to its final size before it is executed.

### \[protected\] KBookmarkManager \*KBookmarkMenu::manager() const {#manager}

### QAction \*KBookmarkMenu::newBookmarkFolderAction() const {#newBookmarkFolderAction}

Returns the action for adding a new bookmarks folder. If you are using KXmlGui, you can add it to your action collection.

```cpp
KBookmarkMenu *menu = new KBookmarkMenu(manager, owner, parentMenu);
QAction *newBookmarkFolderAction = menu->bookmarkTabsAsFolderAction();
actionCollection()->addAction(newBookmarkFolderAction->objectName(), newBookmarkFolderAction);
```

Returns the action for adding a new bookmarks folder

### \[protected\] KBookmarkOwner \*KBookmarkMenu::owner() const {#owner}

### \[protected\] QString KBookmarkMenu::parentAddress() const {#parentAddress}

Parent bookmark for this menu.

### \[protected\] QMenu \*KBookmarkMenu::parentMenu() const {#parentMenu}

The menu in which we insert our actions Supplied in the constructor.

### \[since 6.0\] void KBookmarkMenu::setBrowserMode(bool *browserMode*) {#setBrowserMode}

Set this to true to make any "Edit Bookmarks" dialog show UI elements that are specific to browsers.

This function was introduced in Qt 6.0.

*See also* [browserMode](kbookmarkmenu.md#browserMode)()
