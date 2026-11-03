---
title: "Padding QML Type"
description: "This item simply adds an external padding to contentItem's size. This type was introduced in Qt 6.0."
---

# Padding QML Type

This item simply adds an external padding to [contentItem](qml-org-kde-kirigami-layouts-padding.md#contentItem-prop)'s size. This type was introduced in Qt 6.0. [More...](#details)

- Import Statement: import org.kde.kirigami.layouts
- Since: Qt 6.0
- Inherits: [Item](https://doc.qt.io/qt-6/qml-qtquick-item.html)

## Detailed Description {#details}

Padding item behaves similarly to [Control::padding](https://doc.qt.io/qt-6/qml-qtquick-controls-control.html#padding-prop), but is more lightweight and thus efficient. Its implicit size is set to that of its [contentItem](qml-org-kde-kirigami-layouts-padding.md#contentItem-prop)'s implicit size plus padding.

```cpp
import QtQuick.Controls as QQC2
import org.kde.kirigami as Kirigami

Kirigami.Padding {
    padding: Kirigami.Units.largeSpacing
    contentItem: QQC2.Button {}
}
```

With this component it is possible to add external paddings as a placeholder for an item, whereas with [QtQuick](https://doc.qt.io/qt-6/qtquick-qmlmodule.html) Layouts} you would need to manually assign or bind attached properties whenever content item changes.

```cpp
import QtQuick
import QtQuick.Layouts
import QtQuick.Controls as QQC2
import org.kde.kirigami as Kirigami

ColumnLayout {
    property alias contentItem: container.contentItem

    Kirigami.Heading {
        Layout.fillWidth: true
        Layout.margins: Kirigami.Units.largeSpacing
    }

    Kirigami.Padding {
        id: container
        Layout.fillWidth: true
        padding: Kirigami.Units.largeSpacing
    }
}
```

## Property Documentation {#property-documentation}

### \[read-only\] availableHeight : real {#availableHeight-prop}

The height available to the [contentItem](qml-org-kde-kirigami-layouts-padding.md#contentItem-prop) after deducting vertical padding from the width of the Padding.

### \[read-only\] availableWidth : real {#availableWidth-prop}

The width available to the [contentItem](qml-org-kde-kirigami-layouts-padding.md#contentItem-prop) after deducting horizontal padding from the width of the Padding.

### bottomPadding : real {#bottomPadding-prop}

This property holds the padding on the bottom side.

Unless explicitly set, it falls back to [verticalPadding](qml-org-kde-kirigami-layouts-padding.md#verticalPadding-prop) and then to padding.

### contentItem : Item {#contentItem-prop}

This property holds the visual content Item.

It will automatically resized taking into account all the paddings

### horizontalPadding : real {#horizontalPadding-prop}

This property holds the horizontal padding.

Unless explicitly set, the value is equal to padding.

### \[read-only\] implicitContentHeight : real {#implicitContentHeight-prop}

The implicitHeight of its [contentItem](qml-org-kde-kirigami-layouts-padding.md#contentItem-prop), or 0 if not present.

### \[read-only\] implicitContentWidth : real {#implicitContentWidth-prop}

The implicitWidth of its [contentItem](qml-org-kde-kirigami-layouts-padding.md#contentItem-prop), or 0 if not present.

### leftPadding : real {#leftPadding-prop}

This property holds the padding on the left side.

Unless explicitly set, it falls back to [horizontalPadding](qml-org-kde-kirigami-layouts-padding.md#horizontalPadding-prop) and then to padding. This always refers to the actual left, it won't be flipped on RTL layouts.

### padding : real {#padding-prop}

This property holds the default padding.

Padding adds a space between each edge of this ITem and its [contentItem](qml-org-kde-kirigami-layouts-padding.md#contentItem-prop), effectively controlling its size. To specify a padding value for a specific edge of the control, set its relevant property:

- [leftPadding](qml-org-kde-kirigami-layouts-padding.md#leftPadding-prop)
- [rightPadding](qml-org-kde-kirigami-layouts-padding.md#rightPadding-prop)
- [topPadding](qml-org-kde-kirigami-layouts-padding.md#topPadding-prop)
- [bottomPadding](qml-org-kde-kirigami-layouts-padding.md#bottomPadding-prop)

### rightPadding : real {#rightPadding-prop}

This property holds the padding on the right side.

Unless explicitly set, it falls back to [horizontalPadding](qml-org-kde-kirigami-layouts-padding.md#horizontalPadding-prop) and then to padding. This always refers to the actual right, it won't be flipped on RTL layouts.

### topPadding : real {#topPadding-prop}

the padding on the top side.

Unless explicitly set, it falls back to [verticalPadding](qml-org-kde-kirigami-layouts-padding.md#verticalPadding-prop) and then to padding.

### verticalPadding : real {#verticalPadding-prop}

This property holds the vertical padding.

Unless explicitly set, the value is equal to padding.
