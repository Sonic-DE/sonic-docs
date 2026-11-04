---
title: "KIO::FileUndoManager::UiInterface Class"
description: "productname."
---

# KIO::FileUndoManager::UiInterface Class

productname. [More...](#details)

- **Header:** `#include <UiInterface>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS KIO)`  
  `target_link_libraries(mytarget PRIVATE KF6::KIOWidgets)`

[List of all members, including inherited members](kio-fileundomanager-uiinterface-members.md)

## Public Functions

- [bool copiedFileWasModified(const QUrl &src, const QUrl &dest, const QDateTime &srcTime, const QDateTime &destTime)](#copiedFileWasModified)
- [void jobError(KIO::Job \*job)](#jobError)
- [QWidget \*parentWidget() const](#parentWidget)
- [void setParentWidget(QWidget \*parentWidget)](#setParentWidget)
- [void setShowProgressInfo(bool b)](#setShowProgressInfo)
- [bool showProgressInfo() const](#showProgressInfo)

## Detailed Description {#details}

Interface for the gui handling of [FileUndoManager](kio-fileundomanager.md). This includes three events currently:

- error when undoing a job
- (until KF 5.78) confirm deletion before undoing a copy job
- confirm deletion when the copied file has been modified afterwards

By default [UiInterface](kio-fileundomanager-uiinterface.md) shows message boxes in all three cases; applications can reimplement this interface to provide different user interfaces.

## Member Function Documentation {#member-function-documentation}

### \[virtual\] bool UiInterface::copiedFileWasModified(const QUrl &*src*, const QUrl &*dest*, const QDateTime &*srcTime*, const QDateTime &*destTime*) {#copiedFileWasModified}

Called when dest was modified since it was copied from src. Note that this is called after confirmDeletion. Return true if we should proceed with deleting dest.

### \[virtual\] void UiInterface::jobError(KIO::Job \**job*) {#jobError}

Called when an undo job errors; default implementation displays a message box.

### QWidget \*UiInterface::parentWidget() const {#parentWidget}

Returns the parent widget passed to the last call to undo(parentWidget), or `nullptr`.

*See also* [setParentWidget](kio-fileundomanager-uiinterface.md#setParentWidget)()

### void UiInterface::setParentWidget(QWidget \**parentWidget*) {#setParentWidget}

Sets the parent widget to use for message boxes.

*See also* [parentWidget](kio-fileundomanager-uiinterface.md#parentWidget)()

### void UiInterface::setShowProgressInfo(bool *b*) {#setShowProgressInfo}

Sets whether to show progress info when running the KIO jobs for undoing.

*See also* [showProgressInfo](kio-fileundomanager-uiinterface.md#showProgressInfo)()

### bool UiInterface::showProgressInfo() const {#showProgressInfo}

Returns whether progress info dialogs are shown while undoing.

*See also* [setShowProgressInfo](kio-fileundomanager-uiinterface.md#setShowProgressInfo)()
