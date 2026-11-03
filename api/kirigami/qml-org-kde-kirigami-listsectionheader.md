---
title: "ListSectionHeader QML Type"
description: "A section delegate for the primitive ListView component."
---

# ListSectionHeader QML Type

A section delegate for the primitive [ListView](https://doc.qt.io/qt-6/qml-qtquick-listview.html) component. [More...](#details)

- Import Statement: import org.kde.kirigami
- Inherits: [ItemDelegate](https://doc.qt.io/qt-6/qml-qtquick-controls-itemdelegate.html)

## Detailed Description {#details}

It's intended to make all listviews look coherent.

Any additional content items will be positioned in a row at the trailing side of this component.

Example usage:

```cpp
import QtQuick
import QtQuick.Controls as QQC2
import org.kde.kirigami as Kirigami

ListView {
    section.delegate: Kirigami.ListSectionHeader {
        text: section

        QQC2.Button {
            text: "Button 1"
        }
        QQC2.Button {
            text: "Button 2"
        }
    }
}
```
