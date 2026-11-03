---
title: "Kirigami::Platform::PlatformPluginFactory Class"
description: "This class is reimplemented by plugins to provide different implementations of PlatformTheme."
---

# Kirigami::Platform::PlatformPluginFactory Class

This class is reimplemented by plugins to provide different implementations of [PlatformTheme](kirigami-platform-platformtheme.md). [More...](#details)

- **Header:** `#include <Kirigami/Platform/PlatformPluginFactory>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS KirigamiPlatform)`  
  `target_link_libraries(mytarget PRIVATE KF6::KirigamiPlatform)`
- **Inherits:** [QObject](https://doc.qt.io/qt-6/qobject.html)

[List of all members, including inherited members](kirigami-platform-platformpluginfactory-members.md)

## Public Functions

- [Kirigami::Platform::PlatformTheme \*createPlatformTheme(QObject \*parent)](#createPlatformTheme)
- [Kirigami::Platform::Units \*createUnits(QObject \*parent)](#createUnits)

## Static Public Members

- [Kirigami::Platform::PlatformPluginFactory \*findPlugin(const QString &pluginName = {})](#findPlugin)

## Detailed Description {#details}

## Member Function Documentation {#member-function-documentation}

### \[pure virtual\] Kirigami::Platform::PlatformTheme \*PlatformPluginFactory::createPlatformTheme(QObject \**parent*) {#createPlatformTheme}

Creates an instance of [PlatformTheme](kirigami-platform-platformtheme.md) which can come out from an implementation provided by a plugin.

If this returns nullptr the [PlatformTheme](kirigami-platform-platformtheme.md) will use a fallback implementation that loads a theme definition from a QML file.

`parent` The parent object of the created [PlatformTheme](kirigami-platform-platformtheme.md)

### \[pure virtual\] Kirigami::Platform::Units \*PlatformPluginFactory::createUnits(QObject \**parent*) {#createUnits}

Creates an instance of Units which can come from an implementation provided by a plugin

`parent` The parent of the units object

### \[static\] Kirigami::Platform::PlatformPluginFactory \*PlatformPluginFactory::findPlugin(const QString &*pluginName* = {}) {#findPlugin}

Finds the plugin providing units and platformtheme for the current style The plugin pointer is cached, so only the first call is a potentially heavy operation

`pluginName` The name we want to search for, if empty the name of the current QtQuickControls style will be searched.

Returns a pointer to the [PlatformPluginFactory](kirigami-platform-platformpluginfactory.md) of the current style.
