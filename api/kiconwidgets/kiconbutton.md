---
title: "KIconButton Class"
description: "A pushbutton for choosing an icon."
---

# KIconButton Class

A pushbutton for choosing an icon. [More...](#details)

- **Header:** `#include <KIconButton>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS IconWidgets)`  
  `target_link_libraries(mytarget PRIVATE KF6::IconWidgets)`
- **Inherits:** [QPushButton](https://doc.qt.io/qt-6/qpushbutton.html)

[List of all members, including inherited members](kiconbutton-members.md)

## Properties

- [icon : QString](#icon-prop)
- [iconSize : int](#iconSize-prop)
- [strictIconSize : bool](#strictIconSize-prop)

## Public Functions

- [KIconButton(QWidget \*parent = nullptr)](#KIconButton)
- [int buttonIconSize() const](#buttonIconSize)
- [const QString &icon() const](#icon)
- [int iconSize() const](#iconSize)
- [void resetIcon()](#resetIcon)
- [void setButtonIconSize(int size)](#setButtonIconSize)
- [void setIcon(const QIcon &icon)](#setIcon)
- [void setIcon(const QString &icon)](#setIcon-1)
- [void setIconSize(int size)](#setIconSize)
- [void setIconType(KIconLoader::Group group, KIconLoader::Context context, bool user = false)](#setIconType)
- [void setStrictIconSize(bool b)](#setStrictIconSize)
- [bool strictIconSize() const](#strictIconSize)

## Signals

- [void iconChanged(const QString &icon)](#iconChanged)

## Detailed Description {#details}

Pressing on the button will open a [KIconDialog](kicondialog.md) for the user to select an icon. The current icon will be displayed on the button.

*See also* [KIconDialog](kicondialog.md)

## Property Documentation {#property-documentation}

### icon : QString {#icon-prop}

**Access functions:**

- const `QString` &**[icon](kiconbutton.md#icon)**() const
- `void` **[setIcon](kiconbutton.md#setIcon-1)**(const `QString` &*icon*)
- `void` **[setIcon](kiconbutton.md#setIcon)**(const `QIcon` &*icon*)
- `void` **[resetIcon](kiconbutton.md#resetIcon)**()

**Notifier signal:**

- `void` **[iconChanged](kiconbutton.md#iconChanged)**(const `QString` &*icon*)

### iconSize : int {#iconSize-prop}

**Access functions:**

- `int` **[iconSize](kiconbutton.md#iconSize)**() const
- `void` **[setIconSize](kiconbutton.md#setIconSize)**(`int` *size*)

### strictIconSize : bool {#strictIconSize-prop}

**Access functions:**

- `bool` **[strictIconSize](kiconbutton.md#strictIconSize)**() const
- `void` **[setStrictIconSize](kiconbutton.md#setStrictIconSize)**(`bool` *b*)

## Member Function Documentation {#member-function-documentation}

### \[explicit\] KIconButton::KIconButton(QWidget \**parent* = nullptr) {#KIconButton}

Constructs a [KIconButton](kiconbutton.md) using the global icon loader.

`parent` The parent widget.

### int KIconButton::buttonIconSize() const {#buttonIconSize}

Returns the button's icon size.

*See also* [setButtonIconSize](kiconbutton.md#setButtonIconSize)()

### const QString &KIconButton::icon() const {#icon}

Returns the name of the selected icon.

> **Note:** Getter function for property [icon](kiconbutton.md#icon-prop).

*See also* [setIcon](kiconbutton.md#setIcon)()

### \[signal\] void KIconButton::iconChanged(const QString &*icon*) {#iconChanged}

Emitted when the icon has changed.

> **Note:** Notifier signal for property [icon](kiconbutton.md#icon-prop).

### int KIconButton::iconSize() const {#iconSize}

Returns the icon size set via [setIconSize](kiconbutton.md#setIconSize)() or 0, if the default icon size will be used.

> **Note:** Getter function for property [iconSize](kiconbutton.md#iconSize-prop).

*See also* [setIconSize](kiconbutton.md#setIconSize)()

### void KIconButton::resetIcon() {#resetIcon}

Resets the icon (reverts to an empty button).

> **Note:** Resetter function for property [icon](kiconbutton.md#icon-prop).

### void KIconButton::setButtonIconSize(int *size*) {#setButtonIconSize}

Sets the size of the icon to be shown on the button.

*See also* [KIconLoader::StdSizes](../kiconthemes/kiconloader.md#StdSizes-enum), [buttonIconSize](kiconbutton.md#buttonIconSize)

### void KIconButton::setIcon(const QIcon &*icon*) {#setIcon}

Sets the button's initial icon.

> **Note:** Setter function for property [icon](kiconbutton.md#icon-prop).

*See also* [icon](kiconbutton.md#icon)()

### void KIconButton::setIcon(const QString &*icon*) {#setIcon-1}

Sets the button's initial icon.

> **Note:** Setter function for property [icon](kiconbutton.md#icon-prop).

### void KIconButton::setIconSize(int *size*) {#setIconSize}

Sets the size of the icon to be shown / selected.

> **Note:** Setter function for property [iconSize](kiconbutton.md#iconSize-prop).

*See also* [KIconLoader::StdSizes](../kiconthemes/kiconloader.md#StdSizes-enum), [iconSize](kiconbutton.md#iconSize)

### void KIconButton::setIconType(KIconLoader::Group *group*, KIconLoader::Context *context*, bool *user* = false) {#setIconType}

Sets the icon group and context. Use [KIconLoader::NoGroup](../kiconthemes/kiconloader.md#Group-enum) if you want to allow icons for any group in the given context.

### void KIconButton::setStrictIconSize(bool *b*) {#setStrictIconSize}

Sets a strict icon size policy for allowed icons. When true, only icons of the specified group's size in [setIconType](kiconbutton.md#setIconType)() are allowed, and only icons of that size will be shown in the icon dialog.

> **Note:** Setter function for property [strictIconSize](kiconbutton.md#strictIconSize-prop).

*See also* [strictIconSize](kiconbutton.md#strictIconSize)()

### bool KIconButton::strictIconSize() const {#strictIconSize}

Returns true if a strict icon size policy is set.

> **Note:** Getter function for property [strictIconSize](kiconbutton.md#strictIconSize-prop).

*See also* [setStrictIconSize](kiconbutton.md#setStrictIconSize)()
