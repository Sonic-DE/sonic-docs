---
title: "FormButtonDelegate QML Type"
description: "A Form delegate that corresponds to a clickable button."
---

# FormButtonDelegate QML Type

A Form delegate that corresponds to a clickable button. [More...](#details)

- Import Statement: import org.kde.kirigamiaddons.formcard
- Inherits: [AbstractFormDelegate](qml-org-kde-kirigamiaddons-formcard-abstractformdelegate.md)
- Inherited By: [FormLinkDelegate](qml-org-kde-kirigamiaddons-formcard-formlinkdelegate.md)

## Detailed Description {#details}

Use the inherited [AbstractButton.text](https://doc.qt.io/qt-6/qml-qtquick-controls-abstractbutton.html#text-prop) property to define the main text of the button.

The [trailingLogo](qml-org-kde-kirigamiaddons-formcard-formbuttondelegate.md#trailingLogo-prop) property (right-most side of the button) includes an arrow pointing to the right by default and cannot be overridden.

## Property Documentation {#property-documentation}

### description : string {#description-prop}

A label containing secondary text that appears under the inherited text property.

This provides additional information shown in a faint gray color.

This is supposed to be short text and the API user should avoid making it longer than two lines.

### descriptionItem : Label {#descriptionItem-prop}

This property allows overriding the internal description item with a custom component.

### \[default: null\] leading : Item {#leading-prop}

This property holds an item that will be displayed to the left of the delegate's contents.

### leadingPadding : real {#leadingPadding-prop}

This property holds the padding after the leading item.

It is recommended to use [Kirigami.Units](../kirigamiplatform/qml-org-kde-kirigami-platform-units.md) here instead of direct values.

*See also* [Kirigami.Units](../kirigamiplatform/qml-org-kde-kirigami-platform-units.md)

### \[default: null\] trailing : Item {#trailing-prop}

This property holds an item that will be displayed to the right of the delegate's contents.

### \[read-only\] trailingLogo : alias {#trailingLogo-prop}

This property holds an alias to the internal [FormArrow](qml-org-kde-kirigamiaddons-formcard-formarrow.md).

This allows hiding it completely or changing the direction (e.g. to implement a collapsible section).

### trailingPadding : real {#trailingPadding-prop}

This property holds the padding before the trailing item.

It is recommended to use [Kirigami.Units](../kirigamiplatform/qml-org-kde-kirigami-platform-units.md) here instead of direct values.

*See also* [Kirigami.Units](../kirigamiplatform/qml-org-kde-kirigami-platform-units.md)
