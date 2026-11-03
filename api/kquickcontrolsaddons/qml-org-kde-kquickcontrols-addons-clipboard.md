---
title: "Clipboard QML Type"
description: "Wrapper for QClipboard."
---

# Clipboard QML Type

Wrapper for QClipboard. [More...](#details)

- Import Statement: import org.kde.kquickcontrols.addons

## Detailed Description {#details}

Offers a simple wrapper to interact with QClipboard from [QtQuick](https://doc.qt.io/qt-6/qtquick-qmlmodule.html).

```qml
import QtQuick
import org.kde.kquickcontrolsaddons as KQuickControlsAddons
Text {
    text: "lorem ipsum"

    KQuickControlsAddons.Clipboard { id: clipboard }

    MouseArea {
        anchors.fill: parent
        acceptedButtons: Qt.LeftButton | Qt.RightButton
        onClicked: clipboard.content = parent.text
    }
}
```

## Property Documentation {#property-documentation}

### content : var {#content-prop}

Provides the contents currently in the clipboard and lets modify them.

### formats : list\<string\> {#formats-prop}

Figure out the nature of the contents in the clipboard as mimetype strings.

### mode : QClipboard::Mode {#mode-prop}

Controls the state this object will be monitoring and extracting its contents from.

## Signal Documentation {#signal-documentation}

### contentChanged() {#contentChanged-signal}

> **Note:** The corresponding handler is `onContentChanged`.

### modeChanged(QClipboard::Mode *mode*) {#modeChanged-signal}

> **Note:** The corresponding handler is `onModeChanged`.

## Method Documentation {#method-documentation}

### void clear() {#clear-method}

*See also* QClipboard::clear()

### variant contentFormat(string *format*) {#contentFormat-method}

Returns Output based on the mimetype.

This may be a list of URLs, text, image data, or use [QMimeData::data](https://doc.qt.io/qt-6/qmimedata.html#data).

`format` mimetype string
