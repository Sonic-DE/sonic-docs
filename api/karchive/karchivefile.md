---
title: "KArchiveFile Class"
description: "A file in an archive."
---

# KArchiveFile Class

A file in an archive. [More...](#details)

- **Header:** `#include <KArchiveFile>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS Archive)`  
  `target_link_libraries(mytarget PRIVATE KF6::Archive)`
- **Inherits:** [KArchiveEntry](karchiveentry.md)
- **Inherited By:** [KZipFileEntry](kzipfileentry.md)

[List of all members, including inherited members](karchivefile-members.md)

## Public Functions

- [KArchiveFile(KArchive \*archive, const QString &name, int access, const QDateTime &date, const QString &user, const QString &group, const QString &symlink, qint64 pos, qint64 size)](#KArchiveFile)
- [~KArchiveFile()](#dtor.KArchiveFile)
- [bool copyTo(const QString &dest) const](#copyTo)
- [QIODevice \*createDevice() const](#createDevice)
- [QByteArray data() const](#data)
- [bool isFile() const](#isFile)
- [qint64 position() const](#position)
- [void setSize(qint64 s)](#setSize)
- [qint64 size() const](#size)

## Detailed Description {#details}

*See also* [KArchive](karchive-index.md), [KArchiveDirectory](karchivedirectory.md)

## Member Function Documentation {#member-function-documentation}

### KArchiveFile::KArchiveFile(KArchive \**archive*, const QString &*name*, int *access*, const QDateTime &*date*, const QString &*user*, const QString &*group*, const QString &*symlink*, qint64 *pos*, qint64 *size*) {#KArchiveFile}

Creates a new file entry. Do not call this, [KArchive](karchive-module.md) takes care of it. `archive` the entries archive `name` the name of the entry `access` the permissions in unix format `date` the date (in seconds since 1970) `user` the user that owns the entry `group` the group that owns the entry `symlink` the symlink, or QString() `pos` the position of the file in the directory `size` the size of the file

### \[override virtual noexcept\] KArchiveFile::~KArchiveFile() {#dtor.KArchiveFile}

Destructor. Do not call this, [KArchive](karchive-module.md) takes care of it.

### bool KArchiveFile::copyTo(const QString &*dest*) const {#copyTo}

Extracts the file to the directory `dest` `dest` the directory to extract to Returns true on success, false if the file (dest + '/' + [name](karchiveentry.md#name)()) couldn't be created

### \[virtual\] QIODevice \*KArchiveFile::createDevice() const {#createDevice}

This method returns [QIODevice](https://doc.qt.io/qt-6/qiodevice.html) (internal class: KLimitedIODevice) on top of the underlying [QIODevice](https://doc.qt.io/qt-6/qiodevice.html). This is obviously for reading only.

WARNING: Note that the ownership of the device is being transferred to the caller, who will have to delete it.

The returned device auto-opens (in readonly mode), no need to open it. Returns the [QIODevice](https://doc.qt.io/qt-6/qiodevice.html) of the file

### \[virtual\] QByteArray KArchiveFile::data() const {#data}

Returns the content of this file.

> **Note:** The data returned by this call is not cached.

> **Warning:** This method loads the entire file content into memory at once. For large files or untrusted archives, this could cause excessive memory allocation. Consider reading in chunks using [createDevice](karchivefile.md#createDevice)() instead when dealing with archives from untrusted sources.

### \[override virtual\] bool KArchiveFile::isFile() const {#isFile}

Reimplements: [KArchiveEntry::isFile() const](karchiveentry.md#isFile).

Checks whether this entry is a file. Returns true, since this entry is a file

### qint64 KArchiveFile::position() const {#position}

Position of the data in the \[uncompressed\] archive. Returns the position of the file

### void KArchiveFile::setSize(qint64 *s*) {#setSize}

Set size of data, usually after writing the file. `s` the new size of the file

*See also* [size](karchivefile.md#size)()

### qint64 KArchiveFile::size() const {#size}

Size of the data. Returns the size of the file

*See also* [setSize](karchivefile.md#setSize)()
