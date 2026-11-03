---
title: "KZipFileEntry Class"
description: "Represents a file in a zip archive."
---

# KZipFileEntry Class

Represents a file in a zip archive. [More...](#details)

- **Header:** `#include <KZipFileEntry>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS Archive)`  
  `target_link_libraries(mytarget PRIVATE KF6::Archive)`
- **Inherits:** [KArchiveFile](karchivefile.md)

[List of all members, including inherited members](kzipfileentry-members.md)

## Public Functions

- [KZipFileEntry(KZip \*zip, const QString &name, int access, const QDateTime &date, const QString &user, const QString &group, const QString &symlink, const QString &path, qint64 start, qint64 uncompressedSize, int encoding, qint64 compressedSize)](#KZipFileEntry)
- [qint64 compressedSize() const](#compressedSize)
- [unsigned long crc32() const](#crc32)
- [QIODevice \*createDevice() const](#createDevice)
- [QByteArray data() const](#data)
- [int encoding() const](#encoding)
- [qint64 headerStart() const](#headerStart)
- [const QString &path() const](#path)
- [void setCRC32(unsigned long crc32)](#setCRC32)
- [void setCompressedSize(qint64 compressedSize)](#setCompressedSize)
- [void setHeaderStart(qint64 headerstart)](#setHeaderStart)

## Detailed Description {#details}

## Member Function Documentation {#member-function-documentation}

### KZipFileEntry::KZipFileEntry(KZip \**zip*, const QString &*name*, int *access*, const QDateTime &*date*, const QString &*user*, const QString &*group*, const QString &*symlink*, const QString &*path*, qint64 *start*, qint64 *uncompressedSize*, int *encoding*, qint64 *compressedSize*) {#KZipFileEntry}

Creates a new zip file entry. Do not call this, [KZip](kzip.md) takes care of it.

### qint64 KZipFileEntry::compressedSize() const {#compressedSize}

Only used when writing

*See also* [setCompressedSize](kzipfileentry.md#setCompressedSize)()

### unsigned long KZipFileEntry::crc32() const {#crc32}

CRC: only used when writing

### \[override virtual\] QIODevice \*KZipFileEntry::createDevice() const {#createDevice}

Reimplements: [KArchiveFile::createDevice() const](karchivefile.md#createDevice).

This method returns a [QIODevice](https://doc.qt.io/qt-6/qiodevice.html) to read the file contents.

This is obviously for reading only.

Note that the ownership of the device is being transferred to the caller, who will have to delete it.

The returned device auto-opens (in readonly mode), no need to open it.

> **Note:** It can return nullptr

### \[override virtual\] QByteArray KZipFileEntry::data() const {#data}

Reimplements: [KArchiveFile::data() const](karchivefile.md#data).

Returns the content of this file.

> **Note:** The data returned by this call is not cached.

> **Warning:** This method loads the entire file content into memory at once. For large files or untrusted archives, this could cause excessive memory allocation. Consider reading in chunks using [createDevice](kzipfileentry.md#createDevice)() instead when dealing with archives from untrusted sources.

### int KZipFileEntry::encoding() const {#encoding}

### qint64 KZipFileEntry::headerStart() const {#headerStart}

Header start: only used when writing

*See also* [setHeaderStart](kzipfileentry.md#setHeaderStart)()

### const QString &KZipFileEntry::path() const {#path}

Name with complete path - [KArchiveFile::name](karchiveentry.md#name)() is the filename only (no path)

### void KZipFileEntry::setCRC32(unsigned long *crc32*) {#setCRC32}

CRC: only used when writing

### void KZipFileEntry::setCompressedSize(qint64 *compressedSize*) {#setCompressedSize}

Only used when writing

*See also* [compressedSize](kzipfileentry.md#compressedSize)()

### void KZipFileEntry::setHeaderStart(qint64 *headerstart*) {#setHeaderStart}

Header start: only used when writing

*See also* [headerStart](kzipfileentry.md#headerStart)()
