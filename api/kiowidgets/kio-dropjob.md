---
title: "KIO::DropJob Class"
description: "A KIO job that handles dropping into a file-manager-like view."
---

# KIO::DropJob Class

A KIO job that handles dropping into a file-manager-like view. [More...](#details)

- **Header:** `#include <KIO/DropJob>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS KIO)`  
  `target_link_libraries(mytarget PRIVATE KF6::KIOWidgets)`
- **Inherits:** [KIO::Job](../kiocore/kio-job.md)

[List of all members, including inherited members](kio-dropjob-members.md)

## Public Functions

- [void setApplicationActions(const QList\<QAction \*\> &actions)](#setApplicationActions)
- [void showMenu(const QPoint &p, QAction \*atAction = nullptr)](#showMenu)

## Signals

- [void copyJobStarted(KIO::CopyJob \*job)](#copyJobStarted)
- [void itemCreated(const QUrl &url)](#itemCreated)
- [void popupMenuAboutToShow(const KFileItemListProperties &itemProps)](#popupMenuAboutToShow)

## Detailed Description {#details}

The popupmenu that can appear on drop, can be customized with plugins, see [KIO::DndPopupMenuPlugin](../kiogui/kio-dndpopupmenuplugin.md).

*See also* [KIO::drop](kio-dropjob.md#drop)

## Member Function Documentation {#member-function-documentation}

### \[signal\] void DropJob::copyJobStarted(KIO::CopyJob \**job*) {#copyJobStarted}

Emitted when a copy job was started as subjob after user selection.

You can use `job` to monitor the progress of the copy/move/link operation. Note that a CopyJob isn't always started by [DropJob](kio-dropjob.md). For instance dropping files onto an executable will simply launch the executable.

`job` the job started for moving, copying or symlinking files

### \[signal\] void DropJob::itemCreated(const QUrl &*url*) {#itemCreated}

Signals that a file or directory was created.

### \[signal\] void DropJob::popupMenuAboutToShow(const KFileItemListProperties &*itemProps*) {#popupMenuAboutToShow}

Signals that the popup menu is about to be shown. Applications can use the information provided about the dropped URLs (e.g. the MIME type) to decide whether to call [setApplicationActions](kio-dropjob.md#setApplicationActions).

`itemProps` properties of the dropped items

### void DropJob::setApplicationActions(const QList\<QAction \*\> &*actions*) {#setApplicationActions}

Allows the application to set additional actions in the drop popup menu. For instance, the application handling the desktop might want to add "set as wallpaper" if the dropped url is an image file. This can be called upfront, or for convenience, when [popupMenuAboutToShow](kio-dropjob.md#popupMenuAboutToShow) is emitted.

### void DropJob::showMenu(const QPoint &*p*, QAction \**atAction* = nullptr) {#showMenu}

Allows the application to show the menu manually. [DropJob](kio-dropjob.md) instance has to be created with the [KIO::ShowMenuManually](kio-sub-kiowidgets.md#DropJobFlag-enum) flag

## Related Non-Members {#related-non-members}

### KIO::DropJob \*drop(const QDropEvent \**dropEvent*, const QUrl &*destUrl*, KIO::JobFlags *flags* = DefaultFlags) {#drop}

Drops the clipboard contents.

If the mime data contains URLs, a popup appears to choose between Move, Copy, Link and Cancel which is then implemented by the job, using [KIO::move](../kiocore/kio-copyjob.md#move), [KIO::copy](../kiocore/kio-copyjob.md#copy) or [KIO::link](../kiocore/kio-copyjob.md#link) Additional actions provided by the application or by plugins can be shown in the popup.

If the mime data contains data other than URLs, it is saved into a file after asking the user to choose a filename and the preferred data format.

This job takes care of recording the subjob in the [FileUndoManager](kio-fileundomanager.md), and emits [itemCreated](kio-dropjob.md#itemCreated) for every file or directory being created, so that the view can select these items.

`dropEvent` the drop event, from which the job will extract mimeData, dropAction, etc. The application should take care of calling dropEvent-\>acceptProposedAction().

`destUrl` The URL of the target file or directory

`flags` passed to the sub job

Returns A pointer to the job handling the operation.

> **Warning:** Don't forget to call KJobWidgets::setWindow() on this job, otherwise the popup menu won't be properly positioned with Wayland compositors.

### KIO::DropJob \*drop(const QDropEvent \**dropEvent*, const QUrl &*destUrl*, KIO::DropJobFlags *dropjobFlags*, KIO::JobFlags *flags* = DefaultFlags) {#drop-1}

Similar to [KIO::drop](kio-dropjob.md#drop)

`dropEvent` the drop event, from which the job will extract mimeData, dropAction, etc. The application should take care of calling dropEvent-\>acceptProposedAction().

`destUrl` The URL of the target file or directory

`dropjobFlags` Show the menu immediately or manually.

`flags` passed to the sub job

Returns A pointer to the job handling the operation.

> **Warning:** Don't forget to call [DropJob::showMenu](kio-dropjob.md#showMenu) on this job, otherwise the popup will never be shown
