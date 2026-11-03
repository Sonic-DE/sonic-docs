---
title: "KBookmarkAction Class"
description: "This class is a QAction for bookmarks."
---

# KBookmarkAction Class

This class is a QAction for bookmarks. [More...](#details)

- **Header:** `#include <KBookmarkAction>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS Bookmarks)`  
  `target_link_libraries(mytarget PRIVATE KF6::Bookmarks)`
- **Inherits:** [KBookmarkActionInterface](kbookmarkactioninterface.md) and

[List of all members, including inherited members](kbookmarkaction-members.md)

## Public Functions

- [KBookmarkAction(const KBookmark &bk, KBookmarkOwner \*owner, QObject \*parent)](#KBookmarkAction)

## Public Slots

- [void slotSelected(Qt::MouseButtons mb, Qt::KeyboardModifiers km)](#slotSelected)

## Detailed Description {#details}

It provides a nice constructor. And on triggered uses the owner to open the bookmark.

## Member Function Documentation {#member-function-documentation}

### KBookmarkAction::KBookmarkAction(const KBookmark &*bk*, KBookmarkOwner \**owner*, QObject \**parent*) {#KBookmarkAction}

### \[slot\] void KBookmarkAction::slotSelected(Qt::MouseButtons *mb*, Qt::KeyboardModifiers *km*) {#slotSelected}
