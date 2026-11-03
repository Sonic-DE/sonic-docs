---
title: "KIO Namespace"
description: "The KIO namespace includes the following elements from module KIOWidgets. The full namespace is documented in module KIOCore here.."
---

# KIO Namespace

The KIO namespace includes the following elements from module KIOWidgets. The full namespace is documented in module KIOCore here..

## Namespaces {#namespaces}

### namespace KIO::SslUi

## Classes {#classes}

### class [DeleteOrTrashJob](kio-deleteortrashjob.md)

This job asks the user for confirmation to delete or move to Trash a list of URLs; or if the job is constructed with AskUserActionInterface::EmptyTrash, to empty the Trash.

### class [DropJob](kio-dropjob.md)

A KIO job that handles dropping into a file-manager-like view.

### class [FileUndoManager](kio-fileundomanager.md)

Makes it possible to undo KIO jobs.

### class [JobUiDelegate](kio-jobuidelegate.md)

### class [KUriFilterSearchProviderActions](kio-kurifiltersearchprovideractions.md)

This class is a manager for web shortcuts.

### class [PasteJob](kio-pastejob.md)

A KIO job that handles pasting the clipboard contents.

### class [RenameDialog](kio-renamedialog.md)

### class [RenameFileDialog](kio-renamefiledialog.md)

Dialog for renaming a variable number of files.

### class [RenameFileWarningDialog](kio-renamefilewarningdialog.md)

Checks whether renaming a file/folder requires user confirmation and shows the appropriate dialog if so.

### class [WidgetsAskUserActionHandler](kio-widgetsaskuseractionhandler.md)

## Type Documentation {#type-documentation}

### \[since 6.14\] enum KIO::DndBehavior {#DndBehavior-enum}

Setting flag to determine what the default behaviour should be when dropping items.

| Constant | Value |   |
| --- | --- | --- |
| `KIO::AlwaysAsk` | `0` |   |
| `KIO::MoveIfSameDevice` | `1` | Move the dragged items without showing the options menu they are on the same device |

This enum was introduced in Qt 6.14.

### enum KIO::DropJobFlag {#DropJobFlag-enum}

**flags KIO::DropJobFlags**

Special flag of [DropJob](kio-dropjob.md) in addition to [KIO::JobFlag](../kiocore/kio.md#JobFlag-enum)

| Constant | Value |   |
| --- | --- | --- |
| `KIO::DropJobDefaultFlags` | `0` |   |
| `KIO::ShowMenuManually` | `1` | Show the menu manually with [DropJob::showMenu](kio-dropjob.md#showMenu) |
| `KIO::ExcludePluginsActions (since Qt 6.23)` | `2` | Exclude plugins actions from drop popup menu |

The `DropJobFlags` type is a typedef for `QFlags<DropJobFlag>. `It stores an OR combination of `DropJobFlag` values.

## Function Documentation {#function-documentation}

### \[since 5.0 (was called canPasteMimeSource before)\] bool KIO::canPasteMimeData(const QMimeData \**data*) {#canPasteMimeData}

Returns true if pasteMimeData will find any interesting format in `data`. You can use this method to enable/disable the paste action appropriately.

This function was introduced in 5.0 (was called canPasteMimeSource before).

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

### bool KIO::isClipboardDataCut(const QMimeData \**mimeData*) {#isClipboardDataCut}

Returns true if the URLs in `mimeData` were cut by the user. This should be called when pasting, to choose between moving and copying.

### KIO::PasteJob \*paste(const QMimeData \**mimeData*, const QUrl &*destDir*, KIO::JobFlags *flags* = DefaultFlags) {#paste}

Pastes the clipboard contents.

If the clipboard contains URLs, they are copied (or moved) to the destination URL, using a [KIO::CopyJob](../kiocore/kio-copyjob.md) subjob. Otherwise, the data from the clipboard is saved into a file using [KIO::storedPut](../kiocore/kio-storedtransferjob.md#storedPut), after asking the user to choose a filename and the preferred data format.

This takes care of recording the subjob in the [FileUndoManager](kio-fileundomanager.md), and emits [itemCreated](kio-pastejob.md#itemCreated) for every file or directory being created, so that the view can select these items.

`mimeData` the MIME data to paste, usually [QApplication::clipboard](https://doc.qt.io/qt-6/qguiapplication.html#clipboard)()-\>mimeData()

`destDir` The URL of the target directory

`flags` passed to the sub job

Returns a pointer to the job handling the operation.

### QString KIO::pasteActionText(const QMimeData \**mimeData*, bool \**enable*, const KFileItem &*destItem*) {#pasteActionText}

Returns the text to use for the Paste action, when the application supports pasting files, urls, and clipboard data, using pasteClipboard().

`mimeData` the mime data, usually [QApplication::clipboard](https://doc.qt.io/qt-6/qguiapplication.html#clipboard)()-\>mimeData().

`enable` output parameter, to be passed to [QAction::setEnabled](https://doc.qt.io/qt-6/qaction.html#enabled-prop). The pointer must be non-null, and in return the function will always set its value.

`destItem` item representing the directory into which the clipboard data or items would be pasted. Used to find out about permissions in that directory.

Returns a string suitable for [QAction::setText](https://doc.qt.io/qt-6/qaction.html#text-prop)

### void KIO::setClipboardDataCut(QMimeData \**mimeData*, bool *cut*) {#setClipboardDataCut}

Add the information whether the files were cut, into the mimedata.

`mimeData` pointer to the mimeData object to be populated. Must not be null.

`cut` if true, the user selected "cut" (saved as application/x-kde-cutselection in the mimedata).

*See also* [isClipboardDataCut](kio-sub-kiowidgets.md#isClipboardDataCut)()
