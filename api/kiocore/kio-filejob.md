---
title: "KIO::FileJob Class"
description: "Network transparent access to files and data."
---

# KIO::FileJob Class

Network transparent access to files and data. [More...](#details)

- **Header:** `#include <KIO/FileJob>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS KIO)`  
  `target_link_libraries(mytarget PRIVATE KF6::KIOCore)`
- **Inherits:** [KIO::SimpleJob](kio-simplejob.md)

[List of all members, including inherited members](kio-filejob-members.md)

## Public Functions

- [void close()](#close)
- [void read(KIO::filesize\_t size)](#read)
- [void seek(KIO::filesize\_t offset)](#seek)
- [KIO::filesize\_t size()](#size)
- [void truncate(KIO::filesize\_t length)](#truncate)
- [void write(const QByteArray &data)](#write)

## Signals

- [void data(KIO::Job \*job, const QByteArray &data)](#data)
- [void fileClosed(KIO::Job \*job)](#fileClosed)
- [void mimeTypeFound(KIO::Job \*job, const QString &mimeType)](#mimeTypeFound)
- [void open(KIO::Job \*job)](#open)
- [void position(KIO::Job \*job, KIO::filesize\_t offset)](#position)
- [void redirection(KIO::Job \*job, const QUrl &url)](#redirection)
- [void truncated(KIO::Job \*job, KIO::filesize\_t length)](#truncated)
- [void written(KIO::Job \*job, KIO::filesize\_t written)](#written)

## Detailed Description {#details}

The file-job is an asynchronous version of normal file handling. It allows block-wise reading and writing, and allows seeking and truncation. Results are returned through signals.

Should always be created using [KIO::open](kio-filejob.md#open-1)(const [QUrl](https://doc.qt.io/qt-6/qurl.html)&, QIODevice::OpenMode).

## Member Function Documentation {#member-function-documentation}

### void FileJob::close() {#close}

Closes the file KIO worker.

The worker emits close() and [result](../kcoreaddons/kjob.md#result)().

### \[signal\] void FileJob::data(KIO::Job \**job*, const QByteArray &*data*) {#data}

Data from the worker has arrived. Emitted after [read](kio-filejob.md#read)().

Unless a [read](kio-filejob.md#read)() request was sent for 0 bytes, End of data (EOD) has been reached if data.[size](kio-filejob.md#size)() == 0

`job` the job that emitted this signal

`data` data received from the worker.

### \[signal\] void FileJob::fileClosed(KIO::Job \**job*) {#fileClosed}

Signals that the file is closed and will accept no more commands.

`job` the job that emitted this signal

### \[signal\] void FileJob::mimeTypeFound(KIO::Job \**job*, const QString &*mimeType*) {#mimeTypeFound}

MIME type determined.

`job` the job that emitted this signal

`mimeType` the MIME type

### \[signal\] void FileJob::open(KIO::Job \**job*) {#open}

File is open, metadata has been determined and the file KIO worker is ready to receive commands.

`job` the job that emitted this signal

> **Note:** This signal is overloaded. To connect to this signal:
>
> ```
> // Connect using qOverload:
> connect(fileJob, qOverload<KIO::Job *>(&FileJob::open),
>         receiver, &ReceiverClass::slot);
>
> // Or using a lambda:
> connect(fileJob, qOverload<KIO::Job *>(&FileJob::open),
>         this, [](KIO::Job *job) { /* handle open */ });
> ```
>
> For more examples and approaches, see [connecting to overloaded signals](https://doc.qt.io/qt-6/signalsandslots.html#connecting-overloaded-signals).

### \[signal\] void FileJob::position(KIO::Job \**job*, KIO::filesize\_t *offset*) {#position}

The file has reached this position. Emitted after [seek](kio-filejob.md#seek)().

`job` the job that emitted this signal

`offset` the new position

### void FileJob::read(KIO::filesize\_t *size*) {#read}

This function attempts to read up to `size` bytes from the URL passed to [KIO::open](kio-filejob.md#open-1)() and returns the bytes received via the [data](kio-filejob.md#data)() signal.

The read operation commences at the current file offset, and the file offset is incremented by the number of bytes read, but this change in the offset does not result in the [position](kio-filejob.md#position)() signal being emitted.

If the current file offset is at or past the end of file (i.e. EOD), no bytes are read, and the [data](kio-filejob.md#data)() signal returns an empty [QByteArray](https://doc.qt.io/qt-6/qbytearray.html).

On error the [data](kio-filejob.md#data)() signal is not emitted. To catch errors please connect to the [result](../kcoreaddons/kjob.md#result)() signal.

### \[signal\] void FileJob::redirection(KIO::Job \**job*, const QUrl &*url*) {#redirection}

Signals the file is a redirection. Follow this url manually to reach data

`job` the job that emitted this signal

`url` the new URL

### void FileJob::seek(KIO::filesize\_t *offset*) {#seek}

Seek

The worker emits [position](kio-filejob.md#position)() on successful seek to the specified `offset`.

On error the [position](kio-filejob.md#position)() signal is not emitted. To catch errors please connect to the [result](../kcoreaddons/kjob.md#result)() signal.

### KIO::filesize\_t FileJob::size() {#size}

Returns the file size

### void FileJob::truncate(KIO::filesize\_t *length*) {#truncate}

Truncate

The worker emits [truncated](kio-filejob.md#truncated)() on successful truncation to the specified `length`.

On error the [truncated](kio-filejob.md#truncated)() signal is not emitted. To catch errors please connect to the [result](../kcoreaddons/kjob.md#result)() signal.

### \[signal\] void FileJob::truncated(KIO::Job \**job*, KIO::filesize\_t *length*) {#truncated}

The file has been truncated to this point. Emitted after [truncate](kio-filejob.md#truncate)().

`job` the job that emitted this signal

`length` the new length of the file

### void FileJob::write(const QByteArray &*data*) {#write}

This function attempts to write all the bytes in `data` to the URL passed to [KIO::open](kio-filejob.md#open-1)() and returns the bytes written received via the [written](kio-filejob.md#written)() signal.

The write operation commences at the current file offset, and the file offset is incremented by the number of bytes read, but this change in the offset does not result in the [position](kio-filejob.md#position)() being emitted.

On error the [written](kio-filejob.md#written)() signal is not emitted. To catch errors please connect to the [result](../kcoreaddons/kjob.md#result)() signal.

### \[signal\] void FileJob::written(KIO::Job \**job*, KIO::filesize\_t *written*) {#written}

`written` bytes were written to the file. Emitted after [write](kio-filejob.md#write)().

`job` the job that emitted this signal

`written` bytes written.

## Related Non-Members {#related-non-members}

### KIO::FileJob \*open(const QUrl &*url*, QIODevice::OpenMode *mode*) {#open-1}

Open ( random access I/O )

The file-job emits [open](kio-filejob.md#open)() when opened

On error the [open](kio-filejob.md#open)() signal is not emitted. To catch errors please connect to the [result](../kcoreaddons/kjob.md#result)() signal.

`url` the URL of the file

`mode` the access privileges: see OpenMode

Returns the file-handling job. It will never return 0. Errors are handled asynchronously (emitted as signals).
