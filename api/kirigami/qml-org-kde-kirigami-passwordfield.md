---
title: "PasswordField QML Type"
description: "This is a standard password text field."
---

# PasswordField QML Type

This is a standard password text field. [More...](#details)

- Import Statement: import org.kde.kirigami
- Inherits: [ActionTextField](qml-org-kde-kirigami-actiontextfield.md)

## Detailed Description {#details}

Example usage:

```cpp
import org.kde.kirigami as Kirigami

Kirigami.PasswordField {
    id: passwordField
    onAccepted: {
        // check if passwordField.text is valid
    }
}
```

## Property Documentation {#property-documentation}

### showPassword : bool {#showPassword-prop}

This property tells whether the password will be displayed in cleartext rather than obfuscated.

default: `false`
