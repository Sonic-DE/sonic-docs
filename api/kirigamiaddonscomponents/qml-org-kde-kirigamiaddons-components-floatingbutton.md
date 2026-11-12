---
title: "FloatingButton QML Type"
description: "This component is a button that can be displayed at the bottom of a page."
---

# FloatingButton QML Type

This component is a button that can be displayed at the bottom of a page. [More...](#details)

- Import Statement: import org.kde.kirigamiaddons.components
- Inherits: [FloatingButton](qml-org-kde-kirigamiaddons-components-templates-floatingbutton.md)

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

        KirigamiComponents.FloatingButton {
            anchors {
                right: parent.right
                bottom: parent.bottom
            }
            margins: Kirigami.Units.largeSpacing

            action: Kirigami.Action {
                text: "Add new item"
                icon.name: "list-add"
            }
        }
    }
}
```
