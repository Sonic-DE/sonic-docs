---
title: "Heading QML Type"
description: "A pre-formatted label used for titles and section headers."
---

# Heading QML Type

A pre-formatted label used for titles and section headers. [More...](#details)

- Import Statement: import org.kde.kirigami
- Inherits: [Label](https://doc.qt.io/qt-6/qml-qtquick-controls-label.html)

## Detailed Description {#details}

Use this component for titles and section headers. The characteristics of the text will be automatically set according to the `Kirigami.Theme`.

The most important property is [text](https://doc.qt.io/qt-6/qml-qtquick-text.html#text-prop); use this to set the heading text to be displayed.

Example usage:

```cpp
import QtQuick.Layouts
import QtQuick.Controls as QQC2
import org.kde.kirigami as Kirigami
[...]
ColumnLayout {
    spacing: 0

    Kirigami.Heading {
        Layout.fillWidth: true
        wrapMode: Text.Wrap
        text: "Apples in the sunlight"
        level: 2
    }
    QQC2.Label {
        Layout.fillWidth: true
        wrapMode: Text.Wrap
        text: "And this is why apples are amazing: let me tell you a story about this one time I was napping below a tree…"
    }
  [...]
}
```

## Property Documentation {#property-documentation}

### level : int {#level-prop}

This property holds the level of the heading, which determines its size.

This property holds the level, which determines how large the header is.

Acceptable values range from 1 (big) to 5 (small).

default: 1

### type : enumeration {#type-prop}

This property holds the heading type.

The type of heading. This can be:

- Kirigami.Heading.Type.Normal: Create a normal heading.
- Kirigami.Heading.Type.Primary: Makes the heading more prominent. Useful when making the heading bigger is not enough.
- Kirigami.Heading.Type.Secondary: Makes the heading less prominent. Useful when an heading is for a less important section in an application.

default: Kirigami.Heading.Type.Normal
