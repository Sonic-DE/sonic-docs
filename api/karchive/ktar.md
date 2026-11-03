---
title: "KTar Class"
description: "A class for reading / writing (optionally compressed) tar archives."
---

# KTar Class

A class for reading / writing (optionally compressed) tar archives. [More...](#details)

- **Header:** `#include <KTar>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS Archive)`  
  `target_link_libraries(mytarget PRIVATE KF6::Archive)`
- **Inherits:** [KArchive](karchive.md)

[List of all members, including inherited members](ktar-members.md)

## Public Functions

- [KTar(QIODevice \*dev)](#KTar)
- [KTar(const QString &filename, const QString &mimetype = QString())](#KTar-1)
- [~KTar()](#dtor.KTar)
- [void setOrigFileName(const QByteArray &fileName)](#setOrigFileName)

## Detailed Description {#details}

[KTar](ktar.md) allows you to read and write tar archives, including those that are compressed using gzip, bzip2, xz or lzip.

## Member Function Documentation {#member-function-documentation}

### \[explicit\] KTar::KTar(QIODevice \**dev*) {#KTar}

Creates an instance that operates on the given device.

The device can be compressed ([KCompressionDevice](kcompressiondevice.md)) or not ([QFile](https://doc.qt.io/qt-6/qfile.html), etc.).

> **Warning:** Do not assume that giving a [QFile](https://doc.qt.io/qt-6/qfile.html) here will decompress the file, in case it's compressed!

`dev` the device to read from. If the source is compressed, the [QIODevice](https://doc.qt.io/qt-6/qiodevice.html) must take care of decompression

### \[explicit\] KTar::KTar(const QString &*filename*, const QString &*mimetype* = QString()) {#KTar-1}

Creates an instance that operates on the given filename using the compression filter associated to given mimetype.

`filename` is a local path (e.g. "/home/weis/myfile.tgz")

`mimetype` "application/gzip" (before 5.85: "application/x-gzip"), "application/x-bzip", "application/x-xz", "application/zstd" (since 5.82) "application/x-lzip" (since 6.15) Do not use application/x-compressed-tar or similar - you only need to specify the compression layer ! If the mimetype is omitted, it will be determined from the filename.

### \[override virtual noexcept\] KTar::~KTar() {#dtor.KTar}

If the tar ball is still opened, then it will be closed automatically by the destructor.

### void KTar::setOrigFileName(const QByteArray &*fileName*) {#setOrigFileName}

Special function for setting the "original file name" in the gzip header, when writing a tar.gz file. It appears when using in the "file" command, for instance. Should only be called if the underlying device is a [KCompressionDevice](kcompressiondevice.md)!

`fileName` the original file name
