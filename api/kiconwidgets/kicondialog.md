---
title: "KIconDialog Class"
description: "An icon selection dialog."
---

# KIconDialog Class

An icon selection dialog. [More...](#details)

- **Header:** `#include <KIconDialog>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS IconWidgets)`  
  `target_link_libraries(mytarget PRIVATE KF6::IconWidgets)`
- **Inherits:** [QDialog](https://doc.qt.io/qt-6/qdialog.html)

[List of all members, including inherited members](kicondialog-members.md)

## Public Functions

- [KIconDialog(QWidget \*parent = nullptr)](#KIconDialog)
- [int iconSize() const](#iconSize)
- [QString openDialog()](#openDialog)
- [void setCustomLocation(const QString &location)](#setCustomLocation)
- [void setIconSize(int size)](#setIconSize)
- [void setSelectedIcon(const QString &iconName)](#setSelectedIcon)
- [void setStrictIconSize(bool policy)](#setStrictIconSize)
- [void setup(KIconLoader::Group group, KIconLoader::Context context = KIconLoader::Application, bool strictIconSize = false, int iconSize = 0, bool user = false, bool lockUser = false, bool lockCustomDir = false)](#setup)
- [void showDialog()](#showDialog)
- [bool strictIconSize() const](#strictIconSize)

## Signals

- [void newIconName(const QString &iconName)](#newIconName)

## Static Public Members

- [QString getIcon(KIconLoader::Group group = KIconLoader::Desktop, KIconLoader::Context context = KIconLoader::Application, bool strictIconSize = false, int iconSize = 0, bool user = false, QWidget \*parent = nullptr, const QString &title = QString())](#getIcon)

## Detailed Description {#details}

Dialog for interactive selection of icons. Use the function [getIcon](kicondialog.md#getIcon)() to let the user select an icon.

## Member Function Documentation {#member-function-documentation}

### \[explicit\] KIconDialog::KIconDialog(QWidget \**parent* = nullptr) {#KIconDialog}

Constructs an icon selection dialog using the global icon loader.

`parent` The parent widget.

### \[static\] QString KIconDialog::getIcon(KIconLoader::Group *group* = KIconLoader::Desktop, KIconLoader::Context *context* = KIconLoader::Application, bool *strictIconSize* = false, int *iconSize* = 0, bool *user* = false, QWidget \**parent* = nullptr, const QString &*title* = QString()) {#getIcon}

Pops up the dialog an lets the user select an icon.

`group` The icon group this icon is intended for. Providing the group shows the icons in the dialog with the same appearance as when used outside the dialog.

`context` The initial icon context. Initially, the icons having this context are shown in the dialog. The user can change this.

`strictIconSize` When true, only icons of the specified group's size are shown, otherwise icon not available in the desired group's size will also be selectable.

`iconSize` the size of the icons – the default of the icon group if set to 0

`user` Begin with the "user icons" instead of "system icons".

`parent` The parent widget of the dialog.

`title` The title to use for the dialog.

Returns The name of the icon, suitable for loading with [KIconLoader](../kiconthemes/kiconloader.md).

### int KIconDialog::iconSize() const {#iconSize}

Returns the icon size set via [setIconSize](kicondialog.md#setIconSize)() or 0, if the default icon size will be used.

*See also* [setIconSize](kicondialog.md#setIconSize)()

### \[signal\] void KIconDialog::newIconName(const QString &*iconName*) {#newIconName}

### QString KIconDialog::openDialog() {#openDialog}

[exec](https://doc.qt.io/qt-6/qdialog.html#exec)()utes this modal dialog and returns the name of the selected icon, or QString() if the dialog was aborted. Returns the name of the icon, suitable for loading with [KIconLoader](../kiconthemes/kiconloader.md).

*See also* [getIcon](kicondialog.md#getIcon)

### void KIconDialog::setCustomLocation(const QString &*location*) {#setCustomLocation}

Sets the location of the custom icon directory. Only local directory paths are allowed.

### void KIconDialog::setIconSize(int *size*) {#setIconSize}

Sets the size of the icons to be shown / selected.

*See also* [KIconLoader::StdSizes](../kiconthemes/kiconloader.md#StdSizes-enum), [iconSize](kicondialog.md#iconSize)

### void KIconDialog::setSelectedIcon(const QString &*iconName*) {#setSelectedIcon}

Sets the icon that is initially selected in the dialog.

> **Note:** Changing this after the dialog has been shown has no effect.

> **Note:** If the given icon cannot be found in the current context, no icon will be selected.

`iconName` The name of the icon to select

### void KIconDialog::setStrictIconSize(bool *policy*) {#setStrictIconSize}

Sets a strict icon size policy for allowed icons.

`policy` When true, only icons of the specified group's size in [getIcon](kicondialog.md#getIcon)() are shown.

When false, icons not available at the desired group's size will also be selectable.

*See also* [strictIconSize](kicondialog.md#strictIconSize)()

### void KIconDialog::setup(KIconLoader::Group *group*, KIconLoader::Context *context* = KIconLoader::Application, bool *strictIconSize* = false, int *iconSize* = 0, bool *user* = false, bool *lockUser* = false, bool *lockCustomDir* = false) {#setup}

Allows you to set the same parameters as in the class method [getIcon](kicondialog.md#getIcon)(), as well as two additional parameters to lock the choice between system and user directories and to lock the custom icon directory itself.

### void KIconDialog::showDialog() {#showDialog}

[show](https://doc.qt.io/qt-6/qwidget.html#show)()s this dialog and emits a [newIconName](kicondialog.md#newIconName)(const [QString](https://doc.qt.io/qt-6/qstring.html)&) signal when successful. QString() will be emitted if the dialog was aborted.

### bool KIconDialog::strictIconSize() const {#strictIconSize}

Returns true if a strict icon size policy is set.

*See also* [setStrictIconSize](kicondialog.md#setStrictIconSize)()
