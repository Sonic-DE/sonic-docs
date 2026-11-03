---
title: "Dialog QML Type"
description: "Creates a Plasma themed top level window that can contain any QML component."
---

# Dialog QML Type

Creates a Plasma themed top level window that can contain any QML component. [More...](#details)

- Import Statement: import org.kde.plasma.core
- In C++: [Dialog](../plasmaquick/plasmaquick-dialog.md)

## Detailed Description {#details}

It can be automatically positioned relative to a visual parent The dialog will resize to the size of the main item

```qml
import QtQuick 2.0
 import org.kde.plasma.core as PlasmaCore
 Item {
    PlasmaCore.Dialog {
         visible: true
         mainItem: Item {
             width: 500
             height: 500

             Text {
                 anchors.centerIn: parent
                 color: "red"
                 text: "text"
             }
         }
     }
}
```
