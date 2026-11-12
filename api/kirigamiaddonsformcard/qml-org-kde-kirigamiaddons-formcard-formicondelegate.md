---
title: "FormIconDelegate QML Type"
description: "A FormCard delegate for icons."
---

# FormIconDelegate QML Type

A [FormCard](qml-org-kde-kirigamiaddons-formcard-templates-formcard.md) delegate for icons. [More...](#details)

- Import Statement: import org.kde.kirigamiaddons.formcard
- Inherits: [AbstractFormDelegate](qml-org-kde-kirigamiaddons-formcard-abstractformdelegate.md)

## Detailed Description {#details}

Allow users to select icons. By default "Icon" is the default label but this can be overwritten with the \`text\` property.

```cpp
FormCard.FormCard {
    FormCard.FormIconDelegate {}

    FormCard.FormDelegateSeparator {}

    FormCard.FormIconDelegate {
        text: I18n.i18nc("@label", "Active icon")
        iconName: "actor-symbolic"
    }
}
```

> **Note:** This element is readonly on Android.

## Property Documentation {#property-documentation}

### iconName : alias {#iconName-prop}

This property holds the name of the selected icon.
