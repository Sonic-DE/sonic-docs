---
title: "FormCheckDelegate QML Type"
description: "A Form delegate that corresponds to a checkbox."
---

# FormCheckDelegate QML Type

A Form delegate that corresponds to a checkbox. [More...](#details)

- Import Statement: import org.kde.kirigamiaddons.formcard

## Detailed Description {#details}

This component is used for individual settings that can be toggled on, off, or tristate, typically in conjunction with multiple other checkboxes.

Use the inherited [AbstractButton.text](https://doc.qt.io/qt-6/qml-qtquick-controls-abstractbutton.html#text-prop) property to define the main text of the checkbox.

If you need a purely on/off toggle for a single setting, consider using a [FormSwitchDelegate](qml-org-kde-kirigamiaddons-formcard-formswitchdelegate.md).

If you need multiple toggles for the same setting, use a [FormRadioDelegate](qml-org-kde-kirigamiaddons-formcard-formradiodelegate.md) instead.

If you need multiple values for the same setting, use a [FormComboBoxDelegate](qml-org-kde-kirigamiaddons-formcard-formcomboboxdelegate.md) instead.

*See also* [AbstractButton](https://doc.qt.io/qt-6/qml-qtquick-controls-abstractbutton.html), [FormSwitchDelegate](qml-org-kde-kirigamiaddons-formcard-formswitchdelegate.md), [FormComboBoxDelegate](qml-org-kde-kirigamiaddons-formcard-formcomboboxdelegate.md), [FormRadioDelegate](qml-org-kde-kirigamiaddons-formcard-formradiodelegate.md)

## Property Documentation {#property-documentation}

### description : string {#description-prop}

A label containing secondary text that appears under the inherited text property.

This provides additional information shown in a faint gray color.

### descriptionItem : Label {#descriptionItem-prop}

This property allows one to override the internal description item with a custom component.

### leading : Item {#leading-prop}

This property holds an item that will be displayed to the left of the delegate's contents.

### leadingPadding : real {#leadingPadding-prop}

This property holds the padding after the leading item.

### trailing : Item {#trailing-prop}

This property holds an item that will be displayed to the right of the delegate's contents.

### trailingPadding : real {#trailingPadding-prop}

This property holds the padding before the trailing item.
