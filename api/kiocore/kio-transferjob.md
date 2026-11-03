---
title: "KIO::TransferJob Class"
description: "The transfer job pumps data into and/or out of a KIO worker."
---

# KIO::TransferJob Class

The transfer job pumps data into and/or out of a KIO worker. [More...](#details)

- **Header:** `#include <KIO/TransferJob>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS KIO)`  
  `target_link_libraries(mytarget PRIVATE KF6::KIOCore)`
- **Inherits:** [KIO::SimpleJob](kio-simplejob.md)
- **Inherited By:** [KIO::DavJob](kio-davjob.md), [KIO::MimetypeJob](kio-mimetypejob.md), [KIO::SpecialJob](kio-specialjob.md), and [KIO::StoredTransferJob](kio-storedtransferjob.md)

[List of all members, including inherited members](kio-transferjob-members.md)  
[Deprecated members](kio-transferjob-obsolete.md)

## Public Functions

- [QString mimetype() const](#mimetype)
- [QUrl redirectUrl() const](#redirectUrl)
- [void sendAsyncData(const QByteArray &data)](#sendAsyncData)
- [void setAsyncDataEnabled(bool enabled)](#setAsyncDataEnabled)
- [void setModificationTime(const QDateTime &mtime)](#setModificationTime)
- [void setSourceSize(KIO::filesize\_t size)](#setSourceSize) (since 6.25)
- [void setTotalSize(KIO::filesize\_t bytes)](#setTotalSize)

## Public Slots

- [void slotData(const QByteArray &data)](#slotData)
- [void slotDataReq()](#slotDataReq)
- [void slotMimetype(const QString &mimetype)](#slotMimetype)
- [void slotRedirection(const QUrl &url)](#slotRedirection)

## Signals

- [void data(KIO::Job \*job, const QByteArray &data)](#data)
- [void dataReq(KIO::Job \*job, QByteArray &data)](#dataReq)
- [void mimeTypeFound(KIO::Job \*job, const QString &mimeType)](#mimeTypeFound)
- [void permanentRedirection(KIO::Job \*job, const QUrl &fromUrl, const QUrl &toUrl)](#permanentRedirection)
- [void redirection(KIO::Job \*job, const QUrl &url)](#redirection)

## Detailed Description {#details}

Data is sent to the worker on request of the worker ( [dataReq](kio-transferjob.md#dataReq)). If data coming from the worker can not be handled, the reading of data from the worker should be suspended.

## Member Function Documentation {#member-function-documentation}

### \[signal\] void TransferJob::data(KIO::Job \**job*, const QByteArray &*data*) {#data}

Data from the worker has arrived.

`job` the job that emitted this signal

`data` data received from the worker.

End of data (EOD) has been reached if data.size() == 0, however, you should not be certain of data.size() == 0 ever happening (e.g. in case of an error), so you should rely on [result](../kcoreaddons/kjob.md#result)() instead.

### \[signal\] void TransferJob::dataReq(KIO::Job \**job*, QByteArray &*data*) {#dataReq}

Request for data.

Please note, that you shouldn't put too large chunks of data in it as this requires copies within the frame work, so you should rather split the data you want to pass here in reasonable chunks (about 1MB maximum)

`job` the job that emitted this signal

`data` buffer to fill with data to send to the worker. An empty buffer indicates end of data. (EOD)

### \[signal\] void TransferJob::mimeTypeFound(KIO::Job \**job*, const QString &*mimeType*) {#mimeTypeFound}

MIME type determined.

`job` the job that emitted this signal

`mimeType` the MIME type

### QString TransferJob::mimetype() const {#mimetype}

Call this in the slot connected to result, and only after making sure no error happened.

Returns the MIME type of the URL

### \[signal\] void TransferJob::permanentRedirection(KIO::Job \**job*, const QUrl &*fromUrl*, const QUrl &*toUrl*) {#permanentRedirection}

Signals a permanent redirection.

The redirection itself is handled internally.

`job` the job that emitted this signal

`fromUrl` the original URL

`toUrl` the new URL

### QUrl TransferJob::redirectUrl() const {#redirectUrl}

After the job has finished, it will return the final url in case a redirection has happened.

Returns the final url that can be empty in case no redirection has happened.

### \[signal\] void TransferJob::redirection(KIO::Job \**job*, const QUrl &*url*) {#redirection}

Signals a redirection.

Use to update the URL shown to the user. The redirection itself is handled internally.

`job` the job that emitted this signal

`url` the new URL

### void TransferJob::sendAsyncData(const QByteArray &*data*) {#sendAsyncData}

Provide data to the job when async data is enabled. Should be called exactly once after receiving a [dataReq](kio-transferjob.md#dataReq) signal Sending an empty block indicates end of data.

### void TransferJob::setAsyncDataEnabled(bool *enabled*) {#setAsyncDataEnabled}

Enable the async data mode. When async data is enabled, data should be provided to the job by calling [sendAsyncData](kio-transferjob.md#sendAsyncData)() instead of returning data in the [dataReq](kio-transferjob.md#dataReq)() signal.

### void TransferJob::setModificationTime(const QDateTime &*mtime*) {#setModificationTime}

Sets the modification time of the file to be created (by [KIO::put](kio-transferjob.md#put)) Note that some KIO workers might ignore this.

### \[since 6.25\] void TransferJob::setSourceSize(KIO::filesize\_t *size*) {#setSourceSize}

Sets the source file size for put operations. Workers can use this to optimize upload strategy (e.g. multipart chunk size).

This function was introduced in Qt 6.25.

### void TransferJob::setTotalSize(KIO::filesize\_t *bytes*) {#setTotalSize}

Set the total size of data that we are going to send in a put job. Helps getting proper progress information.

### \[virtual protected slot\] void TransferJob::slotData(const QByteArray &*data*) {#slotData}

### \[virtual protected slot\] void TransferJob::slotDataReq() {#slotDataReq}

### \[virtual protected slot\] void TransferJob::slotMimetype(const QString &*mimetype*) {#slotMimetype}

### \[virtual protected slot\] void TransferJob::slotRedirection(const QUrl &*url*) {#slotRedirection}

## Related Non-Members {#related-non-members}

### KIO::TransferJob \*get(const QUrl &*url*, KIO::LoadType *reload* = NoReload, KIO::JobFlags *flags* = DefaultFlags) {#get}

Get (means: read). This is the job to use in order to "download" a file into memory. The worker emits the data through the [data](kio-transferjob.md#data)() signal.

Special case: if you want to determine the MIME type of the file first, and then read it with the appropriate component, you can still use a KIO::get() directly. When that job emits the mimeType signal, (which is guaranteed to happen before it emits any data), put the job on hold:

```cpp
job->putOnHold();
```

and forget about the job. The next time someone does a KIO::get() on the same URL (even in another process) this job will be resumed. This saves KIO from doing two requests to the server.

`url` the URL of the file

`reload` Reload to reload the file, [NoReload](kio.md#LoadType-enum) if it can be taken from the cache

`flags` Can be [HideProgressInfo](kio.md#JobFlag-enum) here

Returns the job handling the operation.

### KIO::TransferJob \*http\_delete(const QUrl &*url*, KIO::JobFlags *flags* = DefaultFlags) {#http_delete}

HTTP DELETE.

Though this function servers the same purpose as [KIO::file\_delete](kio-simplejob.md#file_delete), unlike [file\_delete](kio-simplejob.md#file_delete) it accommodates HTTP specific actions such as redirections.

`url` url resource to delete.

`flags` Can be [HideProgressInfo](kio.md#JobFlag-enum) here

Returns the job handling the operation.

### KIO::TransferJob \*http\_post(const QUrl &*url*, const QByteArray &*postData*, KIO::JobFlags *flags* = DefaultFlags) {#http_post}

HTTP POST (for form data).

Example:

```cpp
job = KIO::http_post( url, postData, KIO::HideProgressInfo );
job->addMetaData("content-type", contentType );
```

`postData` is the data that you want to send and

`contentType` is the complete HTTP header line that specifies the content's MIME type, for example "Content-Type: text/xml".

You MUST specify content-type!

Often `contentType` is "Content-Type: application/x-www-form-urlencoded" and the `postData` is then an ASCII string (without null-termination!) with characters like space, linefeed and percent escaped like %20, %0A and %25.

`url` Where to write the data.

`postData` Encoded data to post.

`flags` Can be [HideProgressInfo](kio.md#JobFlag-enum) here

Returns the job handling the operation.

### KIO::TransferJob \*http\_post(const QUrl &*url*, QIODevice \**device*, qint64 *size* = -1, KIO::JobFlags *flags* = DefaultFlags) {#http_post-1}

HTTP POST.

This function, unlike the one that accepts a [QByteArray](https://doc.qt.io/qt-6/qbytearray.html), accepts an IO device from which to read the encoded data to be posted to the server in order to to avoid holding the content of very large post requests, e.g. multimedia file uploads, in memory.

`url` Where to write the data.

`device` the device to read from

`size` Size of the encoded post data.

`flags` Can be [HideProgressInfo](kio.md#JobFlag-enum) here

Returns the job handling the operation.

### KIO::TransferJob \*put(const QUrl &*url*, int *permissions*, KIO::JobFlags *flags* = DefaultFlags) {#put}

Put (means: write)

`url` Where to write data.

`permissions` May be -1. In this case no special permission mode is set.

`flags` Can be [HideProgressInfo](kio.md#JobFlag-enum), Overwrite and Resume here.

> **Warning:** Setting Resume means that the data will be appended to `url` if `url` exists.

Returns the job handling the operation.
