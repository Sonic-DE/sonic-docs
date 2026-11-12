---
title: "DoubleFloatingButton QML Type"
description: "This component allows one to display two buttons at the bottom of a page."
---

# DoubleFloatingButton QML Type

This component allows one to display two buttons at the bottom of a page. [More...](#details)

- Import Statement: import org.kde.kirigamiaddons.components
- Inherits: [DoubleFloatingButton](qml-org-kde-kirigamiaddons-components-templates-doublefloatingbutton.md)

## Detailed Description {#details}

```qml
import QtQuick
import QtQuick.Controls as QQC2
import org.kde.kirigami as Kirigami
import org.kde.kirigamiaddons.components as KirigamiComponents

Kirigami.ScrollablePage {
    ListView {
        model: []
        delegate: QQC2.ItemDelegate {}

        KirigamiComponents.DoubleFloatingButton {
            anchors {
                right: parent.right
                bottom: parent.bottom
                margins: Kirigami.Units.largeSpacing
            }

            leadingAction: Kirigami.Action {
                text: "Zoom Out"
                icon.name: "list-remove"
            }

            trailingAction: Kirigami.Action {
                text: "Zoom In"
                icon.name: "list-add"
            }
        }
    }
}
```
