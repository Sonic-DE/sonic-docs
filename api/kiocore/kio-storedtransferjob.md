---
title: "KIO::StoredTransferJob Class"
description: "StoredTransferJob is a TransferJob (for downloading or uploading data) that also stores a QByteArray with the data, making it simpler to use than the standard TransferJob."
---

# KIO::StoredTransferJob Class

[StoredTransferJob](kio-storedtransferjob.md) is a [TransferJob](kio-transferjob.md) (for downloading or uploading data) that also stores a [QByteArray](https://doc.qt.io/qt-6/qbytearray.html) with the data, making it simpler to use than the standard [TransferJob](kio-transferjob.md). [More...](#details)

- **Header:** `#include <KIO/StoredTransferJob>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS KIO)`  
  `target_link_libraries(mytarget PRIVATE KF6::KIOCore)`
- **Inherits:** [KIO::TransferJob](kio-transferjob.md)

[List of all members, including inherited members](kio-storedtransferjob-members.md)

## Public Functions

- [QByteArray data() const](#data)
- [void setData(const QByteArray &arr)](#setData)

## Detailed Description {#details}

For [KIO::storedGet](kio-storedtransferjob.md#storedGet) it puts the data into the member [QByteArray](https://doc.qt.io/qt-6/qbytearray.html), so the user of this class can get hold of the whole data at once by calling [data](kio-storedtransferjob.md#data)() when the result signal is emitted. You should only use [StoredTransferJob](kio-storedtransferjob.md) to download data if you cannot process the data by chunks while it's being downloaded, since storing everything in a [QByteArray](https://doc.qt.io/qt-6/qbytearray.html) can potentially require a lot of memory.

For [KIO::storedPut](kio-storedtransferjob.md#storedPut) the user of this class simply provides the bytearray from the start, and the job takes care of uploading it. You should only use [StoredTransferJob](kio-storedtransferjob.md) to upload data if you cannot provide the in chunks while it's being uploaded, since storing everything in a [QByteArray](https://doc.qt.io/qt-6/qbytearray.html) can potentially require a lot of memory.

## Member Function Documentation {#member-function-documentation}

### QByteArray StoredTransferJob::data() const {#data}

Get hold of the downloaded data. This is for get jobs. You're supposed to call this only from the slot connected to the [result](../kcoreaddons/kjob.md#result)() signal.

*See also* [setData](kio-storedtransferjob.md#setData)()

### void StoredTransferJob::setData(const QByteArray &*arr*) {#setData}

Set data to be uploaded. This is for put jobs. Automatically called by [KIO::storedPut](kio-storedtransferjob.md#storedPut)(const [QByteArray](https://doc.qt.io/qt-6/qbytearray.html) &, ...), do not call this yourself.

*See also* [data](kio-storedtransferjob.md#data)()

## Related Non-Members {#related-non-members}

### KIO::StoredTransferJob \*storedGet(const QUrl &*url*, KIO::LoadType *reload* = NoReload, KIO::JobFlags *flags* = DefaultFlags) {#storedGet}

Get (means: read), into a single [QByteArray](https://doc.qt.io/qt-6/qbytearray.html).

`url` the URL of the file

`reload` Reload to reload the file, [NoReload](kio.md#LoadType-enum) if it can be taken from the cache

`flags` Can be [HideProgressInfo](kio.md#JobFlag-enum) here

Returns the job handling the operation.

### KIO::StoredTransferJob \*storedHttpPost(const QByteArray &*arr*, const QUrl &*url*, KIO::JobFlags *flags* = DefaultFlags) {#storedHttpPost}

HTTP POST (means: write) data from a single [QByteArray](https://doc.qt.io/qt-6/qbytearray.html).

`arr` The data to write

`url` Where to write data.

`flags` Can be [HideProgressInfo](kio.md#JobFlag-enum) here.

Returns the job handling the operation.

### KIO::StoredTransferJob \*storedHttpPost(QIODevice \**device*, const QUrl &*url*, qint64 *size* = -1, KIO::JobFlags *flags* = DefaultFlags) {#storedHttpPost-1}

HTTP POST (means: write) data from the given IO device.

`device` Device from which the encoded data to be posted is read. Must be open for reading.

`url` Where to write data.

`size` Size of the encoded data to be posted.

`flags` Can be [HideProgressInfo](kio.md#JobFlag-enum) here.

Returns the job handling the operation.

### KIO::StoredTransferJob \*storedPut(QIODevice \**input*, const QUrl &*url*, int *permissions*, KIO::JobFlags *flags* = DefaultFlags) {#storedPut}

Put (means: write) data from a [QIODevice](https://doc.qt.io/qt-6/qiodevice.html).

`input` The data to write, a device to read from. Must be open for reading (data will be read from the current position).

`url` Where to write data.

`permissions` May be -1. In this case no special permission mode is set.

`flags` Can be [HideProgressInfo](kio.md#JobFlag-enum), Overwrite and Resume here. WARNING: Setting Resume means that the data will be appended to `dest` if `dest` exists.

Returns the job handling the operation.

### KIO::StoredTransferJob \*storedPut(const QByteArray &*arr*, const QUrl &*url*, int *permissions*, KIO::JobFlags *flags* = DefaultFlags) {#storedPut-1}

Put (means: write) data from a single [QByteArray](https://doc.qt.io/qt-6/qbytearray.html).

`arr` The data to write

`url` Where to write data.

`permissions` May be -1. In this case no special permission mode is set.

`flags` Can be [HideProgressInfo](kio.md#JobFlag-enum), Overwrite and Resume here. WARNING: Setting Resume means that the data will be appended to `url` if `url` exists.

Returns the job handling the operation.
