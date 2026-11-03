---
title: "FormPlaceholderMessageDelegate QML Type"
description: "A placeholder message indicating that a FormCard is empty. This type was introduced in Qt 6.9."
---

# FormPlaceholderMessageDelegate QML Type

A placeholder message indicating that a [FormCard](qml-org-kde-kirigamiaddons-formcard-formcard.md) is empty. This type was introduced in Qt 6.9. [More...](#details)

- Import Statement: import org.kde.kirigamiaddons.formcard
- Since: Qt 6.9
- Inherits: [AbstractFormDelegate](qml-org-kde-kirigamiaddons-formcard-abstractformdelegate.md)

## Detailed Description {#details}

Example usage:

```qml
import org.kde.kirigamiaddons.formcard as FormCard

FormCard.FormCardPage {
    FormCard.FormHeader {
        title: i18nc("@title:group", "Items")
    }

    FormCard.FormCard {
        FormCard.FormPlaceholderMessageDelegate {
            text: i18nc("@info:placeholder", "There are no items in this list")
            visible: repeater.count === 0
        }

        Repeater {
            id: repeater
            model: [ ... ]
            delegate: [ ... ]
        }

        FormCard.FormDelegateSeparator {}

        FormCard.FormButtonDelegate {
            text: i18nc("@action:button", "Add Item")
            icon.name: "list-add-symbolic"
        }
    }
}
```

## Property Documentation {#property-documentation}

### explanation : string {#explanation-prop}

This property holds the smaller explanatory text to show below the larger title-style text.

Useful for providing a user-friendly explanation on how to proceed.

Optional; if not defined, the message will have no supplementary explanatory text.

### hoveredLink : alias {#hoveredLink-prop}

This property holds the link embedded in the explanatory message text that the user is hovering over.

## Signal Documentation {#signal-documentation}

### linkActivated(string *link*) {#linkActivated-signal}

This signal is emitted when a `link` is clicked or tapped in the explanatory message text.

> **Note:** The corresponding handler is `onLinkActivated`.

### linkHovered(string *link*) {#linkHovered-signal}

This signal is emitted when a `link` is hovered in the explanatory message text.

> **Note:** The corresponding handler is `onLinkHovered`.
