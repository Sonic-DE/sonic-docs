---
title: "ActionTextField QML Type"
description: "This is advanced textfield. It is recommended to use this class when there is a need to create a create a textfield with action buttons (e.g a clear action)."
---

# ActionTextField QML Type

This is advanced textfield. It is recommended to use this class when there is a need to create a create a textfield with action buttons (e.g a clear action). [More...](#details)

- Import Statement: import org.kde.plasma.extras
- Inherits: [TextField](../plasmacomponents/qml-org-kde-plasma-components-textfield.md)
- Inherited By: [PasswordField](qml-org-kde-plasma-extras-passwordfield.md) and [SearchField](qml-org-kde-plasma-extras-searchfield.md)

## Detailed Description {#details}

For common pattern like, a search field or a password field, prefer using the more specific [SearchField](qml-org-kde-plasma-extras-searchfield.md) or [PasswordField](qml-org-kde-plasma-extras-passwordfield.md).

Example usage for a search field:

```qml
import QtQuick.Controls as QQC2
import org.kde.plasma.extras as PlasmaExtras

PlasmaExtras.ActionTextField {
    id: searchField

    placeholderText: "Search…"

    focusSequence: StandardKey.Find

    rightActions: [
        QQC2.Action {
            icon.name: "edit-clear"
            enabled: searchField.text !== ""
            onTriggered: {
                searchField.clear()
                searchField.accepted()
            }
        }
    ]

    onAccepted: console.log("Search text is " + searchField.text)
}
```

## Property Documentation {#property-documentation}

### focusSequence : keysequence {#focusSequence-prop}

This property holds a shortcut sequence that will focus the text field.

### \[since 6.7\] focusSequences : keysequence {#focusSequences-prop}

This property holds multiple shortcut sequences that will focus the text field.

By default no shortcut is set.

This property was introduced in Qt 6.7.

### leftActions : list\<T.Action\> {#leftActions-prop}

This property holds a list of actions that will be displayed on the left side of the text field.

By default this list is empty.

### rightActions : list\<T.Action\> {#rightActions-prop}

This property holds a list of actions that will be displayed on the right side of the text field.

By default this list is empty.
