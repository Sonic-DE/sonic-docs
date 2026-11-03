---
title: "WallpaperItem QML Type"
description: "This class is exposed to wallpapers as the WallpaperItem root qml item."
---

# WallpaperItem QML Type

This class is exposed to wallpapers as the [WallpaperItem](qml-org-kde-plasma-plasmoid-wallpaperitem.md) root qml item. [More...](#details)

- Import Statement: import org.kde.plasma.plasmoid
- Inherits: [Item](https://doc.qt.io/qt-6/qml-qtquick-item.html)

## Detailed Description {#details}

## Property Documentation {#property-documentation}

### \[since 6.0\] accentColor : color {#accentColor-prop}

The accent color manually set by the wallpaper plugin. By default it's transparent, which means either the dominant color is used when "Accent Color From Wallpaper" is enabled, or the theme color is used.

This property was introduced in Qt 6.0.

### configuration : KConfigPropertyMap {#configuration-prop}

### contextualActions : list\<QAction\> {#contextualActions-prop}

Actions to be added in the desktop context menu. To instantiate QActions in a declarative way, PlasmaCore.Action {} can be used

### loading : bool {#loading-prop}

### pluginName : string {#pluginName-prop}
