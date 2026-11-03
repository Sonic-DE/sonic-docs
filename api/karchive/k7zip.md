---
title: "K7Zip Class"
description: "A class for reading / writing p7zip archives."
---

# K7Zip Class

A class for reading / writing p7zip archives. [More...](#details)

- **Header:** `#include <K7Zip>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS Archive)`  
  `target_link_libraries(mytarget PRIVATE KF6::Archive)`
- **Inherits:** [KArchive](karchive.md)

[List of all members, including inherited members](k7zip-members.md)

## Public Functions

- [K7Zip(QIODevice \*dev)](#K7Zip)
- [K7Zip(const QString &filename)](#K7Zip-1)
- [~K7Zip()](#dtor.K7Zip)
- [bool passwordNeeded() const](#passwordNeeded) (since 6.13)
- [void setPassword(const QString &password)](#setPassword) (since 6.13)

## Protected Functions

- [bool openArchive(QIODevice::OpenMode mode)](#openArchive)

## Detailed Description {#details}

## Member Function Documentation {#member-function-documentation}

### \[explicit\] K7Zip::K7Zip(QIODevice \**dev*) {#K7Zip}

Creates an instance that operates on the given device.

The device can be compressed ([KCompressionDevice](kcompressiondevice.md)) or not ([QFile](https://doc.qt.io/qt-6/qfile.html), etc.).

> **Warning:** Do not assume that giving a [QFile](https://doc.qt.io/qt-6/qfile.html) here will decompress the file, in case it's compressed!

`dev` the device to read from. If the source is compressed, the [QIODevice](https://doc.qt.io/qt-6/qiodevice.html) must take care of decompression

### \[explicit\] K7Zip::K7Zip(const QString &*filename*) {#K7Zip-1}

Creates an instance that operates on the given filename using the compression filter associated to given mimetype.

`filename` is a local path (e.g. "/home/user/myfile.7z")

### \[override virtual noexcept\] K7Zip::~K7Zip() {#dtor.K7Zip}

If the archive is still opened, then it will be closed automatically by the destructor.

### \[override virtual protected\] bool K7Zip::openArchive(QIODevice::OpenMode *mode*) {#openArchive}

Reimplements: [KArchive::openArchive(QIODevice::OpenMode mode)](karchive.md#openArchive).

Opens the archive for reading.

Parses the directory listing of the archive and creates the [KArchiveDirectory](karchivedirectory.md)/[KArchiveFile](karchivefile.md) entries.

`mode` the mode of the file

### \[since 6.13\] bool K7Zip::passwordNeeded() const {#passwordNeeded}

Whether the archive needs a password to be opened.

> **Note:** This can only be called after [open](karchive.md#open)() has been called once.

Returns `true` if the archive requires a password to be opened

This function was introduced in Qt 6.13.

### \[since 6.13\] void K7Zip::setPassword(const QString &*password*) {#setPassword}

Sets the password to use for encrypted archives.

This method must be called before opening the archive.

> **Note:** Currently only AES decryption is supported.

`password` the password to use for encrypted archive

This function was introduced in Qt 6.13.
