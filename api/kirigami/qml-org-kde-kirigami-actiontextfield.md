---
title: "ActionTextField QML Type"
description: "An advanced control to create custom textfields with inline buttons."
---

# ActionTextField QML Type

An advanced control to create custom textfields with inline buttons. [More...](#details)

- Import Statement: import org.kde.kirigami
- Inherits: [TextField](https://doc.qt.io/qt-6/qml-qtquick-controls-textfield.html)
- Inherited By: [PasswordField](qml-org-kde-kirigami-passwordfield.md) and [SearchField](qml-org-kde-kirigami-searchfield.md)

## Detailed Description {#details}

[ActionTextField](qml-org-kde-kirigami-actiontextfield.md) can display inline action buttons on the leading or trailing sides, and is used as the base class for other kinds of specialized text fields, including [SearchField](qml-org-kde-kirigami-searchfield.md) and [PasswordField](qml-org-kde-kirigami-passwordfield.md).

Each action's `text` property will be displayed in a tooltip on hover.

Example usage:

```cpp
import org.kde.kirigami as Kirigami

Kirigami.ActionTextField {
    id: inputField

    placeholderText: i18n("Enter name")

    rightActions: Kirigami.Action {
        icon.name: "edit-clear"
        visible: inputField.text.length > 0
        onTriggered: {
            inputField.clear();
            inputField.accepted();
        }
    }

    onAccepted: console.log("Entered text is " + inputField.text);
}
```

## Property Documentation {#property-documentation}

### focusSequence : keysequence {#focusSequence-prop}

This property holds a shortcut sequence that will focus the text field.

By default no shortcut is set.

### \[since 6.18\] focusSequences : keysequence {#focusSequences-prop}

This property holds multiple shortcut sequences that will focus the text field.

By default no shortcut is set.

This property was introduced in Qt 6.18.

### leftActions : list\<Action\> {#leftActions-prop}

This property holds a list of actions that will be displayed on the leading side of the text field.

By default this list is empty.

### rightActions : list\<Action\> {#rightActions-prop}

This property holds a list of actions that will be displayed on the trailing side of the text field.

By default this list is empty.
