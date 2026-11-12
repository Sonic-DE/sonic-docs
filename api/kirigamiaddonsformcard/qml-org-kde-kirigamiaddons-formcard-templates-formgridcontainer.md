---
title: "FormGridContainer QML Type"
description: "This component render a grid of small cards."
---

# FormGridContainer QML Type

This component render a grid of small cards. [More...](#details)

- Import Statement: import org.kde.kirigamiaddons.formcard.templates
- Inherits: [Item](https://doc.qt.io/qt-6/qml-qtquick-item.html) (QtQuick)
- Inherited By: [FormGridContainer](qml-org-kde-kirigamiaddons-formcard-formgridcontainer.md) (org.kde.kirigamiaddons.formcard)

## Detailed Description {#details}

This is used to display multiple information in a [FormCard](qml-org-kde-kirigamiaddons-formcard-templates-formcard.md).[FormLayout](../kirigami/qml-org-kde-kirigami-layouts-formlayout.md) without taking too much vertical space.

Form delegates can also be placed directly inside the container. In this mode, delegates are displayed in a two-column grid, each with its own card background.

```qml
import org.kde.kirigamiaddons.formcard as FormCard

FormCard.FormGridContainer {
    id: container

    Layout.topMargin: Kirigami.Units.largeSpacing
    Layout.fillWidth: true

    infoCards: [
        FormCard.FormGridContainer.InfoCard {
            title: "42"
            subtitle: i18nc("@info:Number of Posts", "Posts")
        },
        FormCard.FormGridContainer.InfoCard {
            title: "42"
            subtitle: i18nc("@info:Number of followers.", "Followers")
        }
    ]
}
```

```qml
import org.kde.kirigamiaddons.formcard as FormCard

FormCard.FormGridContainer {
    FormCard.FormTextDelegate {
        text: "Name"
    }
    FormCard.FormSwitchDelegate {
        text: "Enable notifications"
    }
}
```

## Property Documentation {#property-documentation}

### \[default: 0\] bottomPadding : real {#bottomPadding-prop}

Padding property used around the content edges.

### \[read-only\] cardWidthRestricted : bool {#cardWidthRestricted-prop}

This property holds whether the card's width is being restricted.

### delegates : list\<Item\> {#delegates-prop}

The form delegates displayed in the container. When left empty, controls added as children are included, even after construction.

### \[default: 0\] horizontalPadding : real {#horizontalPadding-prop}

Padding property used around the content edges.

### \[default: 0\] leftPadding : real {#leftPadding-prop}

Padding property used around the content edges.

### \[default: Kirigami.Units.gridUnit \* 30\] maximumWidth : real {#maximumWidth-prop}

This property holds the maximum width of the grid.

### \[default: 0\] padding : real {#padding-prop}

Padding property used around the content edges.

### \[default: 0\] rightPadding : real {#rightPadding-prop}

Padding property used around the content edges.

### \[default: 0\] topPadding : real {#topPadding-prop}

Padding property used around the content edges.

### \[default: 0\] verticalPadding : real {#verticalPadding-prop}

Padding property used around the content edges.
