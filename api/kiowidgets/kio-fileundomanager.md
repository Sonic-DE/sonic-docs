---
title: "KIO::FileUndoManager Class"
description: "Makes it possible to undo KIO jobs."
---

# KIO::FileUndoManager Class

Makes it possible to undo KIO jobs. [More...](#details)

- **Header:** `#include <KIO/FileUndoManager>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS KIO)`  
  `target_link_libraries(mytarget PRIVATE KF6::KIOWidgets)`
- **Inherits:** [QObject](https://doc.qt.io/qt-6/qobject.html)

[List of all members, including inherited members](kio-fileundomanager-members.md)

## Public Types

- [enum FileUndoManager::CommandType](#CommandType-enum)

## Public Functions

- [quint64 currentCommandSerialNumber() const](#currentCommandSerialNumber)
- [bool isRedoAvailable() const](#isRedoAvailable) (since 6.17)
- [bool isUndoAvailable() const](#isUndoAvailable)
- [quint64 newCommandSerialNumber()](#newCommandSerialNumber)
- [void recordCopyJob(KIO::CopyJob \*copyJob)](#recordCopyJob)
- [void recordJob(KIO::FileUndoManager::CommandType op, const QList\<QUrl\> &src, const QUrl &dst, KIO::Job \*job)](#recordJob)
- [QString redoText() const](#redoText) (since 6.17)
- [void setUiInterface(KIO::FileUndoManager::UiInterface \*ui)](#setUiInterface)
- [KIO::FileUndoManager::UiInterface \*uiInterface() const](#uiInterface)
- [QString undoText() const](#undoText)

## Public Slots

- [void redo()](#redo) (since 6.17)
- [void undo()](#undo)

## Signals

- [void jobRecordingFinished(KIO::FileUndoManager::CommandType op)](#jobRecordingFinished)
- [void jobRecordingStarted(KIO::FileUndoManager::CommandType op)](#jobRecordingStarted)
- [void redoAvailable(bool avail)](#redoAvailable) (since 6.17)
- [void redoTextChanged(const QString &text)](#redoTextChanged) (since 6.17)
- [void undoAvailable(bool avail)](#undoAvailable)
- [void undoJobFinished()](#undoJobFinished)
- [void undoTextChanged(const QString &text)](#undoTextChanged)

## Static Public Members

- [KIO::FileUndoManager \*self()](#self)

## Detailed Description {#details}

This class is a singleton, use [self](kio-fileundomanager.md#self)() to access its only instance.

## Member Type Documentation {#member-type-documentation}

### enum FileUndoManager::CommandType {#CommandType-enum}

The type of job.

| Constant | Value |   |
| --- | --- | --- |
| `KIO::FileUndoManager::Copy` | `0` |   |
| `KIO::FileUndoManager::Move` | `1` |   |
| `KIO::FileUndoManager::Rename` | `2` |   |
| `KIO::FileUndoManager::Link` | `3` |   |
| `KIO::FileUndoManager::Mkdir` | `4` |   |
| `KIO::FileUndoManager::Trash` | `5` |   |
| `KIO::FileUndoManager::Put (since Qt 4.7)` | `6` | Represents the creation of a file from data in memory. Used when pasting data from clipboard or drag-n-drop |
| `KIO::FileUndoManager::Mkpath (since Qt 5.4)` | `7` | Represents a [KIO::mkpath](../kiocore/kio-mkpathjob.md#mkpath)() job |
| `KIO::FileUndoManager::BatchRename (since Qt 5.42)` | `8` | Represents a KIO::batchRename() job. Used when renaming multiple files |

## Member Function Documentation {#member-function-documentation}

### quint64 FileUndoManager::currentCommandSerialNumber() const {#currentCommandSerialNumber}

### \[since 6.17\] bool FileUndoManager::isRedoAvailable() const {#isRedoAvailable}

Returns true if redo is possible. Usually used for enabling/disabling the redo action.

This function was introduced in Qt 6.17.

### bool FileUndoManager::isUndoAvailable() const {#isUndoAvailable}

Returns true if undo is possible. Usually used for enabling/disabling the undo action.

### \[signal\] void FileUndoManager::jobRecordingFinished(KIO::FileUndoManager::CommandType *op*) {#jobRecordingFinished}

Emitted when a job that has been recorded by [FileUndoManager::recordJob](kio-fileundomanager.md#recordJob)() or [FileUndoManager::recordCopyJob](kio-fileundomanager.md#recordCopyJob) has been finished. The command is now available for an undo-operation.

### \[signal\] void FileUndoManager::jobRecordingStarted(KIO::FileUndoManager::CommandType *op*) {#jobRecordingStarted}

Emitted when a job recording has been started by [FileUndoManager::recordJob](kio-fileundomanager.md#recordJob)() or [FileUndoManager::recordCopyJob](kio-fileundomanager.md#recordCopyJob)(). After the job recording has been finished, the signal [jobRecordingFinished](kio-fileundomanager.md#jobRecordingFinished)() will be emitted.

### quint64 FileUndoManager::newCommandSerialNumber() {#newCommandSerialNumber}

These two functions are useful when wrapping [FileUndoManager](kio-fileundomanager.md) and adding custom commands. Each command has a unique ID. You can get a new serial number for a custom command with newCommandSerialNumber(), and then when you want to undo, check if the command [FileUndoManager](kio-fileundomanager.md) would undo is newer or older than your custom command.

*See also* [currentCommandSerialNumber](kio-fileundomanager.md#currentCommandSerialNumber)()

### void FileUndoManager::recordCopyJob(KIO::CopyJob \**copyJob*) {#recordCopyJob}

Record this CopyJob while it's happening and add a command for it so that the user can undo it. The signal [jobRecordingStarted](kio-fileundomanager.md#jobRecordingStarted)() is emitted.

### void FileUndoManager::recordJob(KIO::FileUndoManager::CommandType *op*, const QList\<QUrl\> &*src*, const QUrl &*dst*, KIO::Job \**job*) {#recordJob}

Record this job while it's happening and add a command for it so that the user can undo it. The signal [jobRecordingStarted](kio-fileundomanager.md#jobRecordingStarted)() is emitted.

`op` the type of job - which is also the type of command that will be created for it

`src` list of source urls. This is empty for Mkdir, Mkpath, Put operations.

`dst` destination url

`job` the job to record

### \[slot, since 6.17\] void FileUndoManager::redo() {#redo}

Redoes the last command Remember to call [uiInterface](kio-fileundomanager.md#uiInterface)()-\>setParentWidget(parentWidget) first, if you have multiple mainwindows.

This operation is asynchronous. [undoJobFinished](kio-fileundomanager.md#undoJobFinished) will be emitted once the redo is complete.

This function was introduced in Qt 6.17.

### \[signal, since 6.17\] void FileUndoManager::redoAvailable(bool *avail*) {#redoAvailable}

Emitted when the value of [isRedoAvailable](kio-fileundomanager.md#isRedoAvailable)() changes

This function was introduced in Qt 6.17.

### \[since 6.17\] QString FileUndoManager::redoText() const {#redoText}

Returns the current text for the redo action.

This function was introduced in Qt 6.17.

### \[signal, since 6.17\] void FileUndoManager::redoTextChanged(const QString &*text*) {#redoTextChanged}

Emitted when the value of [redoText](kio-fileundomanager.md#redoText)() changes

This function was introduced in Qt 6.17.

### \[static\] KIO::FileUndoManager \*FileUndoManager::self() {#self}

Returns the [FileUndoManager](kio-fileundomanager.md) instance

### void FileUndoManager::setUiInterface(KIO::FileUndoManager::UiInterface \**ui*) {#setUiInterface}

Set a new [UiInterface](kio-fileundomanager-uiinterface.md) implementation. This deletes the previous one.

`ui` the [UiInterface](kio-fileundomanager-uiinterface.md) instance, which becomes owned by the undo manager.

*See also* [uiInterface](kio-fileundomanager.md#uiInterface)()

### KIO::FileUndoManager::UiInterface \*FileUndoManager::uiInterface() const {#uiInterface}

Returns the [UiInterface](kio-fileundomanager-uiinterface.md) instance passed to [setUiInterface](kio-fileundomanager.md#setUiInterface). This is useful for calling setParentWidget on it. Never delete it!

*See also* [setUiInterface](kio-fileundomanager.md#setUiInterface)()

### \[slot\] void FileUndoManager::undo() {#undo}

Undoes the last command Remember to call [uiInterface](kio-fileundomanager.md#uiInterface)()-\>setParentWidget(parentWidget) first, if you have multiple mainwindows.

This operation is asynchronous. [undoJobFinished](kio-fileundomanager.md#undoJobFinished) will be emitted once the undo is complete.

### \[signal\] void FileUndoManager::undoAvailable(bool *avail*) {#undoAvailable}

Emitted when the value of [isUndoAvailable](kio-fileundomanager.md#isUndoAvailable)() changes

### \[signal\] void FileUndoManager::undoJobFinished() {#undoJobFinished}

Emitted when an undo (or redo) job finishes. Used for unit testing.

### QString FileUndoManager::undoText() const {#undoText}

Returns the current text for the undo action.

### \[signal\] void FileUndoManager::undoTextChanged(const QString &*text*) {#undoTextChanged}

Emitted when the value of [undoText](kio-fileundomanager.md#undoText)() changes
