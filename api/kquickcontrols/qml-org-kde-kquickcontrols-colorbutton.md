---
title: "ColorButton QML Type"
description: "A pushbutton to display or allow user selection of a color."
---

# ColorButton QML Type

A pushbutton to display or allow user selection of a color. [More...](#details)

- Import Statement: import org.kde.kquickcontrols

## Detailed Description {#details}

This widget can be used to display or allow user selection of a color.

Example usage:

```qml
import org.kde.kquickcontrols

ColorButton {
  onColorChanged: console.log(color)
}
```

## Property Documentation {#property-documentation}

### ColorDialog dialogTitle : string {#ColorDialog-dialogTitle-prop}

Title to show in the dialog.

### color : color {#color-prop}

The user-selected color.

### dialogTitle : alias {#dialogTitle-prop}

Title to show in the dialog.

### showAlphaChannel : bool {#showAlphaChannel-prop}

Allow the user to configure an alpha value.

## Signal Documentation {#signal-documentation}

### accepted(color *color*) {#accepted-signal}

This signal is emitted when the `color` dialog has been accepted.

> **Note:** The corresponding handler is `onAccepted`.
