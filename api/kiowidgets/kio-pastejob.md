---
title: "KIO::PasteJob Class"
description: "A KIO job that handles pasting the clipboard contents."
---

# KIO::PasteJob Class

A KIO job that handles pasting the clipboard contents. [More...](#details)

- **Header:** `#include <KIO/PasteJob>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS KIO)`  
  `target_link_libraries(mytarget PRIVATE KF6::KIOWidgets)`
- **Inherits:** [KIO::Job](../kiocore/kio-job.md)

[List of all members, including inherited members](kio-pastejob-members.md)

## Signals

- [void copyJobStarted(KIO::CopyJob \*job)](#copyJobStarted) (since 6.0)
- [void itemCreated(const QUrl &url)](#itemCreated)

## Detailed Description {#details}

If the clipboard contains URLs, they are copied to the destination URL. If the clipboard contains data, it is saved into a file after asking the user to choose a filename and the preferred data format.

*See also* [KIO::paste](kio-pastejob.md#paste)

## Member Function Documentation {#member-function-documentation}

### \[signal, since 6.0\] void PasteJob::copyJobStarted(KIO::CopyJob \**job*) {#copyJobStarted}

Emitted when a copy job was started as subjob as part of pasting. Note that a CopyJob isn't always started by [PasteJob](kio-pastejob.md). For instance pasting image content will create a file.

You can use `job` to monitor the progress of the copy/move/link operation.

`job` the job started for moving, copying or symlinking files

This function was introduced in Qt 6.0.

### \[signal\] void PasteJob::itemCreated(const QUrl &*url*) {#itemCreated}

Signals that a file or directory was created.

## Related Non-Members {#related-non-members}

### KIO::PasteJob \*paste(const QMimeData \**mimeData*, const QUrl &*destDir*, KIO::JobFlags *flags* = DefaultFlags) {#paste}

Pastes the clipboard contents.

If the clipboard contains URLs, they are copied (or moved) to the destination URL, using a [KIO::CopyJob](../kiocore/kio-copyjob.md) subjob. Otherwise, the data from the clipboard is saved into a file using [KIO::storedPut](../kiocore/kio-storedtransferjob.md#storedPut), after asking the user to choose a filename and the preferred data format.

This takes care of recording the subjob in the [FileUndoManager](kio-fileundomanager.md), and emits [itemCreated](kio-pastejob.md#itemCreated) for every file or directory being created, so that the view can select these items.

`mimeData` the MIME data to paste, usually [QApplication::clipboard](https://doc.qt.io/qt-6/qguiapplication.html#clipboard)()-\>mimeData()

`destDir` The URL of the target directory

`flags` passed to the sub job

Returns a pointer to the job handling the operation.
