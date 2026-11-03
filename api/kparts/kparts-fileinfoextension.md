---
title: "KParts::FileInfoExtension Class"
description: "An extension for obtaining file information from the part."
---

# KParts::FileInfoExtension Class

An extension for obtaining file information from the part. [More...](#details)

- **Header:** `#include <KParts/FileInfoExtension>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS Parts)`  
  `target_link_libraries(mytarget PRIVATE KF6::Parts)`
- **Inherits:** [QObject](https://doc.qt.io/qt-6/qobject.html)

[List of all members, including inherited members](kparts-fileinfoextension-members.md)

## Public Types

- [enum FileInfoExtension::QueryMode](#QueryMode-enum)

## Public Functions

- [FileInfoExtension(KParts::ReadOnlyPart \*parent)](#FileInfoExtension)
- [bool hasSelection() const](#hasSelection)
- [KFileItemList queryFor(KParts::FileInfoExtension::QueryMode mode) const](#queryFor)
- [KParts::FileInfoExtension::QueryModes supportedQueryModes() const](#supportedQueryModes)

## Static Public Members

- [KParts::FileInfoExtension \*childObject(QObject \*obj)](#childObject)

## Detailed Description {#details}

This extension provides information about file and directory resources that are present in the part the implements it.

The main purpose of for this extension is to provide information about files and directories located on remote servers so that download managers such as kget can easily retrieve these resources.

## Member Type Documentation {#member-type-documentation}

### enum FileInfoExtension::QueryMode {#QueryMode-enum}

**flags FileInfoExtension::QueryModes**

Supported file information retrieval modes.

| Constant | Value | Description |
| --- | --- | --- |
| `KParts::FileInfoExtension::None` | `0x00` | Querying for file information is NOT possible |
| `KParts::FileInfoExtension::AllItems` | `0x01` | Retrieve or can retrieve file information for all items |
| `KParts::FileInfoExtension::SelectedItems` | `0x02` | Retrieve or can retrieve file information for selected items |

The `QueryModes` type is a typedef for `QFlags<QueryMode>. `It stores an OR combination of `QueryMode` values.

## Member Function Documentation {#member-function-documentation}

### \[explicit\] FileInfoExtension::FileInfoExtension(KParts::ReadOnlyPart \**parent*) {#FileInfoExtension}

### \[static\] KParts::FileInfoExtension \*FileInfoExtension::childObject(QObject \**obj*) {#childObject}

Queries `obj` for a child object which inherits from this class.

### \[virtual\] bool FileInfoExtension::hasSelection() const {#hasSelection}

Returns `true` if any of the items in the current view of the part that implements this extension are selected.

By default this function returns `false`.

### \[pure virtual\] KFileItemList FileInfoExtension::queryFor(KParts::FileInfoExtension::QueryMode *mode*) const {#queryFor}

Returns a information for files that match the specified query `mode`.

If the mode specified by `mode` is not supported or cannot be handled, then an empty list is returned.

### \[virtual\] KParts::FileInfoExtension::QueryModes FileInfoExtension::supportedQueryModes() const {#supportedQueryModes}

Returns the file information retrieve modes supported by the part that implements this extension.

By default this function returns None.
