---
title: "SettingHighlighter QML Type"
description: "SettingHighlighter automatically impacts the representation of an item based on the value of a setting. This type was introduced in Qt 6.0."
---

# SettingHighlighter QML Type

[SettingHighlighter](qml-org-kde-kcmutils-settinghighlighter.md) automatically impacts the representation of an item based on the value of a setting. This type was introduced in Qt 6.0. [More...](#details)

- Import Statement: import org.kde.kcmutils
- Since: Qt 6.0
- Inherits: [Loader](https://doc.qt.io/qt-6/qml-qtquick-loader.html)

## Detailed Description {#details}

When you are using this item you need to manually manage whether the highlighting is enabled or not. For a higher level component see [SettingStateBinding](qml-org-kde-kcmutils-settingstatebinding.md) which will manage the state of the Item.

## Property Documentation {#property-documentation}

### highlight : bool {#highlight-prop}

Whether the target will be highlighted.

### target : Item {#target-prop}

The graphical element whose appearance will be altered.

If target is not set, it will try to find the visual parent item.
