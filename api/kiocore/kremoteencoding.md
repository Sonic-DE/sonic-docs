---
title: "KRemoteEncoding Class"
description: "Allows encoding and decoding properly remote filenames into Unicode."
---

# KRemoteEncoding Class

Allows encoding and decoding properly remote filenames into Unicode. [More...](#details)

- **Header:** `#include <KRemoteEncoding>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS KIO)`  
  `target_link_libraries(mytarget PRIVATE KF6::KIOCore)`

[List of all members, including inherited members](kremoteencoding-members.md)

## Public Functions

- [KRemoteEncoding(const char \*name = nullptr)](#KRemoteEncoding)
- [QString decode(const QByteArray &name) const](#decode)
- [QByteArray directory(const QUrl &url, bool ignore\_trailing\_slash = true) const](#directory)
- [QByteArray encode(const QString &name) const](#encode)
- [QByteArray encode(const QUrl &url) const](#encode-1)
- [const char \*encoding() const](#encoding)
- [QByteArray fileName(const QUrl &url) const](#fileName)
- [void setEncoding(const char \*name)](#setEncoding)

## Detailed Description {#details}

Certain protocols do not specify an appropriate encoding for decoding their 8-bit data into proper Unicode forms. Therefore, KIO workers should use this class in order to convert those forms into QStrings before creating the respective [KIO::UDSEntry](kio-udsentry.md). The same is true for decoding URLs to its components.

Each [KIO::WorkerBase](kio-workerbase.md) has one object of this kind, even if it is not necessary. It can be accessed through [KIO::WorkerBase::remoteEncoding](kio-workerbase.md#remoteEncoding).

## Member Function Documentation {#member-function-documentation}

### \[explicit\] KRemoteEncoding::KRemoteEncoding(const char \**name* = nullptr) {#KRemoteEncoding}

Constructor.

Constructs this object to use the given encoding name. If `name` is a null pointer, the standard encoding will be used.

### QString KRemoteEncoding::decode(const QByteArray &*name*) const {#decode}

Converts the given full pathname or filename to Unicode. This function is supposed to work for dirnames, filenames or a full pathname.

### QByteArray KRemoteEncoding::directory(const QUrl &*url*, bool *ignore\_trailing\_slash* = true) const {#directory}

Converts the given URL into 8-bit form and separate the dirname from the filename. This is useful for worker functions like stat or get.

The dirname is returned with the final slash always stripped

### QByteArray KRemoteEncoding::encode(const QString &*name*) const {#encode}

Converts the given `name` from Unicode. This function is supposed to work for dirnames, filenames or a full pathname.

### QByteArray KRemoteEncoding::encode(const QUrl &*url*) const {#encode-1}

Converts the given URL into its 8-bit components

### const char \*KRemoteEncoding::encoding() const {#encoding}

Returns the encoding being used.

*See also* [setEncoding](kremoteencoding.md#setEncoding)()

### QByteArray KRemoteEncoding::fileName(const QUrl &*url*) const {#fileName}

Converts the given URL into 8-bit form and retrieve the filename.

### void KRemoteEncoding::setEncoding(const char \**name*) {#setEncoding}

Sets the encoding being used. This function does not change the global configuration.

Pass a null pointer in `name` to revert to the standard encoding.

*See also* [encoding](kremoteencoding.md#encoding)()
