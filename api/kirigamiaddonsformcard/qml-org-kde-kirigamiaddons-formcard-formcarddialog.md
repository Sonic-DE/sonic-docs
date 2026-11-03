---
title: "FormCardDialog QML Type"
description: "A dialog designed to use FormCard delegates as its content."
---

# FormCardDialog QML Type

A dialog designed to use [FormCard](qml-org-kde-kirigamiaddons-formcard-formcard.md) delegates as its content. [More...](#details)

- Import Statement: import org.kde.kirigamiaddons.formcard
- Inherits: [Dialog](https://doc.qt.io/qt-6/qml-qtquick-controls-dialog.html)

## Detailed Description {#details}

```qml
import org.kde.kirigamiaddons.formcard as FormCard
import QtQuick.Controls

FormCard.FormCardDialog {
    title: "Add Thingy"
    autoSeparators: true

    standardButtons: Dialog.Ok | Dialog.Cancel
    FormCard.FormTextFieldDelegate {
        label: i18nc("@label:textbox Notebook name", "Name:")
    }

    FormCard.FormButtonDelegate {
        text: i18nc("@action:button", "Color")
        icon.name: "color-picker"
    }

    FormCard.FormButtonDelegate {
        text: i18nc("@action:button", "Icon")
        icon.name: "preferences-desktop-emoticons"
    }
}
```

## Property Documentation {#property-documentation}

### \[default: false\] autoSeparators : bool {#autoSeparators-prop}

Whether to insert a [FormDelegateSeparator](qml-org-kde-kirigamiaddons-formcard-formdelegateseparator.md) between visible delegates.

This also works for delegates created by a Repeater. Do not add explicit separators when this property is enabled.
