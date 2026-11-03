---
title: "KNSWidgets::Button Class"
description: "QPushButton subclass that encapsulates the logic for showing the KNewStuff dialog."
---

# KNSWidgets::Button Class

[QPushButton](https://doc.qt.io/qt-6/qpushbutton.html) subclass that encapsulates the logic for showing the KNewStuff dialog. [More...](#details)

- **Header:** `#include <Button>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS NewStuff)`  
  `target_link_libraries(mytarget PRIVATE KF6::NewStuff)`
- **Inherits:** [QPushButton](https://doc.qt.io/qt-6/qpushbutton.html)

[List of all members, including inherited members](knswidgets-button-members.md)

## Public Functions

- [Button(QWidget \*parent)](#Button)
- [Button(const QString &text, const QString &configFile, QWidget \*parent)](#Button-1)
- [void setConfigFile(const QString &configFile)](#setConfigFile)

## Signals

- [void dialogFinished(const QList\<KNSCore::Entry\> &changedEntries)](#dialogFinished)

## Detailed Description {#details}

If KNewStuff is disabled using [KAuthorized](../kconfigcore/kauthorized.md), the button is hidden.

*See also* [KAuthorized::GenericRestriction::GHNS](../kconfigcore/kauthorized.md#GenericRestriction-enum)

## Member Function Documentation {#member-function-documentation}

### \[explicit\] Button::Button(QWidget \**parent*) {#Button}

Constructor used when the code is generated from a .ui file After the UI is set up, you must call [setConfigFile](knswidgets-button.md#setConfigFile)([QString](https://doc.qt.io/qt-6/qstring.html))

### \[explicit\] Button::Button(const QString &*text*, const QString &*configFile*, QWidget \**parent*) {#Button-1}

Constructor used when the details of the KHotNewStuff download is known when the button is created.

`text` describing what is being downloaded. It should be a text beginning with "Download New ..." for consistency

`configFile` the name of the .knsrc file

`parent` the parent widget

### \[signal\] void Button::dialogFinished(const QList\<KNSCore::Entry\> &*changedEntries*) {#dialogFinished}

Emitted when the dialog has been closed.

`changedEntries` contains the entries that were changed

### void Button::setConfigFile(const QString &*configFile*) {#setConfigFile}

> **Note:** This should only be used when creating the button from a UI-file.
