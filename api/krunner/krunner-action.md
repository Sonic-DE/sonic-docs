---
title: "KRunner::Action Class"
description: "This class represents an action that will be shown next to a match. This class was introduced in Qt 6.0."
---

# KRunner::Action Class

This class represents an action that will be shown next to a match. This class was introduced in Qt 6.0. [More...](#details)

- **Header:** `#include <KRunner/Action>`
- **Since:** Qt 6.0
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS Runner)`  
  `target_link_libraries(mytarget PRIVATE KF6::Runner)`

[List of all members, including inherited members](krunner-action-members.md)

## Properties

- [\[read-only\] iconSource : const QString](#iconSource-prop)
- [\[read-only\] text : const QString](#text-prop)

## Public Functions

- [Action()](#Action)
- [Action(const QString &id, const QString &iconSource, const QString &text)](#Action-1)
- [Action::operator bool() const](#operator-bool)

## Detailed Description {#details}

The goal is to make it more reliable, because [QIcon::fromTheme](https://doc.qt.io/qt-6/qicon.html#fromTheme) which is often needed in a [QAction](https://doc.qt.io/qt-6/qaction.html) constructor is not thread safe. Also, it makes the API more consistent with the org.kde.krunner1 DBus interface and forces consumers to set an icon.

## Property Documentation {#property-documentation}

### \[read-only\] iconSource : const QString {#iconSource-prop}

Source for the icon: Name of the icon from a theme, file path or file URL

**Access functions:**

- `QString` **iconSource**() const

### \[read-only\] text : const QString {#text-prop}

User-visible text

**Access functions:**

- `QString` **text**() const

## Member Function Documentation {#member-function-documentation}

### Action::Action() {#Action}

Empty constructor creating invalid action

### \[explicit\] Action::Action(const QString &*id*, const QString &*iconSource*, const QString &*text*) {#Action-1}

Constructs a new action

`id` ID which identifies the action uniquely within the context of the respective runner plugin

`iconSource` name for the icon, that can be passed in to [QIcon::fromTheme](https://doc.qt.io/qt-6/qicon.html#fromTheme) or file path/URL

### \[explicit\] Action::operator bool() const {#operator-bool}

Check if the action is valid
