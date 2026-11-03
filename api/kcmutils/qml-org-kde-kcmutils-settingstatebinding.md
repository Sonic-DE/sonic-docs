---
title: "SettingStateBinding QML Type"
description: "SettingStateBinding automatically impacts the representation of an item based on the state of a setting. This type was introduced in Qt 6.0."
---

# SettingStateBinding QML Type

[SettingStateBinding](qml-org-kde-kcmutils-settingstatebinding.md) automatically impacts the representation of an item based on the state of a setting. This type was introduced in Qt 6.0. [More...](#details)

- Import Statement: import org.kde.kcmutils
- Since: Qt 6.0
- Inherits: [Loader](https://doc.qt.io/qt-6/qml-qtquick-loader.html)

## Detailed Description {#details}

It will disable the item if the setting is immutable and use a visual indicator for the state of the setting.

This is a higher level convenience wrapper for [SettingStateProxy](qml-org-kde-kcmutils-settingstateproxy.md) and [SettingHighlighter](qml-org-kde-kcmutils-settinghighlighter.md).

## Property Documentation {#property-documentation}

### configObject : KCoreConfigSkeleton {#configObject-prop}

The config object which will be monitored for setting state changes.

### extraEnabledConditions : bool {#extraEnabledConditions-prop}

[SettingStateBinding](qml-org-kde-kcmutils-settingstatebinding.md) will manage the enabled property of the target based on the immutability state of the setting it represents.

Sometimes that enabled state needs to bind to other properties as well to be computed properly. This extra condition will thus be combined with the immutability state of the setting to determine the effective enabled state of the target.

### \[read-only\] nonDefaultHighlightVisible : bool {#nonDefaultHighlightVisible-prop}

Expose whether the non default highlight is visible.

Allow one to implement highlight with custom items.

### settingName : string {#settingName-prop}

The name of the setting in the config object to be monitored.

### target : Item {#target-prop}

The graphical element whose state we want to manage based on a setting.

If target is not set, it will try to find the visual parent item.
