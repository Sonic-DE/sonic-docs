---
title: "BluezQt::ObexFileTransferEntry Class"
description: "OBEX file transfer entry."
---

# BluezQt::ObexFileTransferEntry Class

OBEX file transfer entry. [More...](#details)

- **Header:** `#include <BluezQt/ObexFileTransferEntry>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS BluezQt)`  
  `target_link_libraries(mytarget PRIVATE KF6::BluezQt)`

[List of all members, including inherited members](bluezqt-obexfiletransferentry-members.md)

## Public Types

- [enum ObexFileTransferEntry::Type](#Type-enum)

## Public Functions

- [ObexFileTransferEntry()](#ObexFileTransferEntry)
- [ObexFileTransferEntry(const BluezQt::ObexFileTransferEntry &other)](#ObexFileTransferEntry-1)
- [bool isValid() const](#isValid)
- [QString label() const](#label)
- [QString memoryType() const](#memoryType)
- [QDateTime modificationTime() const](#modificationTime)
- [QString name() const](#name)
- [QString permissions() const](#permissions)
- [quint64 size() const](#size)
- [BluezQt::ObexFileTransferEntry::Type type() const](#type)
- [BluezQt::ObexFileTransferEntry &ObexFileTransferEntry::operator=(const BluezQt::ObexFileTransferEntry &other)](#operator-eq)

## Detailed Description {#details}

This class represents an entry in the remote file system.

## Member Type Documentation {#member-type-documentation}

### enum ObexFileTransferEntry::Type {#Type-enum}

Type of entry.

| Constant | Value | Description |
| --- | --- | --- |
| `BluezQt::ObexFileTransferEntry::File` | `0` | Indicates that the entry is a file. |
| `BluezQt::ObexFileTransferEntry::Folder` | `1` | Indicates that the entry is a folder. |
| `BluezQt::ObexFileTransferEntry::Invalid` | `2` | Indicates that the entry is invalid. |

## Member Function Documentation {#member-function-documentation}

### \[explicit\] ObexFileTransferEntry::ObexFileTransferEntry() {#ObexFileTransferEntry}

Creates a new invalid [ObexFileTransferEntry](bluezqt-obexfiletransferentry.md) object.

### ObexFileTransferEntry::ObexFileTransferEntry(const BluezQt::ObexFileTransferEntry &*other*) {#ObexFileTransferEntry-1}

Constructs a new [ObexFileTransferEntry](bluezqt-obexfiletransferentry.md) object from `other`.

### bool ObexFileTransferEntry::isValid() const {#isValid}

Returns whether the entry is valid.

This only checks if [type](bluezqt-obexfiletransferentry.md#type)() != Invalid.

### QString ObexFileTransferEntry::label() const {#label}

Returns the label of the entry.

### QString ObexFileTransferEntry::memoryType() const {#memoryType}

Returns memory type where the entry is stored.

### QDateTime ObexFileTransferEntry::modificationTime() const {#modificationTime}

Returns the modification time of the entry.

### QString ObexFileTransferEntry::name() const {#name}

Returns the name of the entry.

### QString ObexFileTransferEntry::permissions() const {#permissions}

Returns the permissions of the entry.

### quint64 ObexFileTransferEntry::size() const {#size}

Returns the size of the entry.

The size is a number of items in the folder or file size in bytes.

### BluezQt::ObexFileTransferEntry::Type ObexFileTransferEntry::type() const {#type}

Returns the type of the entry.

The entry can be either a file or folder.

### BluezQt::ObexFileTransferEntry &ObexFileTransferEntry::operator=(const BluezQt::ObexFileTransferEntry &*other*) {#operator-eq}

Copies the [ObexFileTransferEntry](bluezqt-obexfiletransferentry.md) object from `other`.
