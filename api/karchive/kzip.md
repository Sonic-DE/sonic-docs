---
title: "KZip Class"
description: "A class for reading / writing zip archives."
---

# KZip Class

A class for reading / writing zip archives. [More...](#details)

- **Header:** `#include <KZip>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS Archive)`  
  `target_link_libraries(mytarget PRIVATE KF6::Archive)`
- **Inherits:** [KArchive](karchive.md)

[List of all members, including inherited members](kzip-members.md)

## Public Types

- [enum KZip::Compression](#Compression-enum)
- [enum KZip::ExtraField](#ExtraField-enum)

## Public Functions

- [KZip(QIODevice \*dev)](#KZip)
- [KZip(const QString &filename)](#KZip-1)
- [~KZip()](#dtor.KZip)
- [KZip::Compression compression() const](#compression)
- [KZip::ExtraField extraField() const](#extraField)
- [void setCompression(KZip::Compression c)](#setCompression)
- [void setExtraField(KZip::ExtraField ef)](#setExtraField)

## Detailed Description {#details}

You can use it in QIODevice::ReadOnly or in QIODevice::WriteOnly mode, and it behaves just as expected. It can also be used in QIODevice::ReadWrite mode, in this case one can append files to an existing zip archive. When you append new files, which are not yet in the zip, it works as expected, i.e. the files are appended at the end. When you append a file, which is already in the file, the reference to the old file is dropped and the new one is added to the zip - but the old data from the file itself is not deleted, it is still in the zipfile. So when you want to have a small and garbage-free zipfile, just read the contents of the appended zip file and write it to a new one in QIODevice::WriteOnly mode. This is especially important when you don't want to leak information of how intermediate versions of files in the zip were looking.

For more information on the zip fileformat go to http://www.pkware.com/products/enterprise/white_papers/appnote.html

## Member Type Documentation {#member-type-documentation}

### enum KZip::Compression {#Compression-enum}

Describes the compression type for a given file in the Zip archive.

| Constant | Value | Description |
| --- | --- | --- |
| `KZip::NoCompression` | `0` | Uncompressed |
| `KZip::DeflateCompression` | `1` | Deflate compression method |

### enum KZip::ExtraField {#ExtraField-enum}

Describes the contents of the "extra field" for a given file in the Zip archive.

| Constant | Value | Description |
| --- | --- | --- |
| `KZip::NoExtraField` | `0` | No extra field |
| `KZip::ModificationTime` | `1` | Modification time ("extended timestamp" header) |

## Member Function Documentation {#member-function-documentation}

### \[explicit\] KZip::KZip(QIODevice \**dev*) {#KZip}

Creates an instance that operates on the given device.

The device can be compressed ([KCompressionDevice](kcompressiondevice.md)) or not ([QFile](https://doc.qt.io/qt-6/qfile.html), etc.).

`dev` the device to access

> **Warning:** Do not assume that giving a [QFile](https://doc.qt.io/qt-6/qfile.html) here will decompress the file, in case it's compressed!

### \[explicit\] KZip::KZip(const QString &*filename*) {#KZip-1}

Creates an instance that operates on the given filename. using the compression filter associated to given mimetype.

`filename` is a local path (e.g. "/home/holger/myfile.zip")

### \[override virtual noexcept\] KZip::~KZip() {#dtor.KZip}

If the zip file is still opened, then it will be closed automatically by the destructor.

### KZip::Compression KZip::compression() const {#compression}

The current compression mode that will be used for new files.

Returns the current compression mode

*See also* [setCompression](kzip.md#setCompression)()

### KZip::ExtraField KZip::extraField() const {#extraField}

The current type of "extra field" that will be used for new files.

Returns the current type of "extra field"

*See also* [setExtraField](kzip.md#setExtraField)()

### void KZip::setCompression(KZip::Compression *c*) {#setCompression}

Call this before writeFile or prepareWriting, to define whether the next files to be written should be compressed or not.

`c` the new compression mode

*See also* [compression](kzip.md#compression)()

### void KZip::setExtraField(KZip::ExtraField *ef*) {#setExtraField}

Call this before writeFile or prepareWriting, to define what the next file to be written should have in its extra field.

`ef` the type of "extra field"

*See also* [extraField](kzip.md#extraField)()
