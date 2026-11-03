---
title: "KIO::RenameDialog Class"
description: "productname."
---

# KIO::RenameDialog Class

productname. [More...](#details)

- **Header:** `#include <KIO/RenameDialog>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS KIO)`  
  `target_link_libraries(mytarget PRIVATE KF6::KIOWidgets)`
- **Inherits:** [QDialog](https://doc.qt.io/qt-6/qdialog.html)

[List of all members, including inherited members](kio-renamedialog-members.md)

## Public Functions

- [RenameDialog(QWidget \*parent, const QString &title, const QUrl &src, const QUrl &dest, KIO::RenameDialog\_Options options, KIO::filesize\_t sizeSrc = filesize\_t(-1), KIO::filesize\_t sizeDest = filesize\_t(-1), const QDateTime &ctimeSrc = QDateTime(), const QDateTime &ctimeDest = QDateTime(), const QDateTime &mtimeSrc = QDateTime(), const QDateTime &mtimeDest = QDateTime())](#RenameDialog)
- [QUrl autoDestUrl() const](#autoDestUrl)
- [QUrl newDestUrl()](#newDestUrl)

## Public Slots

- [void cancelPressed()](#cancelPressed)
- [void overwriteAllPressed()](#overwriteAllPressed)
- [void overwritePressed()](#overwritePressed)
- [void overwriteWhenOlderPressed()](#overwriteWhenOlderPressed)
- [void renamePressed()](#renamePressed)
- [void resumeAllPressed()](#resumeAllPressed)
- [void resumePressed()](#resumePressed)
- [void skipPressed()](#skipPressed)
- [void suggestNewNamePressed()](#suggestNewNamePressed)

## Detailed Description {#details}

The dialog shown when a CopyJob realizes that a destination file already exists, and wants to offer the user with the choice to either Rename, Overwrite, Skip; this dialog is also used when a .part file exists and the user can choose to Resume a previous download.

## Member Function Documentation {#member-function-documentation}

### RenameDialog::RenameDialog(QWidget \**parent*, const QString &*title*, const QUrl &*src*, const QUrl &*dest*, KIO::RenameDialog\_Options *options*, KIO::filesize\_t *sizeSrc* = KIO::filesize\_t(-1), KIO::filesize\_t *sizeDest* = KIO::filesize\_t(-1), const QDateTime &*ctimeSrc* = QDateTime(), const QDateTime &*ctimeDest* = QDateTime(), const QDateTime &*mtimeSrc* = QDateTime(), const QDateTime &*mtimeDest* = QDateTime()) {#RenameDialog}

Construct a "rename" dialog to let the user know that `src` is about to overwrite `dest`.

`parent` parent widget (often 0)

`title` the title for the dialog box

`src` the url to the file/dir we're trying to copy, as it's part of the text message

`dest` the path to destination file/dir, i.e. the one that already exists

`options` parameters for the dialog (which buttons to show...),

`sizeSrc` size of source file

`sizeDest` size of destination file

`ctimeSrc` creation time of source file

`ctimeDest` creation time of destination file

`mtimeSrc` modification time of source file

`mtimeDest` modification time of destination file

### QUrl RenameDialog::autoDestUrl() const {#autoDestUrl}

Returns an automatically renamed destination valid always

### \[slot\] void RenameDialog::cancelPressed() {#cancelPressed}

### QUrl RenameDialog::newDestUrl() {#newDestUrl}

Returns the new destination valid only if RENAME was chosen

### \[slot\] void RenameDialog::overwriteAllPressed() {#overwriteAllPressed}

### \[slot\] void RenameDialog::overwritePressed() {#overwritePressed}

### \[slot\] void RenameDialog::overwriteWhenOlderPressed() {#overwriteWhenOlderPressed}

### \[slot\] void RenameDialog::renamePressed() {#renamePressed}

### \[slot\] void RenameDialog::resumeAllPressed() {#resumeAllPressed}

### \[slot\] void RenameDialog::resumePressed() {#resumePressed}

### \[slot\] void RenameDialog::skipPressed() {#skipPressed}

### \[slot\] void RenameDialog::suggestNewNamePressed() {#suggestNewNamePressed}
