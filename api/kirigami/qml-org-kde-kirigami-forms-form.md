---
title: "Form QML Type"
description: "The base class for Form conforming to the Kirigami Human Interface Guidelines. This type was introduced in Qt 6.24."
---

# Form QML Type

The base class for Form conforming to the Kirigami Human Interface Guidelines. This type was introduced in Qt 6.24. [More...](#details)

- Import Statement: import org.kde.kirigami.forms
- Since: Qt 6.24
- Inherits: [Item](https://doc.qt.io/qt-6/qml-qtquick-item.html)

## Detailed Description {#details}

This is the base element for forms, used for instance in settings pages. We usually have a Page that contains a single Form, which in turn contains one or more [FormGroup](qml-org-kde-kirigami-forms-formgroup.md), each formGroup containing one or more [FormEntry](qml-org-kde-kirigami-forms-formentry.md).

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

*See also* [FormGroup](qml-org-kde-kirigami-forms-formgroup.md), [FormEntry](qml-org-kde-kirigami-forms-formentry.md)
