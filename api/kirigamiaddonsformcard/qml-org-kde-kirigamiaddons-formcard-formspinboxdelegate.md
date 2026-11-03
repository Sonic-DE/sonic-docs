---
title: "FormSpinBoxDelegate QML Type"
description: "A Form delegate that corresponds to a spinbox."
---

# FormSpinBoxDelegate QML Type

A Form delegate that corresponds to a spinbox. [More...](#details)

- Import Statement: import org.kde.kirigamiaddons.formcard
- Inherits: [AbstractFormDelegate](qml-org-kde-kirigamiaddons-formcard-abstractformdelegate.md)

## Detailed Description {#details}

This component is used to select a number. By default, the spinbox will be initialized with a minimum of 0 and a maximum of 99.

Example code:

```qml
FormCard.FormCardHeader {
    title: "Information"
}

FormCard.FormCard {
    FormCard.FormSpinBoxDelegate {
        label: "Amount"
    }
}
```

## Property Documentation {#property-documentation}

### \[default: ""\] description : string {#description-prop}

A label containing secondary text that appears under the inherited text property.

This provides additional information shown in a faint gray color.

### displayText : string {#displayText-prop}

This property holds the [displayText](https://doc.qt.io/qt-6/qml-qtquick-controls-spinbox.html#displayText-prop) of the internal spinbox.

### fieldActiveFocus : bool {#fieldActiveFocus-prop}

The [activeFocus](https://doc.qt.io/qt-6/qml-qtquick-item.html#activeFocus-prop) state of the internal spinbox.

### from : int {#from-prop}

This property holds the [from](https://doc.qt.io/qt-6/qml-qtquick-controls-spinbox.html#from-prop) of the internal spinbox.

### inputMethodComposing : bool {#inputMethodComposing-prop}

This property holds the [inputMethodComposing](https://doc.qt.io/qt-6/qml-qtquick-controls-spinbox.html#inputMethodComposing-prop) of the internal spinbox.

### inputMethodHints : enumeration {#inputMethodHints-prop}

This property holds the [inputMethodHints](https://doc.qt.io/qt-6/qml-qtquick-controls-spinbox.html#inputMethodHints-prop) of the internal spinbox.

### \[required\] label : string {#label-prop}

A label that appears above the spinbox.

### \[default: null\] leading : Item {#leading-prop}

This property holds an item that will be displayed before the spinbox.

### status : var {#status-prop}

This property holds the current type of status displayed in the text field.

Depending on the status of the text field, the [statusMessage](qml-org-kde-kirigamiaddons-formcard-formspinboxdelegate.md#statusMessage-prop) property will look different.

Accepted values:

| Constant |
| --- |
| Kirigami.MessageType.Information |
| Kirigami.MessageType.Positive |
| Kirigami.MessageType.Warning |
| Kirigami.MessageType.Error |

*See also* Kirigami.MessageType

### \[default: ""\] statusMessage : string {#statusMessage-prop}

This property holds the current status message of the text field.

### stepSize : int {#stepSize-prop}

This property holds the [stepSize](https://doc.qt.io/qt-6/qml-qtquick-controls-spinbox.html#stepSize-prop) of the internal spinbox.

### textFromValue : function {#textFromValue-prop}

This property holds the [textFromValue](https://doc.qt.io/qt-6/qml-qtquick-controls-spinbox.html#textFromValue-prop) of the internal spinbox.

### to : int {#to-prop}

This property holds the [to](https://doc.qt.io/qt-6/qml-qtquick-controls-spinbox.html#to-prop) of the internal spinbox.

### \[default: null\] trailing : Item {#trailing-prop}

This property holds an item that will be displayed after the delegate's contents.

### validator : Validator {#validator-prop}

This property holds the [validator](https://doc.qt.io/qt-6/qml-qtquick-controls-spinbox.html#validator-prop) of the internal spinbox.

### value : int {#value-prop}

This property holds the [value](https://doc.qt.io/qt-6/qml-qtquick-controls-spinbox.html#value-prop) of the internal spinbox.

### valueFromText : function {#valueFromText-prop}

This property holds the [valueFromText](https://doc.qt.io/qt-6/qml-qtquick-controls-spinbox.html#valueFromText-prop) of the internal spinbox.

### wrap : bool {#wrap-prop}

This property holds the [wrap](https://doc.qt.io/qt-6/qml-qtquick-controls-spinbox.html#wrap-prop) of the internal spinbox.

## Signal Documentation {#signal-documentation}

### valueModified() {#valueModified-signal}

This signal is emitted when the spin box value has been interactively modified by the user.

By either touch, mouse, wheel, or keys. In the case of interaction via keyboard, the signal is only emitted when the text has been accepted; meaning when the enter or return keys are pressed, or the input field loses focus.

> **Note:** The corresponding handler is `onValueModified`.

## Method Documentation {#method-documentation}

### decrease() {#decrease-method}

Decreases the value by [stepSize](qml-org-kde-kirigamiaddons-formcard-formspinboxdelegate.md#stepSize-prop), or 1 if [stepSize](qml-org-kde-kirigamiaddons-formcard-formspinboxdelegate.md#stepSize-prop) is not defined.

### increase() {#increase-method}

Increases the value by [stepSize](qml-org-kde-kirigamiaddons-formcard-formspinboxdelegate.md#stepSize-prop), or 1 if [stepSize](qml-org-kde-kirigamiaddons-formcard-formspinboxdelegate.md#stepSize-prop) is not defined.
