---
title: "CheckSubtitleDelegate QML Type"
description: "A convenience wrapper combining QtQuick Controls CheckDelegate and IconTitleSubtitle."
---

# CheckSubtitleDelegate QML Type

A convenience wrapper combining [QtQuick](https://doc.qt.io/qt-6/qtquick-qmlmodule.html) Controls [CheckDelegate](https://doc.qt.io/qt-6/qml-qtquick-controls-checkdelegate.html) and [IconTitleSubtitle](qml-org-kde-kirigami-delegates-icontitlesubtitle.md). [More...](#details)

- Import Statement: import org.kde.kirigami.delegates
- Inherits: [CheckDelegate](https://doc.qt.io/qt-6/qml-qtquick-controls-checkdelegate.html)

## Detailed Description {#details}

This is an intentionally minimal wrapper that replaces the [CheckDelegate](https://doc.qt.io/qt-6/qml-qtquick-controls-checkdelegate.html)'s contentItem with an [IconTitleSubtitle](qml-org-kde-kirigami-delegates-icontitlesubtitle.md) and adds a subtitle property.

If you wish to customize the layout further, create your own [CheckDelegate](https://doc.qt.io/qt-6/qml-qtquick-controls-checkdelegate.html) subclass with the contentItem property set to the content of your choice. This can include [IconTitleSubtitle](qml-org-kde-kirigami-delegates-icontitlesubtitle.md) inside a Layout, for example.

> **Note:** If you don't need a subtitle, use [CheckDelegate](https://doc.qt.io/qt-6/qml-qtquick-controls-checkdelegate.html) directly.

*See also* [TitleSubtitle](qml-org-kde-kirigami-delegates-titlesubtitle.md), [IconTitleSubtitle](qml-org-kde-kirigami-delegates-icontitlesubtitle.md)

## Property Documentation {#property-documentation}

### subtitle : string {#subtitle-prop}

The subtitle to display.
