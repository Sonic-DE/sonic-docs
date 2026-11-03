---
title: "FormColorDelegate QML Type"
description: "A FormCard delegate for colors."
---

# FormColorDelegate QML Type

A [FormCard](qml-org-kde-kirigamiaddons-formcard-formcard.md) delegate for colors. [More...](#details)

- Import Statement: import org.kde.kirigamiaddons.formcard
- Inherits: [AbstractFormDelegate](qml-org-kde-kirigamiaddons-formcard-abstractformdelegate.md)

## Detailed Description {#details}

Allow users to select colors. By default "Color" is the default label but this can be overwritten with the text property.

```qml
FormCard.FormCard {
    FormCard.FormColorDelegate {
        color: "blue"
    }

    FormCard.FormDelegateSeparator {}

    FormCard.FormColorDelegate {
        text: i18nc("@label", "Active color")
        color: "blue"
    }
}
```

## Property Documentation {#property-documentation}

### color : color {#color-prop}

The currently selected color.
