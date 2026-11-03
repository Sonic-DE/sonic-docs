---
title: "SwitchSubtitleDelegate QML Type"
description: "A convenience wrapper combining QtQuick Controls SwitchDelegate and IconTitleSubtitle."
---

# SwitchSubtitleDelegate QML Type

A convenience wrapper combining [QtQuick](https://doc.qt.io/qt-6/qtquick-qmlmodule.html) Controls [SwitchDelegate](https://doc.qt.io/qt-6/qml-qtquick-controls-switchdelegate.html) and [IconTitleSubtitle](qml-org-kde-kirigami-delegates-icontitlesubtitle.md). [More...](#details)

- Import Statement: import org.kde.kirigami.delegates
- Inherits: [SwitchDelegate](https://doc.qt.io/qt-6/qml-qtquick-controls-switchdelegate.html)

## Detailed Description {#details}

This is an intentionally minimal wrapper that replaces the [SwitchDelegate](https://doc.qt.io/qt-6/qml-qtquick-controls-switchdelegate.html)'s contentItem with an [IconTitleSubtitle](qml-org-kde-kirigami-delegates-icontitlesubtitle.md) and adds a subtitle property.

If you wish to customize the layout further, create your own [SwitchDelegate](https://doc.qt.io/qt-6/qml-qtquick-controls-switchdelegate.html) subclass with the `contentItem`: property set to the content of your choice. This can include [IconTitleSubtitle](qml-org-kde-kirigami-delegates-icontitlesubtitle.md) inside a Layout, for example.

> **Note:** If you don't need a subtitle, use [SwitchDelegate](https://doc.qt.io/qt-6/qml-qtquick-controls-switchdelegate.html) directly.

*See also* [TitleSubtitle](qml-org-kde-kirigami-delegates-titlesubtitle.md), [IconTitleSubtitle](qml-org-kde-kirigami-delegates-icontitlesubtitle.md)

## Property Documentation {#property-documentation}

### subtitle : string {#subtitle-prop}

The subtitle to display.
