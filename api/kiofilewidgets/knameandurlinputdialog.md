---
title: "KNameAndUrlInputDialog Class"
description: "Dialog to ask for a name (e.g. filename) and a URL."
---

# KNameAndUrlInputDialog Class

Dialog to ask for a name (e.g. filename) and a URL. [More...](#details)

- **Header:** `#include <KNameAndUrlInputDialog>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS KIO)`  
  `target_link_libraries(mytarget PRIVATE KF6::KIOFileWidgets)`
- **Inherits:** [QDialog](https://doc.qt.io/qt-6/qdialog.html)

[List of all members, including inherited members](knameandurlinputdialog-members.md)

## Public Functions

- [KNameAndUrlInputDialog(const QString &nameLabel, const QString &urlLabel, const QUrl &startDir, QWidget \*parent)](#KNameAndUrlInputDialog)
- [QString name() const](#name)
- [void setSuggestedName(const QString &name)](#setSuggestedName)
- [void setSuggestedUrl(const QUrl &url)](#setSuggestedUrl)
- [QUrl url() const](#url)
- [QString urlText() const](#urlText)

## Detailed Description {#details}

Basically a merge of KLineEditDlg and KUrlRequesterDlg ;)

## Member Function Documentation {#member-function-documentation}

### KNameAndUrlInputDialog::KNameAndUrlInputDialog(const QString &*nameLabel*, const QString &*urlLabel*, const QUrl &*startDir*, QWidget \**parent*) {#KNameAndUrlInputDialog}

`nameLabel` label for the name field

`urlLabel` label for the URL requester

`startDir` start directory for the URL requester (optional)

`parent` parent widget

### QString KNameAndUrlInputDialog::name() const {#name}

Returns the name the user entered

### void KNameAndUrlInputDialog::setSuggestedName(const QString &*name*) {#setSuggestedName}

Pre-fill the name lineedit.

### void KNameAndUrlInputDialog::setSuggestedUrl(const QUrl &*url*) {#setSuggestedUrl}

Pre-fill the URL requester.

### QUrl KNameAndUrlInputDialog::url() const {#url}

Returns the URL the user entered

### QString KNameAndUrlInputDialog::urlText() const {#urlText}

Returns the URL the user entered, as plain text. This is only useful for creating relative symlinks.
