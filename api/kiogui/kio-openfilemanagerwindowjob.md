---
title: "KIO::OpenFileManagerWindowJob Class"
description: "Open a File Manager Window."
---

# KIO::OpenFileManagerWindowJob Class

Open a File Manager Window. [More...](#details)

- **Header:** `#include <KIO/OpenFileManagerWindowJob>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS KIO)`  
  `target_link_libraries(mytarget PRIVATE KIOGui)`
- **Inherits:** [KJob](../kcoreaddons/kjob.md)

[List of all members, including inherited members](kio-openfilemanagerwindowjob-members.md)

## Public Types

- [enum OpenFileManagerWindowJob::Errors](#Errors-enum)

## Public Functions

- [OpenFileManagerWindowJob(QObject \*parent = nullptr)](#OpenFileManagerWindowJob)
- [QList\<QUrl\> highlightUrls() const](#highlightUrls)
- [void setHighlightUrls(const QList\<QUrl\> &highlightUrls)](#setHighlightUrls)
- [void setStartupId(const QByteArray &startupId)](#setStartupId)
- [void start()](#start)
- [QByteArray startupId() const](#startupId)

## Detailed Description {#details}

Using this job you can open a file manager window and highlight specific files within a folder. This can be useful if you downloaded a file and want to present it to the user without the user having to manually search the file in its parent folder. This can also be used for a "Show in Parent Folder" functionality.

On Linux, this job will use the org.freedesktop.FileManager1 interface to highlight the files and/or folders. If this fails, the parent directory of the first URL will be opened in the default file manager instead.

Note that this job is really only about highlighting certain items which means if you, for example, pass it just a URL to a folder it will not open this particular folder but instead highlight it within its parent folder.

If you just want to open a folder, use [OpenUrlJob](kio-openurljob.md) instead.

## Member Type Documentation {#member-type-documentation}

### enum OpenFileManagerWindowJob::Errors {#Errors-enum}

Errors the job may emit

| Constant | Value | Description |
| --- | --- | --- |
| `KIO::OpenFileManagerWindowJob::NoValidUrlsError` | `KJob::UserDefinedError` | No valid URLs to highlight have been specified |
| `KIO::OpenFileManagerWindowJob::LaunchFailedError` | `101` | Failed to launch the file manager |

## Member Function Documentation {#member-function-documentation}

### \[explicit\] OpenFileManagerWindowJob::OpenFileManagerWindowJob(QObject \**parent* = nullptr) {#OpenFileManagerWindowJob}

Creates an [OpenFileManagerWindowJob](kio-openfilemanagerwindowjob.md)

### QList\<QUrl\> OpenFileManagerWindowJob::highlightUrls() const {#highlightUrls}

The files and/or folders to highlight

*See also* [setHighlightUrls](kio-openfilemanagerwindowjob.md#setHighlightUrls)()

### void OpenFileManagerWindowJob::setHighlightUrls(const QList\<QUrl\> &*highlightUrls*) {#setHighlightUrls}

Set the files and/or folders to highlight

*See also* [highlightUrls](kio-openfilemanagerwindowjob.md#highlightUrls)()

### void OpenFileManagerWindowJob::setStartupId(const QByteArray &*startupId*) {#setStartupId}

Sets the platform-specific startup id of the file manager launch.

`startupId` startup id, if any (otherwise "").

For X11, this would be the id for the Startup Notification protocol.

*See also* [startupId](kio-openfilemanagerwindowjob.md#startupId)()

### \[override virtual\] void OpenFileManagerWindowJob::start() {#start}

Reimplements: [KJob::start()](../kcoreaddons/kjob.md#start).

Starts the job

### QByteArray OpenFileManagerWindowJob::startupId() const {#startupId}

The Startup ID

*See also* [setStartupId](kio-openfilemanagerwindowjob.md#setStartupId)()

## Related Non-Members {#related-non-members}

### KIO::OpenFileManagerWindowJob \*highlightInFileManager(const QList\<QUrl\> &*urls*, const QByteArray &*asn* = QByteArray()) {#highlightInFileManager}

Convenience method for creating a job to highlight a certain file or folder.

It will create a job for a given URL(s) and automatically start it.
