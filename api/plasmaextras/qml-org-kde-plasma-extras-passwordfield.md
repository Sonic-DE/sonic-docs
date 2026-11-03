---
title: "PasswordField QML Type"
description: "This is a standard password text field."
---

# PasswordField QML Type

This is a standard password text field. [More...](#details)

- Import Statement: import org.kde.plasma.extras
- Inherits: [ActionTextField](qml-org-kde-plasma-extras-actiontextfield.md)

## Detailed Description {#details}

Example usage for the password field component:

```qml
import org.kde.plasma.extras as PlasmaExtras

PlasmaExtras.PasswordField {
    id: passwordField
    onAccepted: {
        // check if passwordField.text is valid
    }
}
```

## Property Documentation {#property-documentation}

### showPassword : bool {#showPassword-prop}

This property holds whether we show the clear text password.

By default, it's false.
