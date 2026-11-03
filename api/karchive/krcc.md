---
title: "KRcc Class"
description: "A class for reading rcc resources."
---

# KRcc Class

A class for reading rcc resources. [More...](#details)

- **Header:** `#include <KRcc>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS Archive)`  
  `target_link_libraries(mytarget PRIVATE KF6::Archive)`
- **Inherits:** [KArchive](karchive.md)

[List of all members, including inherited members](krcc-members.md)

## Public Functions

- [KRcc(const QString &filename)](#KRcc)
- [~KRcc()](#dtor.KRcc)

## Protected Functions

- [bool closeArchive()](#closeArchive)
- [bool openArchive(QIODevice::OpenMode mode)](#openArchive)

## Detailed Description {#details}

[KRcc](krcc.md) is a class for reading dynamic binary resources created by Qt's rcc tool from a .qrc file and the files it points to.

Writing is not supported.

## Member Function Documentation {#member-function-documentation}

### \[explicit\] KRcc::KRcc(const QString &*filename*) {#KRcc}

Creates an instance that operates on the given filename.

`filename` is a local path (e.g. "/home/holger/myfile.rcc")

### \[override virtual noexcept\] KRcc::~KRcc() {#dtor.KRcc}

If the rcc file is still opened, then it will be closed automatically by the destructor.

### \[override virtual protected\] bool KRcc::closeArchive() {#closeArchive}

Reimplements: [KArchive::closeArchive()](karchive.md#closeArchive).

Unregisters the .rcc resource from the [QResource](https://doc.qt.io/qt-6/qresource.html) system.

### \[override virtual protected\] bool KRcc::openArchive(QIODevice::OpenMode *mode*) {#openArchive}

Reimplements: [KArchive::openArchive(QIODevice::OpenMode mode)](karchive.md#openArchive).

Registers the .rcc resource in the [QResource](https://doc.qt.io/qt-6/qresource.html) system under a unique identifier, then lists that, and creates the [KArchiveFile](karchivefile.md)/[KArchiveDirectory](karchivedirectory.md) entries.
