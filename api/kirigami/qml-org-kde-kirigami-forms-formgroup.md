---
title: "FormGroup QML Type"
description: "The container class that identifies a container of related controls in a form. This type was introduced in Qt 6.24."
---

# FormGroup QML Type

The container class that identifies a container of related controls in a form. This type was introduced in Qt 6.24. [More...](#details)

- Import Statement: import org.kde.kirigami.forms
- Since: Qt 6.24
- Inherits: [Item](https://doc.qt.io/qt-6/qml-qtquick-item.html)

## Detailed Description {#details}

This element should always be positioned in a Form. It is used to group together related form controls, to separate different settings categories. Every form should always have at least one [FormGroup](qml-org-kde-kirigami-forms-formgroup.md).

A [FormGroup](qml-org-kde-kirigami-forms-formgroup.md) should contain only elements of type [FormEntry](qml-org-kde-kirigami-forms-formentry.md) or [FormSeparator](qml-org-kde-kirigami-forms-formseparator.md) (or derivates)

Example usage:

```qml
import QtQuick.Controls as QQC
import org.kde.kirigami as Kirigami

Kirigami.Form {
  Kirigami.FormGroup {
      title: "Global Settings"
      Kirigami.FormEntry {
          contentItem: QQC.CheckBox {
              text: "Show Sidebar"
          }
      }
      Kirigami.FormEntry {
          contentItem: QQC.CheckBox {
              text: "Auto Save"
          }
      }
  }
  Kirigami.FormGroup {
      title: "Theme Options"
      Kirigami.FormEntry {
          title: "Colors"
          contentItem: QQC.CheckBox {
              text: "Dark Theme"
          }
      }
      Kirigami.FormSeparator {}
      Kirigami.FormEntry {
          contentItem: QQC.CheckBox {
              text: "High Contrast"
          }
      }
      ...
  }
}
```

*See also* [Form](qml-org-kde-kirigami-forms-form.md), [FormEntry](qml-org-kde-kirigami-forms-formentry.md)

## Property Documentation {#property-documentation}

### title : string {#title-prop}

Group title.

If set, a title will be displayed on top of the form section, useful for semantically group different settings categories
