---
title: "KCompressionDevice Class"
description: "QIODevice for reading compressed data."
---

# KCompressionDevice Class

[QIODevice](https://doc.qt.io/qt-6/qiodevice.html) for reading compressed data. [More...](#details)

- **Header:** `#include <KCompressionDevice>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS Archive)`  
  `target_link_libraries(mytarget PRIVATE KF6::Archive)`
- **Inherits:** [QIODevice](https://doc.qt.io/qt-6/qiodevice.html)

[List of all members, including inherited members](kcompressiondevice-members.md)

## Public Types

- [enum KCompressionDevice::CompressionType](#CompressionType-enum)

## Public Functions

- [KCompressionDevice(const QString &fileName)](#KCompressionDevice)
- [KCompressionDevice(const QString &fileName, KCompressionDevice::CompressionType type)](#KCompressionDevice-1)
- [KCompressionDevice(QIODevice \*inputDevice, bool autoDeleteInputDevice, KCompressionDevice::CompressionType type)](#KCompressionDevice-2)
- [KCompressionDevice(std::unique\_ptr\<QIODevice\> inputDevice, KCompressionDevice::CompressionType type, std::optional\<qint64\> size = {})](#KCompressionDevice-3) (since 6.16)
- [~KCompressionDevice()](#dtor.KCompressionDevice)
- [KCompressionDevice::CompressionType compressionType() const](#compressionType)
- [QFileDevice::FileError error() const](#error)
- [bool seek(qint64)](#seek)
- [void setOrigFileName(const QByteArray &fileName)](#setOrigFileName)
- [void setSkipHeaders()](#setSkipHeaders)

## Static Public Members

- [KCompressionDevice::CompressionType compressionTypeForMimeType(const QString &mimetype)](#compressionTypeForMimeType)
- [KFilterBase \*filterForCompressionType(KCompressionDevice::CompressionType type)](#filterForCompressionType)

## Detailed Description {#details}

A class for reading and writing compressed data onto a device (e.g. file, but other usages are possible, like a buffer or a socket).

Use this class to read/write compressed files.

## Member Type Documentation {#member-type-documentation}

### enum KCompressionDevice::CompressionType {#CompressionType-enum}

| Constant |   |
| --- | --- |
| `KCompressionDevice::GZip` | `0` |
| `KCompressionDevice::BZip2` | `1` |
| `KCompressionDevice::Xz` | `2` |
| `KCompressionDevice::None` | `3` |
| `KCompressionDevice::Zstd (since Qt 5.82)` | `4` |
| `KCompressionDevice::Lz (since Qt 6.15)` | `5` |

## Member Function Documentation {#member-function-documentation}

### \[explicit\] KCompressionDevice::KCompressionDevice(const QString &*fileName*) {#KCompressionDevice}

Constructs a [KCompressionDevice](kcompressiondevice.md) for a given `fileName`.

`fileName` the name of the file to filter.

### KCompressionDevice::KCompressionDevice(const QString &*fileName*, KCompressionDevice::CompressionType *type*) {#KCompressionDevice-1}

Constructs a [KCompressionDevice](kcompressiondevice.md) for a given [CompressionType](kcompressiondevice.md#CompressionType-enum) (e.g. [GZip](kcompressiondevice.md#CompressionType-enum), [BZip2](kcompressiondevice.md#CompressionType-enum) etc.).

`fileName` the name of the file to filter.

`type` the [CompressionType](kcompressiondevice.md#CompressionType-enum) to use.

### KCompressionDevice::KCompressionDevice(QIODevice \**inputDevice*, bool *autoDeleteInputDevice*, KCompressionDevice::CompressionType *type*) {#KCompressionDevice-2}

Constructs a [KCompressionDevice](kcompressiondevice.md) for a given [CompressionType](kcompressiondevice.md#CompressionType-enum) (e.g. [GZip](kcompressiondevice.md#CompressionType-enum), [BZip2](kcompressiondevice.md#CompressionType-enum) etc.).

`inputDevice` input device.

`autoDeleteInputDevice` if true, `inputDevice` will be deleted automatically

`type` the [CompressionType](kcompressiondevice.md#CompressionType-enum) to use.

### \[since 6.16\] KCompressionDevice::KCompressionDevice(std::unique\_ptr\<QIODevice\> *inputDevice*, KCompressionDevice::CompressionType *type*, std::optional\<qint64\> *size* = {}) {#KCompressionDevice-3}

Constructs a [KCompressionDevice](kcompressiondevice.md) for a given [CompressionType](kcompressiondevice.md#CompressionType-enum) (e.g. [GZip](kcompressiondevice.md#CompressionType-enum), [BZip2](kcompressiondevice.md#CompressionType-enum) etc.).

`inputDevice` input device.

`type` the [CompressionType](kcompressiondevice.md#CompressionType-enum) to use.

`size` the size we know the inputDevice with [CompressionType](kcompressiondevice.md#CompressionType-enum) type has. If we know it.

This function was introduced in Qt 6.16.

### \[override virtual noexcept\] KCompressionDevice::~KCompressionDevice() {#dtor.KCompressionDevice}

Destructs the [KCompressionDevice](kcompressiondevice.md).

Calls [close](https://doc.qt.io/qt-6/qiodevice.html#close)() if the filter device is still open.

### KCompressionDevice::CompressionType KCompressionDevice::compressionType() const {#compressionType}

The compression actually used by this device.

If the support for the compression requested in the constructor is not available, then the device will use None.

### \[static\] KCompressionDevice::CompressionType KCompressionDevice::compressionTypeForMimeType(const QString &*mimetype*) {#compressionTypeForMimeType}

Returns the compression type for the given MIME type, if possible. Otherwise returns None.

This handles simple cases like application/gzip, but also application/x-compressed-tar, and inheritance.

### QFileDevice::FileError KCompressionDevice::error() const {#error}

Returns the error code from the last failing operation. This is especially useful after calling [close](https://doc.qt.io/qt-6/qiodevice.html#close)(), which unfortunately returns void (see https://bugreports.qt.io/browse/QTBUG-70033), to see if the flushing done by close was able to write all the data to disk.

### \[static\] KFilterBase \*KCompressionDevice::filterForCompressionType(KCompressionDevice::CompressionType *type*) {#filterForCompressionType}

Call this to create the appropriate filter for the [CompressionType](kcompressiondevice.md#CompressionType-enum) named `type`.

`type` the type of the compression filter

Returns the filter for the `type`, or 0 if not found

### \[override virtual\] bool KCompressionDevice::seek(*qint64*) {#seek}

Reimplements: [QIODevice::seek(qint64 pos)](https://doc.qt.io/qt-6/qiodevice.html#seek).

That one can be quite slow, when going back. Use with care.

### void KCompressionDevice::setOrigFileName(const QByteArray &*fileName*) {#setOrigFileName}

For writing gzip compressed files only: set the name of the original file, to be used in the gzip header.

`fileName` the name of the original file

### void KCompressionDevice::setSkipHeaders() {#setSkipHeaders}

Call this let this device skip the gzip headers when reading/writing. This way [KCompressionDevice](kcompressiondevice.md) (with gzip filter) can be used as a direct wrapper around zlib - this is used by [KZip](kzip.md).
