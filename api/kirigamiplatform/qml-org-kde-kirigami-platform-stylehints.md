---
title: "StyleHints QML Type"
description: "An attached type that contains hints for styles to use."
---

# StyleHints QML Type

An attached type that contains hints for styles to use. [More...](#details)

- Import Statement: import org.kde.kirigami.platform
- In C++: [StyleHints](kirigami-platform-stylehints.md)

## Detailed Description {#details}

The properties of [StyleHints](qml-org-kde-kirigami-platform-stylehints.md) can be used by [QtQuick](https://doc.qt.io/qt-6/qtquick-qmlmodule.html) styles to adjust how certain things look. Generally these properties are used to supplement the [QtQuick](https://doc.qt.io/qt-6/qtquick-qmlmodule.html) Controls APIs is some way.

## Property Documentation {#property-documentation}

### iconName : string {#iconName-prop}

An icon theme name for an icon.

To be used for controls that lack their own icon property, such as [ComboBox](https://doc.qt.io/qt-6/qml-qtquick-controls-combobox.html).

### iconSource : url {#iconSource-prop}

An icon source URL for an icon.

To be used for controls that lack their own icon property, such as [ComboBox](https://doc.qt.io/qt-6/qml-qtquick-controls-combobox.html).

### showFramedBackground : bool {#showFramedBackground-prop}

Should the background use a framed rather than a plain style.

Primarily intended for ScrollViews to indicate that the [ScrollView](https://doc.qt.io/qt-6/qml-qtquick-controls-scrollview.html) should draw a frame.

### tickMarkStepSize : int {#tickMarkStepSize-prop}

The step size to show tick marks at.

A step size of 0 or less results in no tick marks being shown. This is mainly intended to be used by sliders.

### useAlternateBackgroundColor : bool {#useAlternateBackgroundColor-prop}

Should the background color use an alternating colors style.
