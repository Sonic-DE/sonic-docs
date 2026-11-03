---
title: "FormLayout QML Type"
description: "The base class for Form layouts conforming to the Kirigami Human Interface Guidelines."
---

# FormLayout QML Type

The base class for Form layouts conforming to the Kirigami Human Interface Guidelines. [More...](#details)

- Import Statement: import org.kde.kirigami.layouts
- Inherits: [Item](https://doc.qt.io/qt-6/qml-qtquick-item.html)

## Detailed Description {#details}

The layout consists of two columns: the left column contains only right-aligned labels provided by a [FormData](qml-org-kde-kirigami-layouts-formdata.md) attached property, the right column contains left-aligned child types.

Child types can be sectioned using an [QtQuick](https://doc.qt.io/qt-6/qtquick-qmlmodule.html).Item or Kirigami.Separator with a [FormData](qml-org-kde-kirigami-layouts-formdata.md) attached property, see FormLayoutAttached::isSection for details.

Example usage:

```qml
import QtQuick.Controls as QQC2
import org.kde.kirigami as Kirigami

Kirigami.FormLayout {
   QQC2.TextField {
      Kirigami.FormData.label: "Label:"
   }
   Kirigami.Separator {
       Kirigami.FormData.label: "Section Title"
       Kirigami.FormData.isSection: true
   }
   QQC2.TextField {
      Kirigami.FormData.label: "Label:"
   }
   QQC2.TextField {
   }
}
```

*See also* [FormData](qml-org-kde-kirigami-layouts-formdata.md)

## Property Documentation {#property-documentation}

### twinFormLayouts : list\<Item\> {#twinFormLayouts-prop}

If for some implementation reason multiple FormLayouts have to appear on the same page, they can have each other in twinFormLayouts, so they will vertically align with each other perfectly

### wideMode : bool {#wideMode-prop}

This property tells whether the form layout is in wide mode.

If true, the layout will be optimized for a wide screen, such as a desktop machine (the labels will be on a left column, the fields on a right column beside it), if false (such as on a phone) everything is laid out in a single column.

By default this property automatically adjusts the layout if there is enough screen space.

Set this to `true` for a convergent design, set this to `false` for a mobile-only design.
