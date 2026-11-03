---
title: "KBookmark::List Class"
description: "Bookmarks management library."
---

# KBookmark::List Class

Bookmarks management library. [More...](#details)

- **Header:** `#include <List>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS Bookmarks)`  
  `target_link_libraries(mytarget PRIVATE KF6::Bookmarks)`
- **Inherits:** [QList](https://doc.qt.io/qt-6/qlist.html)

[List of all members, including inherited members](kbookmark-list-members.md)

## Public Functions

- [List()](#List)
- [void populateMimeData(QMimeData \*mimeData) const](#populateMimeData)

## Static Public Members

- [bool canDecode(const QMimeData \*mimeData)](#canDecode)
- [KBookmark::List fromMimeData(const QMimeData \*mimeData, QDomDocument &parentDocument)](#fromMimeData)
- [QStringList mimeDataTypes()](#mimeDataTypes)

## Detailed Description {#details}

[KBookmark::List](kbookmark-list.md) is a [QList](https://doc.qt.io/qt-6/qlist.html) that contains bookmarks with a few convenience methods.

*See also* [KBookmark](kbookmark.md), [QList](https://doc.qt.io/qt-6/qlist.html)

## Member Function Documentation {#member-function-documentation}

### List::List() {#List}

### \[static\] bool List::canDecode(const QMimeData \**mimeData*) {#canDecode}

Return true if `mimeData` contains bookmarks

### \[static\] KBookmark::List List::fromMimeData(const QMimeData \**mimeData*, QDomDocument &*parentDocument*) {#fromMimeData}

Extract a list of bookmarks from the contents of `mimeData`. Decoding will fail if `mimeData` does not contain any bookmarks.

`mimeData` the mime data to extract from; cannot be 0

`parentDocument` pass an empty QDomDocument here, it will be used as container for the bookmarks. You just need to make sure it stays alive longer (or just as long) as the returned bookmarks.

Returns the list of bookmarks

### \[static\] QStringList List::mimeDataTypes() {#mimeDataTypes}

Return the list of mimeTypes that can be decoded by [fromMimeData](kbookmark-list.md#fromMimeData)

### void List::populateMimeData(QMimeData \**mimeData*) const {#populateMimeData}

Adds this list of bookmark into the given [QMimeData](https://doc.qt.io/qt-6/qmimedata.html).

`mimeData` the [QMimeData](https://doc.qt.io/qt-6/qmimedata.html) instance used to drag or copy this bookmark
