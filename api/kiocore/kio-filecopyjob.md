---
title: "KIO::FileCopyJob Class"
description: "Network transparent access to files and data."
---

# KIO::FileCopyJob Class

Network transparent access to files and data. [More...](#details)

- **Header:** `#include <KIO/FileCopyJob>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS KIO)`  
  `target_link_libraries(mytarget PRIVATE KF6::KIOCore)`
- **Inherits:** [KIO::Job](kio-job.md)

[List of all members, including inherited members](kio-filecopyjob-members.md)

## Public Functions

- [QUrl destUrl() const](#destUrl)
- [void setModificationTime(const QDateTime &mtime)](#setModificationTime)
- [void setSourceSize(KIO::filesize\_t size)](#setSourceSize)
- [QUrl srcUrl() const](#srcUrl)

## Public Slots

- [void slotResult(KJob \*job)](#slotResult)

## Signals

- [void mimeTypeFound(KIO::Job \*job, const QString &mimeType)](#mimeTypeFound)

## Detailed Description {#details}

The [FileCopyJob](kio-filecopyjob.md) copies data from one place to another.

*See also* [KIO::file\_copy()](kio-index.md), [KIO::file\_move()](kio-index.md)

## Member Function Documentation {#member-function-documentation}

### QUrl FileCopyJob::destUrl() const {#destUrl}

Returns the destination URL

### \[signal\] void FileCopyJob::mimeTypeFound(KIO::Job \**job*, const QString &*mimeType*) {#mimeTypeFound}

MIME type determined during a file copy. This is never emitted during a move, and might not be emitted during a file copy, depending on the worker. But when a get and a put are being used (which is the common case), this signal forwards the MIME type information from the get job.

`job` the job that emitted this signal

`mimeType` the MIME type

### void FileCopyJob::setModificationTime(const QDateTime &*mtime*) {#setModificationTime}

Sets the modification time of the file

Note that this is ignored if a direct copy ([WorkerBase::copy](kio-workerbase.md#copy)) can be done, in which case the mtime of the source is applied to the destination (if the protocol supports the concept).

### void FileCopyJob::setSourceSize(KIO::filesize\_t *size*) {#setSourceSize}

If you know the size of the source file, call this method to inform this job. It will be displayed in the "resume" dialog.

`size` the size of the source file

### \[override virtual protected slot\] void FileCopyJob::slotResult(KJob \**job*) {#slotResult}

Reimplements: [KCompositeJob::slotResult(KJob \*job)](../kcoreaddons/kcompositejob.md#slotResult).

Called whenever a subjob finishes.

`job` the job that emitted this signal

### QUrl FileCopyJob::srcUrl() const {#srcUrl}

Returns the source URL

## Related Non-Members {#related-non-members}

### KIO::FileCopyJob \*file\_copy(const QUrl &*src*, const QUrl &*dest*, KIO::JobFlags *flags*) {#file_copy}

Overload for catching code mistakes. Do NOT call this method (it is not implemented), insert a value for permissions (-1 by default) before the [JobFlags](kio.md#JobFlag-enum).

### KIO::FileCopyJob \*file\_copy(const QUrl &*src*, const QUrl &*dest*, int *permissions* = -1, KIO::JobFlags *flags* = DefaultFlags) {#file_copy-1}

Copy a single file.

Uses either [WorkerBase::copy](kio-workerbase.md#copy)() if the worker supports that or [get](kio-transferjob.md#get)() and [put](kio-transferjob.md#put)() otherwise.

`src` Where to get the file

`dest` Where to put the file

`permissions` the file mode permissions to set on `dest`; if this is -1 (the default) no special permissions will be set on `dest`, i.e. it'll have the default system permissions for newly created files, and the owner and group permissions are not preserved.

`flags` Can be [JobFlag::HideProgressInfo](kio.md#JobFlag-enum), Overwrite and Resume here WARNING: Setting [JobFlag::Resume](kio.md#JobFlag-enum) means that the data will be appended to `dest` if `dest` exists

Returns the job handling the operation

### KIO::FileCopyJob \*file\_move(const QUrl &*src*, const QUrl &*dest*, int *permissions* = -1, KIO::JobFlags *flags* = DefaultFlags) {#file_move}

Move a single file.

Use either [WorkerBase::rename](kio-workerbase.md#rename)() if the worker supports that, or [copy](kio-copyjob.md#copy)() and [del](kio-deletejob.md#del)() otherwise, or eventually [get](kio-transferjob.md#get)() & [put](kio-transferjob.md#put)() & [del](kio-deletejob.md#del)()

`src` Where to get the file

`dest` Where to put the file

`permissions` the file mode permissions to set on `dest`; if this is -1 (the default), no special permissions are set on `dest`, i.e. it'll have the default system permissions for newly created files, and the owner and group permissions are not preserved.

`flags` Can be [HideProgressInfo](kio.md#JobFlag-enum), Overwrite and Resume here WARNING: Setting [JobFlag::Resume](kio.md#JobFlag-enum) means that the data will be appended to `dest` if `dest` exists

Returns the job handling the operation
