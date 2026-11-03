---
title: "KUrlRequesterDialog Class"
description: "Simple dialog to enter a filename/url."
---

# KUrlRequesterDialog Class

Simple dialog to enter a filename/url. [More...](#details)

- **Header:** `#include <KUrlRequesterDialog>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS KIO)`  
  `target_link_libraries(mytarget PRIVATE KF6::KIOWidgets)`
- **Inherits:** [QDialog](https://doc.qt.io/qt-6/qdialog.html)

[List of all members, including inherited members](kurlrequesterdialog-members.md)

## Public Functions

- [KUrlRequesterDialog(const QUrl &url, QWidget \*parent = nullptr)](#KUrlRequesterDialog)
- [KUrlRequesterDialog(const QUrl &url, const QString &text, QWidget \*parent)](#KUrlRequesterDialog-1)
- [QUrl selectedUrl() const](#selectedUrl)
- [KUrlRequester \*urlRequester()](#urlRequester)

## Static Public Members

- [QUrl getUrl(const QUrl &url = QUrl(), QWidget \*parent = nullptr, const QString &title = QString())](#getUrl)

## Detailed Description {#details}

Dialog in which a user can enter a filename or url. It is a dialog encapsulating [KUrlRequester](kurlrequester.md).

## Member Function Documentation {#member-function-documentation}

### \[explicit\] KUrlRequesterDialog::KUrlRequesterDialog(const QUrl &*url*, QWidget \**parent* = nullptr) {#KUrlRequesterDialog}

Constructs a [KUrlRequesterDialog](kurlrequesterdialog.md).

`url` The url of the directory to start in. Use QString() to start in the current working directory, or the last directory where a file has been selected.

`parent` The parent object of this widget.

### KUrlRequesterDialog::KUrlRequesterDialog(const QUrl &*url*, const QString &*text*, QWidget \**parent*) {#KUrlRequesterDialog-1}

Constructs a [KUrlRequesterDialog](kurlrequesterdialog.md).

`url` The url of the directory to start in. Use QString() to start in the current working directory, or the last directory where a file has been selected.

`text` Text of the label

`parent` The parent object of this widget.

### \[static\] QUrl KUrlRequesterDialog::getUrl(const QUrl &*url* = QUrl(), QWidget \**parent* = nullptr, const QString &*title* = QString()) {#getUrl}

Creates a modal dialog, executes it and returns the selected URL.

`url` This specifies the initial path of the input line.

`parent` The widget the dialog will be centered on initially.

`title` The title to use for the dialog.

### QUrl KUrlRequesterDialog::selectedUrl() const {#selectedUrl}

Returns the fully qualified filename.

### KUrlRequester \*KUrlRequesterDialog::urlRequester() {#urlRequester}

Returns a pointer to the [KUrlRequester](kurlrequester.md).
