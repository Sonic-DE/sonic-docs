---
title: "KFileItemList Class"
description: "Network transparent access to files and data."
---

# KFileItemList Class

Network transparent access to files and data. [More...](#details)

- **Header:** `#include <KFileItem>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS KIO)`  
  `target_link_libraries(mytarget PRIVATE KF6::KIOCore)`
- **Inherits:** [QList](https://doc.qt.io/qt-6/qlist.html)

[List of all members, including inherited members](kfileitemlist-members.md)

## Public Functions

- [KFileItemList()](#KFileItemList)
- [KFileItemList(const QList\<KFileItem\> &items)](#KFileItemList-1)
- [KFileItemList(std::initializer\_list\<KFileItem\> items)](#KFileItemList-2)
- [KFileItem findByName(const QString &fileName) const](#findByName)
- [KFileItem findByUrl(const QUrl &url) const](#findByUrl)
- [QList\<QUrl\> targetUrlList() const](#targetUrlList)
- [QList\<QUrl\> urlList() const](#urlList)

## Detailed Description {#details}

List of [KFileItem](kfileitem.md), which adds a few helper methods to [QList](https://doc.qt.io/qt-6/qlist.html)\<[KFileItem](kfileitem.md)\>.

## Member Function Documentation {#member-function-documentation}

### KFileItemList::KFileItemList() {#KFileItemList}

Creates an empty list of file items.

### KFileItemList::KFileItemList(const QList\<KFileItem\> &*items*) {#KFileItemList-1}

Creates a new [KFileItemList](kfileitemlist.md) from a [QList](https://doc.qt.io/qt-6/qlist.html) of file `items`.

### KFileItemList::KFileItemList(std::initializer\_list\<KFileItem\> *items*) {#KFileItemList-2}

Creates a new [KFileItemList](kfileitemlist.md) from an initializer\_list of file `items`.

### KFileItem KFileItemList::findByName(const QString &*fileName*) const {#findByName}

Find a [KFileItem](kfileitem.md) by name and return it.

Returns the item with the given name, or a null-item if none was found (see [KFileItem::isNull](kfileitem.md#isNull)())

### KFileItem KFileItemList::findByUrl(const QUrl &*url*) const {#findByUrl}

Find a [KFileItem](kfileitem.md) by URL and return it.

Returns the item with the given URL, or a null-item if none was found (see [KFileItem::isNull](kfileitem.md#isNull)())

### QList\<QUrl\> KFileItemList::targetUrlList() const {#targetUrlList}

Returns the list of target URLs that those items represent

### QList\<QUrl\> KFileItemList::urlList() const {#urlList}

Returns the list of URLs that those items represent
