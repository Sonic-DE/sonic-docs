---
title: "LinkButton QML Type"
description: "A button that looks like a link."
---

# LinkButton QML Type

A button that looks like a link. [More...](#details)

- Import Statement: import org.kde.kirigami
- Inherits: [Label](https://doc.qt.io/qt-6/qml-qtquick-controls-label.html)
- Inherited By: [UrlButton](qml-org-kde-kirigami-urlbutton.md)

## Detailed Description {#details}

It uses the color scheme's link color, and triggers an action when clicked.

This component should not be used directly; prefer an actual button to navigate within the app or trigger actions, and prefer a [UrlButton](qml-org-kde-kirigami-urlbutton.md) to display a link to a web site or other remote resource. See also [https://develop.kde.org/hig/getting_input/#signaling-interactivity](https://develop.kde.org/hig/getting_input/#signaling-interactivity)

## Property Documentation {#property-documentation}

### acceptedButtons : Qt::MouseButtons {#acceptedButtons-prop}

This property holds the mouse buttons that the mouse area reacts to.

default: `Qt.LeftButton`

*See also* [MouseArea::acceptedButtons](https://doc.qt.io/qt-6/qml-qtquick-mousearea.html#acceptedButtons-prop)

### action : Action {#action-prop}

An action that will be triggered when the button is clicked

default: `null`; set an action to make it work.

### disabledColor : color {#disabledColor-prop}

This property holds the color of the link when disabled.

default: `Kirigami.Theme.textColor`

### mouseArea : MouseArea {#mouseArea-prop}

This property holds the mouse area element covering the button.

### normalColor : color {#normalColor-prop}

This property holds the normal color of the link when not pressed or disabled.

default: `Kirigami.Theme.linkColor`

### pressedColor : color {#pressedColor-prop}

This property holds the color of the link while pressed.

default: Whatever the normal color is set to, but 200% darker.
