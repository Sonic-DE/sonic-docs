---
title: "KDE Namespace"
description: "Icon GUI utilities."
---

# KDE Namespace

Icon GUI utilities. [More...](#details)

- Header: KDE
- CMake: find\_package(KF6 REQUIRED COMPONENTS IconThemes) target\_link\_libraries(mytarget PRIVATE KF6::IconThemes)

## Detailed Description {#details}

## Function Documentation {#function-documentation}

### QIcon icon(const QString &*iconName*, KIconLoader \**iconLoader* = nullptr) {#icon}

Returns a [QIcon](https://doc.qt.io/qt-6/qicon.html) with an appropriate [KIconEngine](kiconengine.md) to perform loading and rendering. KIcons thus adhere to KDE style and effect standards.

### QIcon icon(const QString &*iconName*, const KIconColors &*colors*, KIconLoader \**iconLoader* = nullptr) {#icon-1}

Returns a [QIcon](https://doc.qt.io/qt-6/qicon.html) with an appropriate [KIconEngine](kiconengine.md) to perform loading and rendering. KIcons thus adhere to KDE style and effect standards.

### QIcon icon(const QString &*iconName*, const QStringList &*overlays*, KIconLoader \**iconLoader* = nullptr) {#icon-2}

Returns a [QIcon](https://doc.qt.io/qt-6/qicon.html) for the given icon, with additional overlays.
