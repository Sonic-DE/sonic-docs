---
title: "KIconEngine Class"
description: "A class to provide rendering of KDE icons."
---

# KIconEngine Class

A class to provide rendering of KDE icons. [More...](#details)

- **Header:** `#include <KIconEngine>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS IconThemes)`  
  `target_link_libraries(mytarget PRIVATE KF6::IconThemes)`
- **Inherits:** [QIconEngine](https://doc.qt.io/qt-6/qiconengine.html)

[List of all members, including inherited members](kiconengine-members.md)

## Public Functions

- [KIconEngine(const QString &iconName, KIconLoader \*iconLoader, const QStringList &overlays)](#KIconEngine)
- [KIconEngine(const QString &iconName, const KIconColors &colors, KIconLoader \*iconLoader)](#KIconEngine-1)
- [KIconEngine(const QString &iconName, const KIconColors &colors, KIconLoader \*iconLoader, const QStringList &overlays)](#KIconEngine-2) (since 6.1)
- [KIconEngine(const QString &iconName, KIconLoader \*iconLoader)](#KIconEngine-3)

## Detailed Description {#details}

This is mostly used to provide Qt's icon loading in plasma-integration

Application developers should use [QIcon::fromTheme](https://doc.qt.io/qt-6/qicon.html#fromTheme) instead of using it directly.

## Member Function Documentation {#member-function-documentation}

### KIconEngine::KIconEngine(const QString &*iconName*, KIconLoader \**iconLoader*, const QStringList &*overlays*) {#KIconEngine}

Constructs an icon engine for a named icon.

`iconName` the name of the icon to load

`iconLoader` The icon loader that this engine is to use.

`overlays` Add one or more overlays to the icon. See KIconLoader::Overlays.

*See also* [KIconLoader](kiconloader.md)

### KIconEngine::KIconEngine(const QString &*iconName*, const KIconColors &*colors*, KIconLoader \**iconLoader*) {#KIconEngine-1}

Constructs an icon engine for a KDE named icon with a specific palette.

`iconName` the name of the icon to load

`colors` defines the colors we want to be applied on this icon

`iconLoader` The KDE icon loader that this engine is to use.

### \[since 6.1\] KIconEngine::KIconEngine(const QString &*iconName*, const KIconColors &*colors*, KIconLoader \**iconLoader*, const QStringList &*overlays*) {#KIconEngine-2}

Constructs an icon engine for a KDE named icon with a specific palette and overlays.

`iconName` the name of the icon to load

`colors` defines the colors we want to be applied on this icon

`iconLoader` The KDE icon loader that this engine is to use.

`overlays` Add one or more overlays to the icon. See KIconLoader::Overlays.

This function was introduced in Qt 6.1.

### KIconEngine::KIconEngine(const QString &*iconName*, KIconLoader \**iconLoader*) {#KIconEngine-3}

This is an overloaded function.
