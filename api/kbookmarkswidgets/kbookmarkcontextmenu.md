---
title: "KBookmarkContextMenu Class"
description: "A context menu for a bookmark."
---

# KBookmarkContextMenu Class

A context menu for a bookmark. [More...](#details)

- **Header:** `#include <KBookmarkContextMenu>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS Bookmarks)`  
  `target_link_libraries(mytarget PRIVATE KF6::BookmarksWidgets)`

[List of all members, including inherited members](kbookmarkcontextmenu-members.md)

## Public Functions

- [KBookmarkContextMenu(const KBookmark &bm, KBookmarkManager \*manager, KBookmarkOwner \*owner, QWidget \*parent = nullptr)](#KBookmarkContextMenu)
- [void addActions()](#addActions)
- [bool browserMode() const](#browserMode) (since 6.0)
- [void setBrowserMode(bool browserMode)](#setBrowserMode) (since 6.0)

## Public Slots

- [void slotCopyLocation()](#slotCopyLocation)
- [void slotEditAt()](#slotEditAt)
- [void slotInsert()](#slotInsert)
- [void slotOpenFolderInTabs()](#slotOpenFolderInTabs)
- [void slotProperties()](#slotProperties)
- [void slotRemove()](#slotRemove)

## Protected Functions

- [void addBookmark()](#addBookmark)
- [void addBookmarkActions()](#addBookmarkActions)
- [void addFolderActions()](#addFolderActions)
- [void addOpenFolderInTabs()](#addOpenFolderInTabs)
- [void addProperties()](#addProperties)
- [KBookmark bookmark() const](#bookmark)
- [KBookmarkManager \*manager() const](#manager)
- [KBookmarkOwner \*owner() const](#owner)

## Detailed Description {#details}

## Member Function Documentation {#member-function-documentation}

### KBookmarkContextMenu::KBookmarkContextMenu(const KBookmark &*bm*, KBookmarkManager \**manager*, KBookmarkOwner \**owner*, QWidget \**parent* = nullptr) {#KBookmarkContextMenu}

### \[virtual\] void KBookmarkContextMenu::addActions() {#addActions}

### \[protected\] void KBookmarkContextMenu::addBookmark() {#addBookmark}

### \[protected\] void KBookmarkContextMenu::addBookmarkActions() {#addBookmarkActions}

### \[protected\] void KBookmarkContextMenu::addFolderActions() {#addFolderActions}

### \[protected\] void KBookmarkContextMenu::addOpenFolderInTabs() {#addOpenFolderInTabs}

### \[protected\] void KBookmarkContextMenu::addProperties() {#addProperties}

### \[protected\] KBookmark KBookmarkContextMenu::bookmark() const {#bookmark}

### \[since 6.0\] bool KBookmarkContextMenu::browserMode() const {#browserMode}

Whether any "Edit Bookmarks" dialog shows UI elements that are specific to browsers.

This function was introduced in Qt 6.0.

*See also* [setBrowserMode](kbookmarkcontextmenu.md#setBrowserMode)()

### \[protected\] KBookmarkManager \*KBookmarkContextMenu::manager() const {#manager}

### \[protected\] KBookmarkOwner \*KBookmarkContextMenu::owner() const {#owner}

### \[since 6.0\] void KBookmarkContextMenu::setBrowserMode(bool *browserMode*) {#setBrowserMode}

Set this to true to make any "Edit Bookmarks" dialog show UI elements that are specific to browsers.

This function was introduced in Qt 6.0.

*See also* [browserMode](kbookmarkcontextmenu.md#browserMode)()

### \[slot\] void KBookmarkContextMenu::slotCopyLocation() {#slotCopyLocation}

### \[slot\] void KBookmarkContextMenu::slotEditAt() {#slotEditAt}

### \[slot\] void KBookmarkContextMenu::slotInsert() {#slotInsert}

### \[slot\] void KBookmarkContextMenu::slotOpenFolderInTabs() {#slotOpenFolderInTabs}

### \[slot\] void KBookmarkContextMenu::slotProperties() {#slotProperties}

### \[slot\] void KBookmarkContextMenu::slotRemove() {#slotRemove}
