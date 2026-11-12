---
title: "BottomDrawer QML Type"
description: "A bottom drawer component with a drag indicator."
---

# BottomDrawer QML Type

A bottom drawer component with a drag indicator. [More...](#details)

- Import Statement: import org.kde.kirigamiaddons.components
- Inherits: [BottomDrawer](qml-org-kde-kirigamiaddons-components-templates-bottomdrawer.md)

## Detailed Description {#details}

Example:

```qml
import org.kde.kirigamiaddons.formcard as FormCard
import org.kde.kirigamiaddons.components as Components

Components.BottomDrawer {
    id: drawer

    headerContentItem: Kirigami.Heading {
        text: "Drawer"
    }

    ColumnLayout {
        spacing: 0

        FormCard.FormButtonDelegate {
            text: "Action 1"
            icon.name: "list-add-symbolic"
            onClicked: {
                doSomething()
                drawer.close()
            }
        }

        FormCard.FormButtonDelegate {
            text: "Action 2"
            icon.name: "list-remove-symbolic"
            onClicked: {
                doSomething()
                drawer.close()
            }
        }
    }
}
```

A drawer with a profile header and a scrollable list:

```qml
Components.BottomDrawer {
    id: drawer
    width: QQC2.ApplicationWindow.window.width

    headerContentItem: RowLayout {
        spacing: Kirigami.Units.smallSpacing

        Components.Avatar {
            name: "World"
        }

        ColumnLayout {
            Layout.leftMargin: Kirigami.Units.largeSpacing
            Layout.fillWidth: true
            spacing: Kirigami.Units.smallSpacing

            Kirigami.Heading {
                text: "John Doe"
                Layout.fillWidth: true
            }
            QQC2.Label {
                text: "Last connection: 20.04.2042"
                Layout.fillWidth: true
            }
        }
    }

    QQC2.ScrollView {
        implicitHeight: Math.max(view.implicitHeight, QQC2.ApplicationWindow.window.height * 0.8)

        ListView {
            id: view

            model: 40
            clip: true

            delegate: Delegates.RoundedItemDelegate {
                required property int index

                text: "Item " + index
            }
        }
    }
}
```
