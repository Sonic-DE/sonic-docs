---
title: "DoubleFloatingButton QML Type"
description: "This component allows to display two buttons at the bottom of a page."
---

# DoubleFloatingButton QML Type

This component allows to display two buttons at the bottom of a page. [More...](#details)

- Import Statement: import org.kde.kirigamiaddons.components

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

## Property Documentation {#property-documentation}

### \[default: 0\] bottomMargin : real {#bottomMargin-prop}

Extra clickable area that adjusts both paddings and insets.

### leadingAction : Kirigami.Action {#leadingAction-prop}

This property holds the leading action.

### \[default: 0\] leftMargin : real {#leftMargin-prop}

Extra clickable area that adjusts both paddings and insets.

### \[default: 0\] margins : real {#margins-prop}

Extra clickable area that adjusts both paddings and insets.

### \[default: 0\] rightMargin : real {#rightMargin-prop}

Extra clickable area that adjusts both paddings and insets.

### \[default: 0\] topMargin : real {#topMargin-prop}

Extra clickable area that adjusts both paddings and insets.

### trailingAction : Kirigami.Action {#trailingAction-prop}

This property holds the trailing action.
