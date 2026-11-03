---
title: "FormRadioDelegate QML Type"
description: "A Form delegate that corresponds to a radio button."
---

# FormRadioDelegate QML Type

A Form delegate that corresponds to a radio button. [More...](#details)

- Import Statement: import org.kde.kirigamiaddons.formcard

## Detailed Description {#details}

This component is used for creating multiple on/off toggles for the same setting. In other words, by grouping multiple radio buttons under the same parent, only one of the radio buttons should be checkable and applied to a setting.

Use the inherited [AbstractButton.text](https://doc.qt.io/qt-6/qml-qtquick-controls-abstractbutton.html#text-prop) property to define the main text of the radio button.

If you need multiple values for the same setting, use a [FormComboBoxDelegate](qml-org-kde-kirigamiaddons-formcard-formcomboboxdelegate.md) instead.

If you need a purely on/off toggle for a single setting, use a [FormSwitchDelegate](qml-org-kde-kirigamiaddons-formcard-formswitchdelegate.md) instead.

If you need an on/off/tristate toggle, use a [FormCheckDelegate](qml-org-kde-kirigamiaddons-formcard-formcheckdelegate.md) instead.

*See also* [AbstractButton](https://doc.qt.io/qt-6/qml-qtquick-controls-abstractbutton.html), [FormSwitchDelegate](qml-org-kde-kirigamiaddons-formcard-formswitchdelegate.md), [FormCheckDelegate](qml-org-kde-kirigamiaddons-formcard-formcheckdelegate.md), [FormComboBoxDelegate](qml-org-kde-kirigamiaddons-formcard-formcomboboxdelegate.md)

## Property Documentation {#property-documentation}

### \[default: ""\] description : string {#description-prop}

A label containing secondary text that appears under the inherited text property.

This provides additional information shown in a faint gray color.

### descriptionItem : Label {#descriptionItem-prop}

This property allows to override the internal description item with a custom component.

### \[default: null\] leading : Item {#leading-prop}

This property holds an item that will be displayed to the left of the delegate's contents.

### \[default: Kirigami.Units.smallSpacing\] leadingPadding : real {#leadingPadding-prop}

This property holds the padding after the leading item.

### \[default: null\] trailing : Item {#trailing-prop}

This property holds an item that will be displayed after the delegate's contents.

### \[default: Kirigami.Units.smallSpacing\] trailingPadding : real {#trailingPadding-prop}

This property holds the padding before the trailing item.
