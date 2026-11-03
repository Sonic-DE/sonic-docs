---
title: "KNSWidgets::Dialog Class"
description: "This class is a wrapper around the QtQuick QML dialog. This dialog content is loaded QQuickWidget. This class was introduced in Qt 6.0."
---

# KNSWidgets::Dialog Class

This class is a wrapper around the QtQuick QML dialog. This dialog content is loaded QQuickWidget. This class was introduced in Qt 6.0. [More...](#details)

- **Header:** `#include <Dialog>`
- **Since:** Qt 6.0
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS NewStuff)`  
  `target_link_libraries(mytarget PRIVATE KF6::NewStuff)`
- **Inherits:** [QDialog](https://doc.qt.io/qt-6/qdialog.html)

[List of all members, including inherited members](knswidgets-dialog-members.md)

## Public Functions

- [Dialog(const QString &configFile, QWidget \*parent = nullptr)](#Dialog)
- [QList\<KNSCore::Entry\> changedEntries() const](#changedEntries)
- [KNSCore::EngineBase \*engine()](#engine)

## Detailed Description {#details}

It is recommended to reuse an instance of this class if it is expected that the user reopens the dialog. For most usecases, you should use [KNSWidgets::Button](knswidgets-button.md) or [KNSWidgets::Action](knswidgets-action.md) directly.

## Member Function Documentation {#member-function-documentation}

### \[explicit\] Dialog::Dialog(const QString &*configFile*, QWidget \**parent* = nullptr) {#Dialog}

Constructs a new Dialog for the given config file and parent widget

### QList\<KNSCore::Entry\> Dialog::changedEntries() const {#changedEntries}

Entries that were changed while the user interacted with the dialog

### KNSCore::EngineBase \*Dialog::engine() {#engine}

Engine that is used by the dialog, might be null if the engine failed to initialize. Returns [KNSCore::EngineBase](../knewstuffcore/knscore-enginebase.md) used by the dialog
