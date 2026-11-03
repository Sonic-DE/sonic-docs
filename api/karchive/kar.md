---
title: "KAr Class"
description: "A class for reading ar archives."
---

# KAr Class

A class for reading ar archives. [More...](#details)

- **Header:** `#include <KAr>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS Archive)`  
  `target_link_libraries(mytarget PRIVATE KF6::Archive)`
- **Inherits:** [KArchive](karchive.md)

[List of all members, including inherited members](kar-members.md)

## Public Functions

- [KAr(QIODevice \*dev)](#KAr)
- [KAr(const QString &filename)](#KAr-1)
- [~KAr()](#dtor.KAr)

## Detailed Description {#details}

KAr is a class for reading archives in ar format. Writing is not supported. Reading archives that contain files bigger than INT\_MAX - 32 bytes is not supported.

## Member Function Documentation {#member-function-documentation}

### \[explicit\] KAr::KAr(QIODevice \**dev*) {#KAr}

Creates an instance that operates on the given device.

The device can be compressed ([KCompressionDevice](kcompressiondevice.md)) or not ([QFile](https://doc.qt.io/qt-6/qfile.html), etc.).

`dev` the device to read from

### \[explicit\] KAr::KAr(const QString &*filename*) {#KAr-1}

Creates an instance that operates on the given filename.

`filename` is a local path (e.g. "/home/holger/myfile.ar")

### \[override virtual noexcept\] KAr::~KAr() {#dtor.KAr}

If the ar file is still opened, then it will be closed automatically by the destructor.
