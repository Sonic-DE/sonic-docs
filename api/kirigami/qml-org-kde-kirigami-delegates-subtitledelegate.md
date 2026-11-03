---
title: "SubtitleDelegate QML Type"
description: "A convenience wrapper combining QtQuick Controls ItemDelegate and IconTitleSubtitle."
---

# SubtitleDelegate QML Type

A convenience wrapper combining [QtQuick](https://doc.qt.io/qt-6/qtquick-qmlmodule.html) Controls [ItemDelegate](https://doc.qt.io/qt-6/qml-qtquick-controls-itemdelegate.html) and [IconTitleSubtitle](qml-org-kde-kirigami-delegates-icontitlesubtitle.md). [More...](#details)

- Import Statement: import org.kde.kirigami.delegates
- Inherits: [ItemDelegate](https://doc.qt.io/qt-6/qml-qtquick-controls-itemdelegate.html)

## Detailed Description {#details}

This is an intentionally minimal wrapper that replaces the [ItemDelegate](https://doc.qt.io/qt-6/qml-qtquick-controls-itemdelegate.html)'s contentItem with an [IconTitleSubtitle](qml-org-kde-kirigami-delegates-icontitlesubtitle.md) and adds a subtitle property.

If you wish to customize the layout further, create your own [ItemDelegate](https://doc.qt.io/qt-6/qml-qtquick-controls-itemdelegate.html) subclass with the contentItem property set to the content of your choice. This can include [IconTitleSubtitle](qml-org-kde-kirigami-delegates-icontitlesubtitle.md) inside a Layout, for example.

> **Note:** If you don't need a subtitle, use [ItemDelegate](https://doc.qt.io/qt-6/qml-qtquick-controls-itemdelegate.html) directly.

*See also* [TitleSubtitle](qml-org-kde-kirigami-delegates-titlesubtitle.md), [IconTitleSubtitle](qml-org-kde-kirigami-delegates-icontitlesubtitle.md)

## Property Documentation {#property-documentation}

### subtitle : string {#subtitle-prop}

The subtitle to display.
