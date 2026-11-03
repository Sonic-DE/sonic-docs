---
title: "KFileItemListProperties Class"
description: "Provides information about the common properties of a group of KFileItem objects."
---

# KFileItemListProperties Class

Provides information about the common properties of a group of [KFileItem](kfileitem.md) objects. [More...](#details)

- **Header:** `#include <KFileItemListProperties>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS KIO)`  
  `target_link_libraries(mytarget PRIVATE KF6::KIOCore)`

[List of all members, including inherited members](kfileitemlistproperties-members.md)

## Public Functions

- [KFileItemListProperties()](#KFileItemListProperties)
- [KFileItemListProperties(const KFileItemList &items)](#KFileItemListProperties-1)
- [KFileItemListProperties(const KFileItemListProperties &)](#KFileItemListProperties-2)
- [bool isDirectory() const](#isDirectory)
- [bool isFile() const](#isFile)
- [bool isLocal() const](#isLocal)
- [KFileItemList items() const](#items)
- [QString mimeGroup() const](#mimeGroup)
- [QString mimeType() const](#mimeType)
- [void setItems(const KFileItemList &items)](#setItems)
- [bool supportsDeleting() const](#supportsDeleting)
- [bool supportsMoving() const](#supportsMoving)
- [bool supportsReading() const](#supportsReading)
- [bool supportsWriting() const](#supportsWriting)
- [QList\<QUrl\> urlList() const](#urlList)

## Detailed Description {#details}

Given a list of KFileItems, this class can determine (and cache) the common MIME type for all items, whether all items are directories, whether all items are readable, writable, etc. As soon as one file item does not support a specific capability (read, write etc.), it is marked as unsupported for all items.

This class is implicitly shared, which means it can be used as a value and copied around at almost no cost.

## Member Function Documentation {#member-function-documentation}

### KFileItemListProperties::KFileItemListProperties() {#KFileItemListProperties}

Default constructor. Use [setItems](kfileitemlistproperties.md#setItems) to specify the items.

### KFileItemListProperties::KFileItemListProperties(const KFileItemList &*items*) {#KFileItemListProperties-1}

Constructor that takes a [KFileItemList](kfileitemlist.md) and sets the capabilities supported by all the FileItems as true.

`items` The list of items that are to have their supported capabilities checked.

### KFileItemListProperties::KFileItemListProperties(*const KFileItemListProperties &*) {#KFileItemListProperties-2}

Copy constructor

### bool KFileItemListProperties::isDirectory() const {#isDirectory}

Returns `true` if all items are directories

### bool KFileItemListProperties::isFile() const {#isFile}

Returns whether all items are files, as reported by [KFileItem::isFile](kfileitem.md#isFile)().

### bool KFileItemListProperties::isLocal() const {#isLocal}

Check if files are local

Returns `true` if all the FileItems are local, otherwise there is one or more remote file, so false.

### KFileItemList KFileItemListProperties::items() const {#items}

List of fileitems passed to the constructor or to [setItems](kfileitemlistproperties.md#setItems)().

*See also* [setItems](kfileitemlistproperties.md#setItems)()

### QString KFileItemListProperties::mimeGroup() const {#mimeGroup}

Returns the MIME type group (e.g. "text") of all items, if they all have the same, otherwise an empty string

### QString KFileItemListProperties::mimeType() const {#mimeType}

Returns the MIME type of all items, if they all have the same, otherwise an empty string

### void KFileItemListProperties::setItems(const KFileItemList &*items*) {#setItems}

Sets the items that are to have their supported capabilities checked.

*See also* [items](kfileitemlistproperties.md#items)()

### bool KFileItemListProperties::supportsDeleting() const {#supportsDeleting}

Check if deleting capability is supported

Returns `true` if all the FileItems can be deleted, otherwise false.

### bool KFileItemListProperties::supportsMoving() const {#supportsMoving}

Check if moving capability is supported

Returns `true` if all the FileItems can be moved, otherwise false.

### bool KFileItemListProperties::supportsReading() const {#supportsReading}

Check if reading capability is supported

Returns `true` if all the FileItems can be read, otherwise false.

### bool KFileItemListProperties::supportsWriting() const {#supportsWriting}

Check if writing capability is supported (file managers use this mostly for directories)

Returns `true` if all the FileItems can be written to, otherwise false.

### QList\<QUrl\> KFileItemListProperties::urlList() const {#urlList}

List of urls, gathered from the fileitems
