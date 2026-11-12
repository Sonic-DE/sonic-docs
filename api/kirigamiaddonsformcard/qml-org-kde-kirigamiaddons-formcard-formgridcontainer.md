---
title: "FormGridContainer QML Type"
description: "This component render a grid of small cards."
---

# FormGridContainer QML Type

This component render a grid of small cards. [More...](#details)

- Import Statement: import org.kde.kirigamiaddons.formcard
- Inherits: [FormGridContainer](qml-org-kde-kirigamiaddons-formcard-templates-formgridcontainer.md)

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
