---
title: "WheelHandler QML Type"
description: "Handles scrolling for a Flickable and 2 attached ScrollBars."
---

# WheelHandler QML Type

Handles scrolling for a Flickable and 2 attached ScrollBars. [More...](#details)

- Import Statement: import org.kde.kirigami

## Detailed Description {#details}

[WheelHandler](qml-org-kde-kirigami-wheelhandler.md) filters events from a Flickable, a vertical [ScrollBar](https://doc.qt.io/qt-6/qml-qtquick-controls-scrollbar.html) and a horizontal [ScrollBar](https://doc.qt.io/qt-6/qml-qtquick-controls-scrollbar.html). Wheel and KeyPress events (when [keyNavigationEnabled](qml-org-kde-kirigami-wheelhandler.md#keyNavigationEnabled-prop) is true) are used to scroll the Flickable. When [filterMouseEvents](qml-org-kde-kirigami-wheelhandler.md#filterMouseEvents-prop) is true, [WheelHandler](qml-org-kde-kirigami-wheelhandler.md) blocks mouse button input from reaching the Flickable and sets the interactive property of the scrollbars to false when touch input is used.

Wheel event handling behavior:

- Pixel delta is ignored unless angle delta is not available because pixel delta scrolling is too slow. Qt Widgets doesn't use pixel delta either, so the default scroll speed should be consistent with Qt Widgets.
- When using angle delta, scroll using the step increments defined by [verticalStepSize](qml-org-kde-kirigami-wheelhandler.md#verticalStepSize-prop) and [horizontalStepSize](qml-org-kde-kirigami-wheelhandler.md#horizontalStepSize-prop).
- When one of the keyboard modifiers in [pageScrollModifiers](qml-org-kde-kirigami-wheelhandler.md#pageScrollModifiers-prop) is used, scroll by pages.
- When using a device that doesn't use 120 angle delta unit increments such as a touchpad, the [verticalStepSize](qml-org-kde-kirigami-wheelhandler.md#verticalStepSize-prop), [horizontalStepSize](qml-org-kde-kirigami-wheelhandler.md#horizontalStepSize-prop) and page increments (if using page scrolling) will be multiplied by `angle delta / 120` to keep scrolling smooth.
- If scrolling has happened in the last 400ms, use an internal [QQuickItem](https://doc.qt.io/qt-6/qquickitem.html) stacked over the Flickable's contentItem to catch wheel events and use those wheel events to scroll, if possible. This prevents controls inside the Flickable's contentItem that allow scrolling to change the value (e.g., Sliders, SpinBoxes) from conflicting with scrolling the page.

Common usage with a Flickable:

```cpp
/* SPDX-FileCopyrightText: 2021 Noah Davis <noahadvs@gmail.com>
 * SPDX-License-Identifier: LGPL-2.1-only OR LGPL-3.0-only OR LicenseRef-KDE-Accepted-LGPL
 */
pragma ComponentBehavior: Bound

import QtQuick
import QtQuick.Controls as QQC2
import org.kde.kirigami as Kirigami

QQC2.ApplicationWindow {
    id: root

    width: flickable.implicitWidth
    height: flickable.implicitHeight
    visible: true

    Flickable {
        id: flickable

        anchors.fill: parent
        implicitWidth: wheelHandler.horizontalStepSize * 10 + leftMargin + rightMargin
        implicitHeight: wheelHandler.verticalStepSize * 10 + topMargin + bottomMargin

        leftMargin: QQC2.ScrollBar.vertical.visible && QQC2.ScrollBar.vertical.mirrored ? QQC2.ScrollBar.vertical.width : 0
        rightMargin: QQC2.ScrollBar.vertical.visible && !QQC2.ScrollBar.vertical.mirrored ? QQC2.ScrollBar.vertical.width : 0
        bottomMargin: QQC2.ScrollBar.horizontal.visible ? QQC2.ScrollBar.horizontal.height : 0

        contentWidth: contentItem.childrenRect.width
        contentHeight: contentItem.childrenRect.height

        Kirigami.WheelHandler {
            id: wheelHandler
            target: flickable
            filterMouseEvents: true
            keyNavigationEnabled: true
        }

        QQC2.ScrollBar.vertical: QQC2.ScrollBar {
            parent: flickable.parent
            height: flickable.height - flickable.topMargin - flickable.bottomMargin
            x: mirrored ? 0 : flickable.width - width
            y: flickable.topMargin
            active: flickable.QQC2.ScrollBar.horizontal.active
            stepSize: wheelHandler.verticalStepSize / flickable.contentHeight
        }

        QQC2.ScrollBar.horizontal: QQC2.ScrollBar {
            parent: flickable.parent
            width: flickable.width - flickable.leftMargin - flickable.rightMargin
            x: flickable.leftMargin
            y: flickable.height - height
            active: flickable.QQC2.ScrollBar.vertical.active
            stepSize: wheelHandler.horizontalStepSize / flickable.contentWidth
        }

        Grid { // Example content
            columns: Math.sqrt(visibleChildren.length)
            Repeater {
                model: 1000
                delegate: Rectangle {
                    id: delegate

                    required property int index

                    implicitWidth: wheelHandler.horizontalStepSize
                    implicitHeight: wheelHandler.verticalStepSize
                    gradient: Gradient {
                        orientation: delegate.index % 2 ? Gradient.Vertical : Gradient.Horizontal
                        GradientStop { position: 0; color: Qt.rgba(Math.random(), Math.random(), Math.random(), 1) }
                        GradientStop { position: 1; color: Qt.rgba(Math.random(), Math.random(), Math.random(), 1) }
                    }
                }
            }
        }
    }
}
```

Common usage inside of a [ScrollView](https://doc.qt.io/qt-6/qml-qtquick-controls-scrollview.html) template:

```cpp
/* SPDX-FileCopyrightText: 2021 Noah Davis <noahadvs@gmail.com>
 * SPDX-License-Identifier: LGPL-2.1-only OR LGPL-3.0-only OR LicenseRef-KDE-Accepted-LGPL
 */

import QtQuick
import QtQuick.Templates as T
import QtQuick.Controls as QQC2
import org.kde.kirigami as Kirigami

T.ScrollView {
    id: control

    implicitWidth: Math.max(implicitBackgroundWidth + leftInset + rightInset,
                            contentWidth + leftPadding + rightPadding)
    implicitHeight: Math.max(implicitBackgroundHeight + topInset + bottomInset,
                             contentHeight + topPadding + bottomPadding)

    leftPadding: mirrored && T.ScrollBar.vertical.visible && !Kirigami.Settings.isMobile ? T.ScrollBar.vertical.width : 0
    rightPadding: !mirrored && T.ScrollBar.vertical.visible && !Kirigami.Settings.isMobile ? T.ScrollBar.vertical.width : 0
    bottomPadding: T.ScrollBar.horizontal.visible && !Kirigami.Settings.isMobile ? T.ScrollBar.horizontal.height : 0

    data: [
        Kirigami.WheelHandler {
            id: wheelHandler
            target: control.contentItem
        }
    ]

    T.ScrollBar.vertical: QQC2.ScrollBar {
        parent: control
        x: control.mirrored ? 0 : control.width - width
        y: control.topPadding
        height: control.availableHeight
        active: control.T.ScrollBar.horizontal.active
        stepSize: wheelHandler.verticalStepSize / control.contentHeight
    }

    T.ScrollBar.horizontal: QQC2.ScrollBar {
        parent: control
        x: control.leftPadding
        y: control.height - height
        width: control.availableWidth
        active: control.T.ScrollBar.vertical.active
        stepSize: wheelHandler.horizontalStepSize / control.contentWidth
    }
}
```

## Property Documentation {#property-documentation}

### blockTargetWheel : bool {#blockTargetWheel-prop}

This property holds whether the [WheelHandler](qml-org-kde-kirigami-wheelhandler.md) blocks all wheel events from reaching the Flickable.

When this property is false, scrolling the Flickable with [WheelHandler](qml-org-kde-kirigami-wheelhandler.md) will only block an event from reaching the Flickable if the Flickable is actually scrolled by [WheelHandler](qml-org-kde-kirigami-wheelhandler.md).

> **Note:** Wheel events created by touchpad gestures with pixel deltas will always be accepted no matter what. This is because they will cause the Flickable to jump back to where scrolling started unless the events are always accepted before they reach the Flickable.

The default value is true.

### filterMouseEvents : bool {#filterMouseEvents-prop}

This property holds whether the [WheelHandler](qml-org-kde-kirigami-wheelhandler.md) filters mouse events like a Qt Quick Controls [ScrollView](https://doc.qt.io/qt-6/qml-qtquick-controls-scrollview.html) would.

Touch events are allowed to flick the view and they make the scrollbars not interactive.

Mouse events are not allowed to flick the view and they make the scrollbars interactive.

Hover events on the scrollbars and wheel events on anything also make the scrollbars interactive when this property is set to true.

The default value is `false`.

### horizontalStepSize : double {#horizontalStepSize-prop}

This property holds the horizontal step size.

The default value is equivalent to `20 * Qt.styleHints.wheelScrollLines`. This is consistent with the default increment for QScrollArea.

*See also* [verticalStepSize](qml-org-kde-kirigami-wheelhandler.md#verticalStepSize-prop)

### keyNavigationEnabled : bool {#keyNavigationEnabled-prop}

This property holds whether the [WheelHandler](qml-org-kde-kirigami-wheelhandler.md) handles keyboard scrolling.

- Left arrow scrolls a step to the left.
- Right arrow scrolls a step to the right.
- Up arrow scrolls a step upwards.
- Down arrow scrolls a step downwards.
- PageUp scrolls to the previous page.
- PageDown scrolls to the next page.
- Home scrolls to the beginning.
- End scrolls to the end.
- When Alt is held, scroll horizontally when using PageUp, PageDown, Home or End.

The default value is `false`.

### pageScrollModifiers : int {#pageScrollModifiers-prop}

This property holds the keyboard modifiers that will be used to start page scrolling.

The default value is equivalent to `Qt.ControlModifier | Qt.ShiftModifier`. This matches QScrollBar, which uses QAbstractSlider behavior.

### scrollFlickableTarget : bool {#scrollFlickableTarget-prop}

This property holds whether the [WheelHandler](qml-org-kde-kirigami-wheelhandler.md) can use wheel events to scroll the Flickable.

The default value is true.

### target : Item {#target-prop}

This property holds the Qt Quick Flickable that the [WheelHandler](qml-org-kde-kirigami-wheelhandler.md) will control.

### verticalStepSize : double {#verticalStepSize-prop}

This property holds the vertical step size.

The default value is equivalent to `20 * Qt.styleHints.wheelScrollLines`. This is consistent with the default increment for QScrollArea.

*See also* [horizontalStepSize](qml-org-kde-kirigami-wheelhandler.md#horizontalStepSize-prop)

## Signal Documentation {#signal-documentation}

### wheel(WheelEvent *wheel*) {#wheel-signal}

This signal is emitted when a wheel event reaches the event filter, just before scrolling is handled.

Accepting the `wheel` event in the `onWheel` signal handler prevents scrolling from happening.

> **Note:** The corresponding handler is `onWheel`.

## Method Documentation {#method-documentation}

### bool scrollDown(double *stepSize* = -1) {#scrollDown-method}

Scroll down one step. If the stepSize parameter is less than 0, the [verticalStepSize](qml-org-kde-kirigami-wheelhandler.md#verticalStepSize-prop) will be used.

returns true if the contentItem was moved.

### bool scrollLeft(double *stepSize* = -1) {#scrollLeft-method}

Scroll left one step. If the `stepSize` is less than 0, the [horizontalStepSize](qml-org-kde-kirigami-wheelhandler.md#horizontalStepSize-prop) will be used.

returns true if the contentItem was moved.

### bool scrollRight(double *stepSize* = -1) {#scrollRight-method}

Scroll right one step. If the stepSize parameter is less than 0, the [horizontalStepSize](qml-org-kde-kirigami-wheelhandler.md#horizontalStepSize-prop) will be used.

returns true if the contentItem was moved.

### bool scrollUp(double *stepSize* = -1) {#scrollUp-method}

Scroll up one step. If the `stepSize` parameter is less than 0, the [verticalStepSize](qml-org-kde-kirigami-wheelhandler.md#verticalStepSize-prop) will be used.

returns true if the contentItem was moved.
