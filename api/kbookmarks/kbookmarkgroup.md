---
title: "KBookmarkGroup Class"
description: "Bookmarks management library."
---

# KBookmarkGroup Class

Bookmarks management library. [More...](#details)

- **Header:** `#include <KBookmark>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS Bookmarks)`  
  `target_link_libraries(mytarget PRIVATE KF6::Bookmarks)`
- **Inherits:** [KBookmark](kbookmark.md)

[List of all members, including inherited members](kbookmarkgroup-members.md)

## Public Functions

- [KBookmarkGroup()](#KBookmarkGroup)
- [KBookmarkGroup(const QDomElement &elem)](#KBookmarkGroup-1)
- [KBookmark addBookmark(const KBookmark &bm)](#addBookmark)
- [KBookmark addBookmark(const QString &text, const QUrl &url, const QString &icon)](#addBookmark-1)
- [KBookmarkGroup createNewFolder(const QString &text)](#createNewFolder)
- [KBookmark createNewSeparator()](#createNewSeparator)
- [void deleteBookmark(const KBookmark &bk)](#deleteBookmark)
- [KBookmark first() const](#first)
- [QList\<QUrl\> groupUrlList() const](#groupUrlList)
- [int indexOf(const KBookmark &child) const](#indexOf)
- [bool isOpen() const](#isOpen)
- [bool isToolbarGroup() const](#isToolbarGroup)
- [bool moveBookmark(const KBookmark &bookmark, const KBookmark &after)](#moveBookmark)
- [KBookmark next(const KBookmark &current) const](#next)
- [KBookmark previous(const KBookmark &current) const](#previous)

## Detailed Description {#details}

A group of bookmarks

## Member Function Documentation {#member-function-documentation}

### KBookmarkGroup::KBookmarkGroup() {#KBookmarkGroup}

Create an invalid group. This is mostly for use in [QList](https://doc.qt.io/qt-6/qlist.html), and other places where we need a null group. Also used as a parent for a bookmark that doesn't have one (e.g. Netscape bookmarks)

### KBookmarkGroup::KBookmarkGroup(const QDomElement &*elem*) {#KBookmarkGroup-1}

Create a bookmark group as specified by the given element

### KBookmark KBookmarkGroup::addBookmark(const KBookmark &*bm*) {#addBookmark}

Create a new bookmark, as the last child of this group Don't forget to use KBookmarkManager::self()-\>emitChanged( parentBookmark );

`bm` the bookmark to add

### KBookmark KBookmarkGroup::addBookmark(const QString &*text*, const QUrl &*url*, const QString &*icon*) {#addBookmark-1}

Create a new bookmark, as the last child of this group Don't forget to use KBookmarkManager::self()-\>emitChanged( parentBookmark );

`text` for the bookmark

`url` the URL that the bookmark points to. It will be stored in its [QUrl::FullyEncoded](https://doc.qt.io/qt-6/qurl.html#ComponentFormattingOption-enum) string format.

`icon` the name of the icon to associate with the bookmark. A suitable default will be determined from the URL if not specified.

### KBookmarkGroup KBookmarkGroup::createNewFolder(const QString &*text*) {#createNewFolder}

Create a new bookmark folder, as the last child of this group

`text` for the folder.

If you want an dialog use [KBookmarkDialog](../kbookmarkswidgets/kbookmarkdialog.md)

### KBookmark KBookmarkGroup::createNewSeparator() {#createNewSeparator}

Create a new bookmark separator Don't forget to use KBookmarkManager::self()-\>emitChanged( parentBookmark );

### void KBookmarkGroup::deleteBookmark(const KBookmark &*bk*) {#deleteBookmark}

Delete a bookmark - it has to be one of our children ! Don't forget to use KBookmarkManager::self()-\>emitChanged( parentBookmark );

### KBookmark KBookmarkGroup::first() const {#first}

Return the first child bookmark of this group

### QList\<QUrl\> KBookmarkGroup::groupUrlList() const {#groupUrlList}

Returns the list of urls of bookmarks at top level of the group

### int KBookmarkGroup::indexOf(const KBookmark &*child*) const {#indexOf}

Return the index of a child bookmark, -1 if not found

### bool KBookmarkGroup::isOpen() const {#isOpen}

Returns true if the bookmark folder is opened in the bookmark editor

### bool KBookmarkGroup::isToolbarGroup() const {#isToolbarGroup}

Returns true if this is the toolbar group

### bool KBookmarkGroup::moveBookmark(const KBookmark &*bookmark*, const KBookmark &*after*) {#moveBookmark}

Moves `bookmark` after `after` (which should be a child of ours). If after is null, `bookmark` is moved as the first child. Don't forget to use KBookmarkManager::self()-\>emitChanged( parentBookmark );

### KBookmark KBookmarkGroup::next(const KBookmark &*current*) const {#next}

Return the next sibling of a child bookmark of this group

`current` has to be one of our child bookmarks.

### KBookmark KBookmarkGroup::previous(const KBookmark &*current*) const {#previous}

Return the previous sibling of a child bookmark of this group

`current` has to be one of our child bookmarks.
