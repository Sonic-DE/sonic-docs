---
title: "KIO::RenameFileDialog Class"
description: "Dialog for renaming a variable number of files."
---

# KIO::RenameFileDialog Class

Dialog for renaming a variable number of files. [More...](#details)

- **Header:** `#include <KIO/RenameFileDialog>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS KIO)`  
  `target_link_libraries(mytarget PRIVATE KF6::KIOWidgets)`
- **Inherits:** [QDialog](https://doc.qt.io/qt-6/qdialog.html)

[List of all members, including inherited members](kio-renamefiledialog-members.md)

## Public Functions

- [RenameFileDialog(const KFileItemList &items, QWidget \*parent)](#RenameFileDialog)

## Signals

- [void error(KJob \*error)](#error)
- [void renamingFinished(const QList\<QUrl\> &urls)](#renamingFinished)

## Detailed Description {#details}

The dialog deletes itself when accepted or rejected.

## Member Function Documentation {#member-function-documentation}

### \[explicit\] RenameFileDialog::RenameFileDialog(const KFileItemList &*items*, QWidget \**parent*) {#RenameFileDialog}

Constructs the Dialog to rename file(s)

`parent` the parent [QWidget](https://doc.qt.io/qt-6/qwidget.html)

`items` a non-empty list of items to rename

### \[signal\] void RenameFileDialog::error(KJob \**error*) {#error}

### \[signal\] void RenameFileDialog::renamingFinished(const QList\<QUrl\> &*urls*) {#renamingFinished}
