---
title: "FormAction QML Type"
description: "A specialized FormEntry for a big clickable action. This type was introduced in Qt 6.24."
---

# FormAction QML Type

A specialized [FormEntry](qml-org-kde-kirigami-forms-formentry.md) for a big clickable action. This type was introduced in Qt 6.24. [More...](#details)

- Import Statement: import org.kde.kirigami.forms
- Since: Qt 6.24
- Inherits: [FormEntry](qml-org-kde-kirigami-forms-formentry.md)

## Detailed Description {#details}

This component is used when the Form needs entries that represent a big clickable action: they will act like a single big button and is controlled by its Action property. Never override the contentItem property for a [FormAction](qml-org-kde-kirigami-forms-formaction.md).

Example usage:

```qml
import QtQuick.Controls as QQC
import org.kde.kirigami as Kirigami

Kirigami.Form {
  Kirigami.FormGroup {
      title: "When Offline:"
      Kirigami.FormAction {
          action: Kirigami.Action {
              icon.name: "offline-settings"
              text: "Offline Settings"
              onTriggered: { Code to open that settings page here }
          }
      }
      ...
  }
}
```

*See also* [FormEntry](qml-org-kde-kirigami-forms-formentry.md)

## Property Documentation {#property-documentation}

### \[required\] action : T.Action {#action-prop}

The main action for this Entry

[FormAction](qml-org-kde-kirigami-forms-formaction.md) acts like a big button that represents and triggers it. The action icon and text properties will be displayed to the user in this control, and clicking anywhere on it will trigger the action.

### \[read-only\] triggerIcon : Primitives.IconPropertiesGroup {#triggerIcon-prop}

An icon to be displayed on the rightof this [FormEntry](qml-org-kde-kirigami-forms-formentry.md) which represents what kind of action this is. By default is "go-next-symbolic", which suggests this action is opening something else or that is going to replace the PAge it's in.
