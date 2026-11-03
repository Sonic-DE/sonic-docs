---
title: "KDesktopFileAction Class"
description: "Class for representing an Action of a desktop file. This class was introduced in Qt 6.0."
---

# KDesktopFileAction Class

Class for representing an Action of a desktop file. This class was introduced in Qt 6.0.

- **Header:** `#include <KDesktopFileAction>`
- **Since:** Qt 6.0
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS Config)`  
  `target_link_libraries(mytarget PRIVATE KF6::ConfigCore)`

## Public Functions

- [KDesktopFileAction()](#KDesktopFileAction)
- [KDesktopFileAction(const QString &name, const QString &text, const QString &icon, const QString &exec, const QString &desktopFilePath)](#KDesktopFileAction-1)
- [QString actionsKey() const](#actionsKey)
- [QString desktopFilePath() const](#desktopFilePath)
- [QString exec() const](#exec)
- [QString icon() const](#icon)
- [bool isSeparator() const](#isSeparator)
- [QString name() const](#name)

## Detailed Description {#details}

This represents an Action following the freedesktop [Desktop Entry Spec](https://specifications.freedesktop.org/desktop-entry-spec/desktop-entry-spec-latest.html).

*See also* [KDesktopFile](kdesktopfile.md)

## Member Function Documentation {#member-function-documentation}

### \[explicit\] KDesktopFileAction::KDesktopFileAction() {#KDesktopFileAction}

Constructs an empty [KDesktopFileAction](kdesktopfileaction.md).

Needed so the Action can be stored in containers that require type T to be default constructible (such as [QVariant](https://doc.qt.io/qt-6/qvariant.html)).

### \[explicit\] KDesktopFileAction::KDesktopFileAction(const QString &*name*, const QString &*text*, const QString &*icon*, const QString &*exec*, const QString &*desktopFilePath*) {#KDesktopFileAction-1}

Constructs a [KDesktopFileAction](kdesktopfileaction.md) at the given `desktopFilePath` with all minimum required properties `name`, `text`, `icon`, and `exec`.

### QString KDesktopFileAction::actionsKey() const {#actionsKey}

Returns the action's internal name.

For instance "Actions=Setup;"... and the group "\[Desktop Action Setup\]" define an action with the name "Setup".

### QString KDesktopFileAction::desktopFilePath() const {#desktopFilePath}

Returns the path of the desktop file this action was loaded from.

### QString KDesktopFileAction::exec() const {#exec}

Returns the action's exec command, as defined by the "Exec=" key in the desktop action group.

### QString KDesktopFileAction::icon() const {#icon}

Returns the action's icon, as defined by the "Icon=" key in the desktop action group.

### bool KDesktopFileAction::isSeparator() const {#isSeparator}

Returns whether the action is a separator.

This is `true` when [actionsKey](kdesktopfileaction.md#actionsKey) contains "\_SEPARATOR\_".

### QString KDesktopFileAction::name() const {#name}

Returns the action's name, as defined by the "Name=" key in the desktop action group.
