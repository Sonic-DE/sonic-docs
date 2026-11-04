---
title: "KNSWidgets Namespace"
description: "Contains UX widgets for KNewStuffCore."
---

# KNSWidgets Namespace

Contains UX widgets for [KNewStuffCore](../knewstuffcore/knewstuffcore-module.md). [More...](#details)

- **Header:** `#include <KNSWidgets>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS NewStuff)`  
  `target_link_libraries(mytarget PRIVATE KF6::NewStuff)`

## Detailed Description {#details}

## Classes {#classes}

### class [Action](knswidgets-action.md)

QAction subclass that encapsulates the logic for showing the KNewStuff dialog.

### class [Button](knswidgets-button.md)

[QPushButton](https://doc.qt.io/qt-6/qpushbutton.html) subclass that encapsulates the logic for showing the KNewStuff dialog.

### class [Dialog](knswidgets-dialog.md)

This class is a wrapper around the QtQuick QML dialog. This dialog content is loaded QQuickWidget.
