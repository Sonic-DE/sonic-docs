---
title: "KIO::DeleteOrTrashJob Class"
description: "This job asks the user for confirmation to delete or move to Trash a list of URLs; or if the job is constructed with AskUserActionInterface::EmptyTrash, to empty the Trash."
---

# KIO::DeleteOrTrashJob Class

This job asks the user for confirmation to delete or move to Trash a list of URLs; or if the job is constructed with AskUserActionInterface::EmptyTrash, to empty the Trash. [More...](#details)

- **Header:** `#include <KIO/DeleteOrTrashJob>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS KIO)`  
  `target_link_libraries(mytarget PRIVATE KF6::KIOWidgets)`
- **Inherits:** [KCompositeJob](../kcoreaddons/kcompositejob.md)

[List of all members, including inherited members](kio-deleteortrashjob-members.md)

## Public Functions

- [DeleteOrTrashJob(const QList\<QUrl\> &urls, KIO::AskUserActionInterface::DeletionType deletionType, KIO::AskUserActionInterface::ConfirmationType confirm, QObject \*parent)](#DeleteOrTrashJob)
- [~DeleteOrTrashJob()](#dtor.DeleteOrTrashJob)
- [void start()](#start)

## Detailed Description {#details}

A KIO::WidgetAskUserActionHandler will be used by default, unless a [KJobUiDelegate](../kcoreaddons/kjobuidelegate.md) that implements [KIO::AskUserActionInterface](../kiocore/kio-askuseractioninterface.md) is set with [setUiDelegate](../kcoreaddons/kjob.md#setUiDelegate)().

In the case of moving items to Trash, this job records the operation using [KIO::FileUndoManager](kio-fileundomanager.md).

To start the job after constructing it, you must call [start](kio-deleteortrashjob.md#start)().

## Member Function Documentation {#member-function-documentation}

### \[explicit\] DeleteOrTrashJob::DeleteOrTrashJob(const QList\<QUrl\> &*urls*, KIO::AskUserActionInterface::DeletionType *deletionType*, KIO::AskUserActionInterface::ConfirmationType *confirm*, QObject \**parent*) {#DeleteOrTrashJob}

Creates a [DeleteOrTrashJob](kio-deleteortrashjob.md).

`urls` the list of urls to delete, move to Trash, or an empty list in the case of AskUserActionInterface::EmptyTrash (in the latter case, the list of urls is ignored)

`deletionType` one of AskUserActionInterface::DeletionType

`confirm` one of AskUserActionInterface::ConfirmationType

`parent` parent object, e.g. a [QWidget](https://doc.qt.io/qt-6/qwidget.html) for widget-based applications

### \[override virtual noexcept\] DeleteOrTrashJob::~DeleteOrTrashJob() {#dtor.DeleteOrTrashJob}

Destructor

Note that jobs auto-delete themselves after emitting result

### \[override virtual\] void DeleteOrTrashJob::start() {#start}

Reimplements: [KJob::start()](../kcoreaddons/kjob.md#start).

You must call this to actually start the job.
