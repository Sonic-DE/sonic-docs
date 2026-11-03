---
title: "FormSeparator QML Type"
description: "An item used to separate entries within a FormGroup. This type was introduced in Qt 6.24."
---

# FormSeparator QML Type

An item used to separate entries within a [FormGroup](qml-org-kde-kirigami-forms-formgroup.md). This type was introduced in Qt 6.24. [More...](#details)

- Import Statement: import org.kde.kirigami.forms
- Since: Qt 6.24
- Inherits: [Item](https://doc.qt.io/qt-6/qml-qtquick-item.html)

## Detailed Description {#details}

This component is used when it's needed to separe entries within a [FormGroup](qml-org-kde-kirigami-forms-formgroup.md) for clarity, for instance if is needed to have separate subcategories within a [FormGroup](qml-org-kde-kirigami-forms-formgroup.md).

Example usage:

```qml
import QtQuick.Controls as QQC
import org.kde.kirigami as Kirigami

Kirigami.Form {
  Kirigami.FormGroup {
      title: "Theme Options"
      Kirigami.FormEntry {
          title: "Subsection 1"
          contentItem: QQC.CheckBox {
              text: "Dark Theme"
          }
      }
      Kirigami.FormSeparator {}
      Kirigami.FormEntry {
          title: "Subsection 2"
          contentItem: QQC.CheckBox {
              text: "High Contrast"
          }
      }
      ...
  }
}
```

*See also* [FormEntry](qml-org-kde-kirigami-forms-formentry.md), [FormGroup](qml-org-kde-kirigami-forms-formgroup.md)
