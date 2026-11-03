---
title: "KIO::AskUserActionInterface Class"
description: "The AskUserActionInterface class allows a KIO::Job to prompt the user for a decision when e.g. copying directories/files and there is a conflict (e.g. a file with the same name already exists at the destination)."
---

# KIO::AskUserActionInterface Class

The [AskUserActionInterface](kio-askuseractioninterface.md) class allows a [KIO::Job](kio-job.md) to prompt the user for a decision when e.g. copying directories/files and there is a conflict (e.g. a file with the same name already exists at the destination). [More...](#details)

- **Header:** `#include <KIO/AskUserActionInterface>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS KIO)`  
  `target_link_libraries(mytarget PRIVATE KF6::KIOCore)`
- **Inherits:** [QObject](https://doc.qt.io/qt-6/qobject.html)

[List of all members, including inherited members](kio-askuseractioninterface-members.md)

## Public Types

- [enum AskUserActionInterface::ConfirmationType](#ConfirmationType-enum)
- [enum AskUserActionInterface::DeletionType](#DeletionType-enum)
- [enum AskUserActionInterface::MessageDialogType](#MessageDialogType-enum)

## Public Functions

- [void askIgnoreSslErrors(const QVariantMap &sslErrorData, QWidget \*parent)](#askIgnoreSslErrors) (since 6.0)
- [void askUserDelete(const QList\<QUrl\> &urls, KIO::AskUserActionInterface::DeletionType deletionType, KIO::AskUserActionInterface::ConfirmationType confirmationType, QWidget \*parent = nullptr)](#askUserDelete)
- [void askUserRename(KJob \*job, const QString &title, const QUrl &src, const QUrl &dest, KIO::RenameDialog\_Options options, KIO::filesize\_t sizeSrc, KIO::filesize\_t sizeDest, const QDateTime &ctimeSrc = {}, const QDateTime &ctimeDest = {}, const QDateTime &mtimeSrc = {}, const QDateTime &mtimeDest = {})](#askUserRename)
- [void askUserSkip(KJob \*job, KIO::SkipDialog\_Options options, const QString &errorText)](#askUserSkip)
- [void requestUserMessageBox(KIO::AskUserActionInterface::MessageDialogType type, const QString &text, const QString &title, const QString &primaryActionText, const QString &secondatyActionText, const QString &primaryActionIconName = {}, const QString &secondatyActionIconName = {}, const QString &dontAskAgainName = {}, const QString &details = {}, QWidget \*parent = nullptr)](#requestUserMessageBox)

## Signals

- [void askIgnoreSslErrorsResult(int result)](#askIgnoreSslErrorsResult)
- [void askUserDeleteResult(bool allowDelete, const QList\<QUrl\> &urls, KIO::AskUserActionInterface::DeletionType deletionType, QWidget \*parent)](#askUserDeleteResult)
- [void askUserRenameResult(KIO::RenameDialog\_Result result, const QUrl &newUrl, KJob \*parentJob)](#askUserRenameResult)
- [void askUserSkipResult(KIO::SkipDialog\_Result result, KJob \*parentJob)](#askUserSkipResult)
- [void messageBoxResult(int result)](#messageBoxResult)

## Protected Functions

- [AskUserActionInterface(QObject \*parent = nullptr)](#AskUserActionInterface)

## Detailed Description {#details}

The methods in this interface are similar to their counterparts in [KIO::JobUiDelegateExtension](kio-jobuidelegateextension.md), the main difference is that [AskUserActionInterface](kio-askuseractioninterface.md) shows the dialogs using show() or [open](kio-filejob.md#open-1)(), rather than exec(), the latter creates a nested event loop which could lead to crashes.

*See also* [KIO::JobUiDelegateExtension](kio-index.md)

## Member Type Documentation {#member-type-documentation}

### enum AskUserActionInterface::ConfirmationType {#ConfirmationType-enum}

Deletion confirmation type.

Used by [askUserDelete](kio-askuseractioninterface.md#askUserDelete)().

| Constant | Value | Description |
| --- | --- | --- |
| `KIO::AskUserActionInterface::DefaultConfirmation` | `0` | Do not ask if the user has previously set the "Do not ask again" checkbox (which is is shown in the message dialog invoked by [askUserDelete](kio-askuseractioninterface.md#askUserDelete)()) |
| `KIO::AskUserActionInterface::ForceConfirmation` | `1` | Always ask the user for confirmation |

### enum AskUserActionInterface::DeletionType {#DeletionType-enum}

The type of deletion.

Used by [askUserDelete](kio-askuseractioninterface.md#askUserDelete)().

| Constant | Value | Description |
| --- | --- | --- |
| `KIO::AskUserActionInterface::Delete` | `0` | Delete the files/directories directly, i.e. without moving them to Trash |
| `KIO::AskUserActionInterface::Trash` | `1` | Move the files/directories to Trash |
| `KIO::AskUserActionInterface::EmptyTrash` | `2` | Empty the Trash |
| `KIO::AskUserActionInterface::DeleteInsteadOfTrash (since Qt 5.100)` | `3` | This is the same as Delete, but more text is added to the message to inform the user that moving to Trash was tried but failed due to size constraints. Typical use case is re-asking the user about deleting instead of Trashing. |
| `KIO::AskUserActionInterface::DeleteNoTrashAvailable (since Qt 6.21)` | `4` | This is the same as DeleteInsteadOfTrash, but used when trashing failed because no trash directory was available. |

### enum AskUserActionInterface::MessageDialogType {#MessageDialogType-enum}

| Constant | Description |
| --- | --- |
| `KIO::AskUserActionInterface::QuestionTwoActions (since Qt 5.100)` | `1` |
| `KIO::AskUserActionInterface::QuestionTwoActionsCancel (since Qt 5.100)` | `2` |
| `KIO::AskUserActionInterface::WarningTwoActions (since Qt 5.100)` | `3` |
| `KIO::AskUserActionInterface::WarningTwoActionsCancel (since Qt 5.100)` | `4` |
| `KIO::AskUserActionInterface::WarningContinueCancel` | `5` |
| `KIO::AskUserActionInterface::Information` | `7` |
| `KIO::AskUserActionInterface::Error` | `9` |

## Member Function Documentation {#member-function-documentation}

### \[explicit protected\] AskUserActionInterface::AskUserActionInterface(QObject \**parent* = nullptr) {#AskUserActionInterface}

Constructor

### \[pure virtual, since 6.0\] void AskUserActionInterface::askIgnoreSslErrors(const QVariantMap &*sslErrorData*, QWidget \**parent*) {#askIgnoreSslErrors}

This function was introduced in Qt 6.0.

### \[signal\] void AskUserActionInterface::askIgnoreSslErrorsResult(int *result*) {#askIgnoreSslErrorsResult}

### \[pure virtual\] void AskUserActionInterface::askUserDelete(const QList\<QUrl\> &*urls*, KIO::AskUserActionInterface::DeletionType *deletionType*, KIO::AskUserActionInterface::ConfirmationType *confirmationType*, QWidget \**parent* = nullptr) {#askUserDelete}

Ask for confirmation before moving `urls` (files/directories) to the Trash, emptying the Trash, or directly deleting files (i.e. without moving to Trash).

Note that this method is not called automatically by KIO jobs. It's the application's responsibility to ask the user for confirmation before calling [KIO::del](kio-deletejob.md#del)() or [KIO::trash](kio-copyjob.md#trash)().

You need to connect to the [askUserDeleteResult](kio-askuseractioninterface.md#askUserDeleteResult) signal to get the dialog's result (exit code).

`urls` the urls about to be moved to the Trash or deleted directly

`deletionType` the type of deletion (Delete for real deletion, Trash otherwise), see the [DeletionType](kio-askuseractioninterface.md#DeletionType-enum) enum

`confirmationType` The type of deletion confirmation, see the [ConfirmationType](kio-askuseractioninterface.md#ConfirmationType-enum) enum. Normally set to [DefaultConfirmation](kio-askuseractioninterface.md#ConfirmationType-enum)

`parent` the parent widget of the message box

### \[signal\] void AskUserActionInterface::askUserDeleteResult(bool *allowDelete*, const QList\<QUrl\> &*urls*, KIO::AskUserActionInterface::DeletionType *deletionType*, QWidget \**parent*) {#askUserDeleteResult}

Implementations of this interface must emit this signal when the dialog invoked by [askUserDelete](kio-askuseractioninterface.md#askUserDelete)() finishes, to notify the caller of the user's decision.

`allowDelete` set to true if the user confirmed the delete operation, otherwise set to false

`urls` a list of urls to delete/trash

`deletionType` the deletion type to use, one of [KIO::AskUserActionInterface::DeletionType](kio-askuseractioninterface.md#DeletionType-enum)

`parent` the parent widget passed to [askUserDelete](kio-askuseractioninterface.md#askUserDelete)(), for request identification

### \[pure virtual\] void AskUserActionInterface::askUserRename(KJob \**job*, const QString &*title*, const QUrl &*src*, const QUrl &*dest*, KIO::RenameDialog\_Options *options*, KIO::filesize\_t *sizeSrc*, KIO::filesize\_t *sizeDest*, const QDateTime &*ctimeSrc* = {}, const QDateTime &*ctimeDest* = {}, const QDateTime &*mtimeSrc* = {}, const QDateTime &*mtimeDest* = {}) {#askUserRename}

Constructs a modal, parent-less "rename" dialog, to prompt the user for a decision in case of conflicts, while copying/moving files. The dialog is shown using [open](kio-filejob.md#open-1)(), rather than exec() (the latter creates a nested eventloop which could lead to crashes). You will need to connect to the [askUserRenameResult](kio-askuseractioninterface.md#askUserRenameResult)() signal to get the dialog's result (exit code). The exit code is one of [KIO::RenameDialog\_Result](kio.md#RenameDialog_Result-enum).

`job` the job that called this method

`title` the title for the dialog box

`src` the URL of the file/dir being copied/moved

`dest` the URL of the destination file/dir, i.e. the one that already exists

`options` parameters for the dialog (which buttons to show... etc), OR'ed values

`from` the [KIO::RenameDialog\_Options](kio.md#RenameDialog_Option-enum) enum

`sizeSrc` size of the source file

`sizeDest` size of the destination file

`ctimeSrc` creation time of the source file

`ctimeDest` creation time of the destination file

`mtimeSrc` modification time of the source file

`mtimeDest` modification time of the destination file

*See also* [KIO::RenameDialog](kio-index.md), [KIO::RenameDialog\_Result](kio-index.md)

### \[signal\] void AskUserActionInterface::askUserRenameResult(KIO::RenameDialog\_Result *result*, const QUrl &*newUrl*, KJob \**parentJob*) {#askUserRenameResult}

Implementations of this interface must emit this signal when the rename dialog finishes, to notify the caller of the dialog's result.

`result` the exit code from the rename dialog, one of the [KIO::RenameDialog\_Result](kio.md#RenameDialog_Result-enum) enum

`newUrl` the new destination URL set by the user

`parentJob` the job that invoked the dialog

### \[pure virtual\] void AskUserActionInterface::askUserSkip(KJob \**job*, KIO::SkipDialog\_Options *options*, const QString &*errorText*) {#askUserSkip}

You need to connect to the [askUserSkipResult](kio-askuseractioninterface.md#askUserSkipResult) signal to get the dialog's result.

`job` the job that called this method

`options` parameters for the dialog (which buttons to show... etc), OR'ed values from the [KIO::SkipDialog\_Options](kio.md#SkipDialog_Option-enum) enum

`error_text` the error text to show to the user (usually the string returned by [KJob::errorText](../kcoreaddons/kjob.md#errorText)())

*See also* [KIO::SkipDialog](kio-index.md)

### \[signal\] void AskUserActionInterface::askUserSkipResult(KIO::SkipDialog\_Result *result*, KJob \**parentJob*) {#askUserSkipResult}

Implementations of this interface must emit this signal when the skip dialog finishes, to notify the caller of the dialog's result.

`result` the exit code from the skip dialog, one of the KIO::SkipDialog\_Result enum

`parentJob` the job that invoked the dialog

### \[signal\] void AskUserActionInterface::messageBoxResult(int *result*) {#messageBoxResult}

Implementations of this interface must emit this signal when the dialog invoked by [requestUserMessageBox](kio-askuseractioninterface.md#requestUserMessageBox)() finishes, to notify the caller of the dialog's result (exit code).

`result` the exit code of the dialog, one of [KIO::WorkerBase::ButtonCode](kio-workerbase.md#ButtonCode-enum) enum

### \[pure virtual\] void AskUserActionInterface::requestUserMessageBox(KIO::AskUserActionInterface::MessageDialogType *type*, const QString &*text*, const QString &*title*, const QString &*primaryActionText*, const QString &*secondatyActionText*, const QString &*primaryActionIconName* = {}, const QString &*secondatyActionIconName* = {}, const QString &*dontAskAgainName* = {}, const QString &*details* = {}, QWidget \**parent* = nullptr) {#requestUserMessageBox}

This function allows for the delegation of user prompts from the KIO worker.

`type` the desired type of message box, see the [MessageDialogType](kio-askuseractioninterface.md#MessageDialogType-enum) enum

`text` the message to show to the user

`title` the title of the message dialog box

`primaryActionText` the text for the primary action

`secondatyActionText` the text for the secondary action

`primaryActionIconName` the icon to show on the primary action

`secondatyActionIconName` the icon to show on the secondary action

`dontAskAgainName` the config key name used to store the result from 'Do not ask again' checkbox

`details` more details about the message shown to the user

`parent` the parent widget of the dialog
