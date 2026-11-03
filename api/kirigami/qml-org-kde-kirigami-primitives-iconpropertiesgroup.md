---
title: "IconPropertiesGroup QML Type"
description: "An object to be used as a grouped property compatible with QtQuickControls \"icon\" grouped property. This type was introduced in Qt 6.17."
---

# IconPropertiesGroup QML Type

An object to be used as a grouped property compatible with QtQuickControls "icon" grouped property. This type was introduced in Qt 6.17. [More...](#details)

- Import Statement: import org.kde.kirigami.primitives
- Since: Qt 6.17
- Inherits: [QtObject](https://doc.qt.io/qt-6/qml-qtqml-qtobject.html)

## Detailed Description {#details}

Kirigami components which expose an icon grouped property use this class. Use it if you are writing a component that exposes an icon that you wish to have an icon property compatible with QtQuickControls one, with name, source, color, width and height properties.

## Property Documentation {#property-documentation}

### color : color {#color-prop}

This property holds a color for the icon. Only monochrome svg icons can be dynamically recolored.

### height : real {#height-prop}

This property holds the preferred height for the icon. This is a size hint for the icon. It depends from the control implementation how this is enforced or not.

### name : string {#name-prop}

This property holds a freedesktop theme compatible name for the icon. It is the preferred source for the icon

### source : var {#source-prop}

This property can hold a full path to the icon, a QImage or a QIcon representing the icon. Use this with care and prefer name when possible

### width : real {#width-prop}

This property holds the preferred width for the icon. This is a size hint for the icon. It depends from the control implementation how this is enforced or not.

## Method Documentation {#method-documentation}

### IconPropertiesGroup fromControlsIcon(var *icon*) {#fromControlsIcon-method}

`icon` The icon to bind to.

This method is used to bind an icon from a QtQuickControls to an [IconPropertiesGroup](qml-org-kde-kirigami-primitives-iconpropertiesgroup.md) to have them to be kept in sync, use it as follows:

```qml
import QtQuick
import QtQuick.Controls as QQC
import org.kde.kirigami as Kirigami

Item {
    Kirigami.PlaceholderMessage {
        icon: icon.fromControlsIcon(button.icon)
    }
    QQC.Button {
        id.button
    }
}
```
