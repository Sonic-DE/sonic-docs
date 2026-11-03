---
title: "FormData QML Type"
description: "An attached property with information for decorating a FormLayout."
---

# FormData QML Type

An attached property with information for decorating a [FormLayout](qml-org-kde-kirigami-layouts-formlayout.md). [More...](#details)

- Import Statement: import org.kde.kirigami.layouts

## Detailed Description {#details}

It contains the text labels of fields and information about sections.

Some of its properties can be used with other Layout types.

```qml
import org.kde.kirigami as Kirigami

Kirigami.FormLayout {
   TextField {
      Kirigami.FormData.label: "User:"
   }
   TextField {
      Kirigami.FormData.label: "Password:"
   }
}
```

*See also* [FormLayout](qml-org-kde-kirigami-layouts-formlayout.md)

## Attached Property Documentation {#attached-property-documentation}

### FormData.buddyFor : Item {#buddyFor-attached-prop}

This property can only be used in conjunction with a [FormData::label](qml-org-kde-kirigami-layouts-formdata.md#label-attached-prop), often in a layout that is a child of a [FormLayout](qml-org-kde-kirigami-layouts-formlayout.md).

It then turns the item specified into a "buddy" of the label, making it work as if it were a child of the [FormLayout](qml-org-kde-kirigami-layouts-formlayout.md).

A buddy item is useful for instance when the label has a keyboard accelerator, which when triggered provides active keyboard focus to the buddy item.

By default buddy is the item that [FormData](qml-org-kde-kirigami-layouts-formdata.md) is attached to. Custom buddy can only be a direct child of that item; nested components are not supported at the moment.

```cpp
Kirigami.FormLayout {
    Layouts.ColumnLayout {
        // If the accelerator is in the letter S,
        // pressing Alt+S gives focus to the slider.
        Kirigami.FormData.label: "Slider label:"
        Kirigami.FormData.buddyFor: slider

        QQC2.Slider {
            id: slider
            from: 0
            to: 100
            value: 50
        }
    }
}
```

### FormData.isSection : bool {#isSection-attached-prop}

If true, the child item of a [FormLayout](qml-org-kde-kirigami-layouts-formlayout.md) becomes a section separator, and may have different looks:

To make it just a space between two fields, just put an empty item with `FormData.isSection`:

```cpp
TextField {
    Kirigami.FormData.label: "Label:"
}
Item {
    Kirigami.FormData.isSection: true
}
TextField {
    Kirigami.FormData.label: "Label:"
}
```

To make it a space with a section title:

```cpp
TextField {
    Kirigami.FormData.label: "Label:"
}
Item {
    Kirigami.FormData.label: "Section Title"
    Kirigami.FormData.isSection: true
}
TextField {
    Kirigami.FormData.label: "Label:"
}
```

To make it a space with a section title and a separator line:

```cpp
TextField {
    Kirigami.FormData.label: "Label:"
}
Kirigami.Separator {
    Kirigami.FormData.label: "Section Title"
    Kirigami.FormData.isSection: true
}
TextField {
    Kirigami.FormData.label: "Label:"
}
```

### FormData.label : string {#label-attached-prop}

The label for a [FormLayout](qml-org-kde-kirigami-layouts-formlayout.md) field

### FormData.labelAlignment : int {#labelAlignment-attached-prop}

The alignment for the label of a [FormLayout](qml-org-kde-kirigami-layouts-formlayout.md) field
