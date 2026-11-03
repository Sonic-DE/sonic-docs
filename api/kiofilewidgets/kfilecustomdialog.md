---
title: "KFileCustomDialog Class"
description: "This class implement a custom file dialog."
---

# KFileCustomDialog Class

This class implement a custom file dialog. [More...](#details)

- **Header:** `#include <KFileCustomDialog>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS KIO)`  
  `target_link_libraries(mytarget PRIVATE KF6::KIOFileWidgets)`
- **Inherits:** [QDialog](https://doc.qt.io/qt-6/qdialog.html)

[List of all members, including inherited members](kfilecustomdialog-members.md)

## Public Functions

- [KFileCustomDialog(QWidget \*parent = nullptr)](#KFileCustomDialog)
- [KFileCustomDialog(const QUrl &startDir, QWidget \*parent = nullptr)](#KFileCustomDialog-1)
- [KFileWidget \*fileWidget() const](#fileWidget)
- [void setCustomWidget(QWidget \*widget)](#setCustomWidget)
- [void setOperationMode(KFileWidget::OperationMode op)](#setOperationMode)
- [void setUrl(const QUrl &url)](#setUrl)

## Detailed Description {#details}

It uses a [KFileWidget](kfilewidget.md) and allows the application to provide a custom widget.

## Member Function Documentation {#member-function-documentation}

### \[explicit\] KFileCustomDialog::KFileCustomDialog(QWidget \**parent* = nullptr) {#KFileCustomDialog}

Constructs a custom file dialog

### \[explicit\] KFileCustomDialog::KFileCustomDialog(const QUrl &*startDir*, QWidget \**parent* = nullptr) {#KFileCustomDialog-1}

Constructs a custom file dialog

`startDir` see the [KFileWidget](kfilewidget.md) constructor for documentation

### KFileWidget \*KFileCustomDialog::fileWidget() const {#fileWidget}

Returns the filewidget used inside this dialog

### void KFileCustomDialog::setCustomWidget(QWidget \**widget*) {#setCustomWidget}

Set a custom widget that should be added to the file dialog.

`widget` A widget, or a widget of widgets, for displaying custom data in the file widget. This can be used, for example, to display a check box with the title "Open as read-only". When creating this widget, you don't need to specify a parent, since the widget's parent will be set automatically by [KFileWidget](kfilewidget.md).

### void KFileCustomDialog::setOperationMode(KFileWidget::OperationMode *op*) {#setOperationMode}

Sets the operational mode of the filedialog to Saving, Opening or Other. This will set some flags that are specific to loading or saving files. E.g. setKeepLocation() makes mostly sense for a save-as dialog. So setOperationMode( [KFileWidget::Saving](kfilewidget.md#OperationMode-enum) ); sets setKeepLocation for example.

The mode Saving, together with a default filter set via setMimeFilter() will make the filter combobox read-only.

The default mode is Opening.

Call this method right after instantiating [KFileWidget](kfilewidget.md).

*See also* [KFileWidget::OperationMode](kfilewidget.md#OperationMode-enum)

### void KFileCustomDialog::setUrl(const QUrl &*url*) {#setUrl}

Sets the directory to view.

`url` URL to show.
