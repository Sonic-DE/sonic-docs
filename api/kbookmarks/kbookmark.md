---
title: "KBookmark Class"
description: "A class representing a bookmark."
---

# KBookmark Class

A class representing a bookmark. [More...](#details)

- **Header:** `#include <KBookmark>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS Bookmarks)`  
  `target_link_libraries(mytarget PRIVATE KF6::Bookmarks)`
- **Inherited By:** [KBookmarkGroup](kbookmarkgroup.md)

[List of all members, including inherited members](kbookmark-members.md)

## Public Types

- [enum KBookmark::MetaDataOverwriteMode](#MetaDataOverwriteMode-enum)

## Public Functions

- [KBookmark()](#KBookmark)
- [KBookmark(const QDomElement &elem)](#KBookmark-1)
- [QString address() const](#address)
- [QString description() const](#description)
- [QString fullText() const](#fullText)
- [bool hasParent() const](#hasParent)
- [QString icon() const](#icon)
- [bool isGroup() const](#isGroup)
- [bool isNull() const](#isNull)
- [bool isSeparator() const](#isSeparator)
- [QDomNode metaData(const QString &owner, bool create) const](#metaData)
- [QString metaDataItem(const QString &key) const](#metaDataItem)
- [QString mimeType() const](#mimeType)
- [KBookmarkGroup parentGroup() const](#parentGroup)
- [void populateMimeData(QMimeData \*mimeData) const](#populateMimeData)
- [int positionInParent() const](#positionInParent)
- [void setDescription(const QString &description)](#setDescription)
- [void setFullText(const QString &fullText)](#setFullText)
- [void setIcon(const QString &icon)](#setIcon)
- [void setMetaDataItem(const QString &key, const QString &value, KBookmark::MetaDataOverwriteMode mode = OverwriteMetaData)](#setMetaDataItem)
- [void setMimeType(const QString &mimeType)](#setMimeType)
- [void setShowInToolbar(bool show)](#setShowInToolbar)
- [void setUrl(const QUrl &url)](#setUrl)
- [bool showInToolbar() const](#showInToolbar)
- [QString text() const](#text)
- [KBookmarkGroup toGroup() const](#toGroup)
- [void updateAccessMetadata()](#updateAccessMetadata)
- [QUrl url() const](#url)
- [bool KBookmark::operator==(const KBookmark &rhs) const](#operator-eq-eq)

## Static Public Members

- [QString commonParent(const QString &A, const QString &B)](#commonParent)
- [QString nextAddress(const QString &address)](#nextAddress)
- [QString parentAddress(const QString &address)](#parentAddress)
- [uint positionInParent(const QString &address)](#positionInParent-1)
- [QString previousAddress(const QString &address)](#previousAddress)
- [KBookmark standaloneBookmark(const QString &text, const QUrl &url, const QString &icon)](#standaloneBookmark)

## Detailed Description {#details}

## Member Type Documentation {#member-type-documentation}

### enum KBookmark::MetaDataOverwriteMode {#MetaDataOverwriteMode-enum}

| Constant |   |
| --- | --- |
| `KBookmark::OverwriteMetaData` | `0` |
| `KBookmark::DontOverwriteMetaData` | `1` |

## Member Function Documentation {#member-function-documentation}

### KBookmark::KBookmark() {#KBookmark}

Constructs a null bookmark, i.e. a bookmark for which [isNull](kbookmark.md#isNull)() returns true If you want to create a new bookmark use eitehr [KBookmarkGroup](kbookmarkgroup.md).addBookmark or if you want an interactive dialog use [KBookmarkDialog](../kbookmarkswidgets/kbookmarkdialog.md).

### \[explicit\] KBookmark::KBookmark(const QDomElement &*elem*) {#KBookmark-1}

Creates the [KBookmark](kbookmark.md) wrapper for `elem` Mostly for internal usage.

### QString KBookmark::address() const {#address}

Return the "address" of this bookmark in the whole tree. This is used when telling other processes about a change in a given bookmark. The encoding of the address is "/4/2", for instance, to designate the 2nd child inside the 4th child of the root bookmark.

### \[static\] QString KBookmark::commonParent(const QString &*A*, const QString &*B*) {#commonParent}

Returns the common parent of both addresses which has the greatest depth

### QString KBookmark::description() const {#description}

Returns Description of the bookmark

*See also* [setDescription](kbookmark.md#setDescription)()

### QString KBookmark::fullText() const {#fullText}

Text shown for the bookmark, not truncated. You should not use this - this is mainly for keditbookmarks.

*See also* [setFullText](kbookmark.md#setFullText)()

### bool KBookmark::hasParent() const {#hasParent}

Returns true if bookmark is contained by a QDomDocument, if not it is most likely that it has become separated and is thus invalid and/or has been deleted from the bookmarks.

### QString KBookmark::icon() const {#icon}

Returns the pixmap file for this bookmark (i.e. the name of the icon)

*See also* [setIcon](kbookmark.md#setIcon)()

### bool KBookmark::isGroup() const {#isGroup}

Whether the bookmark is a group or a normal bookmark

### bool KBookmark::isNull() const {#isNull}

Returns true if this is a null bookmark. This will never be the case for a real bookmark (in a menu), but it's used for instance as the end condition for [KBookmarkGroup::next](kbookmarkgroup.md#next)()

### bool KBookmark::isSeparator() const {#isSeparator}

Whether the bookmark is a separator

### QDomNode KBookmark::metaData(const QString &*owner*, bool *create*) const {#metaData}

Returns the metadata container node for a certain metadata owner

### QString KBookmark::metaDataItem(const QString &*key*) const {#metaDataItem}

Get the value of a specific metadata item (owner = "http://www.kde.org"). a key Name of the metadata item

Returns Value of the metadata item. QString() is returned in case the specified key does not exist.

*See also* [setMetaDataItem](kbookmark.md#setMetaDataItem)()

### QString KBookmark::mimeType() const {#mimeType}

Returns Mime-Type of this item

*See also* [setMimeType](kbookmark.md#setMimeType)()

### \[static\] QString KBookmark::nextAddress(const QString &*address*) {#nextAddress}

Returns address of next sibling (e.g. /4/5/2 -\> /4/5/3) This doesn't check whether it actually exists

### \[static\] QString KBookmark::parentAddress(const QString &*address*) {#parentAddress}

Returns address of parent

### KBookmarkGroup KBookmark::parentGroup() const {#parentGroup}

Returns the group containing this bookmark

### void KBookmark::populateMimeData(QMimeData \**mimeData*) const {#populateMimeData}

Adds this bookmark into the given [QMimeData](https://doc.qt.io/qt-6/qmimedata.html).

> **Warning:** do not call this method multiple times, use [KBookmark::List::populateMimeData](kbookmark-list.md#populateMimeData) instead.

`mimeData` the [QMimeData](https://doc.qt.io/qt-6/qmimedata.html) instance used to drag or copy this bookmark

### int KBookmark::positionInParent() const {#positionInParent}

Return the position in the parent, i.e. the last number in the address

### \[static\] uint KBookmark::positionInParent(const QString &*address*) {#positionInParent-1}

Returns position in parent (e.g. /4/5/2 -\> 2)

### \[static\] QString KBookmark::previousAddress(const QString &*address*) {#previousAddress}

Returns address of previous sibling (e.g. /4/5/2 -\> /4/5/1) Returns QString() for a first child

### void KBookmark::setDescription(const QString &*description*) {#setDescription}

Set the description of the bookmark

`description`

*See also* [description](kbookmark.md#description)()

### void KBookmark::setFullText(const QString &*fullText*) {#setFullText}

Set the text shown for the bookmark.

`fullText` the new bookmark title

*See also* [fullText](kbookmark.md#fullText)()

### void KBookmark::setIcon(const QString &*icon*) {#setIcon}

Set the icon name of the bookmark

`icon` the new icon name for this bookmark

*See also* [icon](kbookmark.md#icon)()

### void KBookmark::setMetaDataItem(const QString &*key*, const QString &*value*, KBookmark::MetaDataOverwriteMode *mode* = OverwriteMetaData) {#setMetaDataItem}

Change the value of a specific metadata item, or create the given item if it doesn't exist already (owner = "http://www.kde.org").

`key` Name of the metadata item to change

`value` Value to use for the specified metadata item

`mode` Whether to overwrite the item's value if it exists already or not.

*See also* [metaDataItem](kbookmark.md#metaDataItem)()

### void KBookmark::setMimeType(const QString &*mimeType*) {#setMimeType}

Set the Mime-Type of this item

*See also* [mimeType](kbookmark.md#mimeType)()

### void KBookmark::setShowInToolbar(bool *show*) {#setShowInToolbar}

Set whether this bookmark is show in a filterd toolbar

*See also* [showInToolbar](kbookmark.md#showInToolbar)()

### void KBookmark::setUrl(const QUrl &*url*) {#setUrl}

Set the URL of the bookmark

`url` the new bookmark URL

*See also* [url](kbookmark.md#url)()

### bool KBookmark::showInToolbar() const {#showInToolbar}

Returns if the bookmark should be shown in the toolbar (used by the filtered toolbar)

*See also* [setShowInToolbar](kbookmark.md#setShowInToolbar)()

### \[static\] KBookmark KBookmark::standaloneBookmark(const QString &*text*, const QUrl &*url*, const QString &*icon*) {#standaloneBookmark}

Creates a stand alone bookmark. This is fairly expensive since a new QDom Tree is build.

### QString KBookmark::text() const {#text}

Text shown for the bookmark If bigger than 40, the text is shortened by replacing middle characters with "..." (see KStringHandler::csqueeze)

### KBookmarkGroup KBookmark::toGroup() const {#toGroup}

Convert this to a group - do this only if [isGroup](kbookmark.md#isGroup)() returns true.

### void KBookmark::updateAccessMetadata() {#updateAccessMetadata}

Updates the bookmarks access metadata Call when a user accesses the bookmark

### QUrl KBookmark::url() const {#url}

URL contained by the bookmark

*See also* [setUrl](kbookmark.md#setUrl)()

### bool KBookmark::operator==(const KBookmark &*rhs*) const {#operator-eq-eq}

Comparison operator
