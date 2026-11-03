---
title: "KIO::RenameFileWarningDialog Class"
description: "Checks whether renaming a file/folder requires user confirmation and shows the appropriate dialog if so. This class was introduced in Qt 6.31."
---

# KIO::RenameFileWarningDialog Class

Checks whether renaming a file/folder requires user confirmation and shows the appropriate dialog if so. This class was introduced in Qt 6.31. [More...](#details)

- **Header:** `#include <KIO/RenameFileWarningDialog>`
- **Since:** Qt 6.31
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS KIO)`  
  `target_link_libraries(mytarget PRIVATE KF6::KIOWidgets)`
- **Inherits:** [QObject](https://doc.qt.io/qt-6/qobject.html)

[List of all members, including inherited members](kio-renamefilewarningdialog-members.md)

## Public Functions

- [RenameFileWarningDialog(const KFileItem &item, const QString &newName, QWidget \*parent = nullptr, bool hiddenFilesVisible = false)](#RenameFileWarningDialog)
- [void exec()](#exec)

## Signals

- [void result(bool accepted)](#result)

## Detailed Description {#details}

## Member Function Documentation {#member-function-documentation}

### \[explicit\] RenameFileWarningDialog::RenameFileWarningDialog(const KFileItem &*item*, const QString &*newName*, QWidget \**parent* = nullptr, bool *hiddenFilesVisible* = false) {#RenameFileWarningDialog}

`hiddenFilesVisible` suppresses the hidden-file warning when the view already shows hidden files.

### void RenameFileWarningDialog::exec() {#exec}

Connect to [result](kio-renamefilewarningdialog.md#result)() before calling this: it may be emitted synchronously.

### \[signal\] void RenameFileWarningDialog::result(bool *accepted*) {#result}

`accepted` is `true` if the rename should proceed.
