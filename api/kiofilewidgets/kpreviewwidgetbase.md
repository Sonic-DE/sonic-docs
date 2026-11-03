---
title: "KPreviewWidgetBase Class"
description: "Abstract baseclass for all preview widgets."
---

# KPreviewWidgetBase Class

Abstract baseclass for all preview widgets. [More...](#details)

- **Header:** `#include <KPreviewWidgetBase>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS KIO)`  
  `target_link_libraries(mytarget PRIVATE KF6::KIOFileWidgets)`
- **Inherits:** [QWidget](https://doc.qt.io/qt-6/qwidget.html)
- **Inherited By:** [KImageFilePreview](kimagefilepreview.md)

[List of all members, including inherited members](kpreviewwidgetbase-members.md)

## Public Functions

- [KPreviewWidgetBase(QWidget \*parent)](#KPreviewWidgetBase)
- [QStringList supportedMimeTypes() const](#supportedMimeTypes)

## Public Slots

- [void clearPreview()](#clearPreview)
- [void showPreview(const QUrl &url)](#showPreview)

## Protected Functions

- [void setSupportedMimeTypes(const QStringList &mimeTypes)](#setSupportedMimeTypes)

## Detailed Description {#details}

Abstract baseclass for all preview widgets which shall be used via KFileDialog::setPreviewWidget(const [KPreviewWidgetBase](kpreviewwidgetbase.md) \*). Ownership will be transferred to KFileDialog, so you have to create the preview with "new" and let KFileDialog delete it.

Just derive your custom preview widget from [KPreviewWidgetBase](kpreviewwidgetbase.md) and implement all the pure virtual methods. The slot [showPreview](kpreviewwidgetbase.md#showPreview)(const [QUrl](https://doc.qt.io/qt-6/qurl.html) &) is called every time the file selection changes.

## Member Function Documentation {#member-function-documentation}

### \[explicit\] KPreviewWidgetBase::KPreviewWidgetBase(QWidget \**parent*) {#KPreviewWidgetBase}

Constructor. Construct the user interface of your preview widget here and pass the KFileDialog this preview widget is going to be used in as the parent.

`parent` The KFileDialog this preview widget is going to be used in

### \[pure virtual slot\] void KPreviewWidgetBase::clearPreview() {#clearPreview}

Reimplement this to clear the preview. This is called when e.g. the selection is cleared or when multiple selections exist, or the directory is changed.

### \[protected\] void KPreviewWidgetBase::setSupportedMimeTypes(const QStringList &*mimeTypes*) {#setSupportedMimeTypes}

*See also* [supportedMimeTypes](kpreviewwidgetbase.md#supportedMimeTypes)()

### \[pure virtual slot\] void KPreviewWidgetBase::showPreview(const QUrl &*url*) {#showPreview}

This slot is called every time the user selects another file in the file dialog. Implement the stuff necessary to reflect the change here.

`url` The URL of the currently selected file.

### QStringList KPreviewWidgetBase::supportedMimeTypes() const {#supportedMimeTypes}

*See also* [setSupportedMimeTypes](kpreviewwidgetbase.md#setSupportedMimeTypes)()
