---
title: "FormTextAreaDelegate QML Type"
description: "A Form delegate that corresponds to a text area."
---

# FormTextAreaDelegate QML Type

A Form delegate that corresponds to a text area. [More...](#details)

- Import Statement: import org.kde.kirigamiaddons.formcard
- Inherits: [AbstractFormDelegate](qml-org-kde-kirigamiaddons-formcard-abstractformdelegate.md)

## Detailed Description {#details}

```qml
FormCard.FormHeader {
    title: "Information"
}

FormCard.FormCard {
    FormCard.FormTextAreaDelegate {
        label: "Account name"
    }
}
```

## Property Documentation {#property-documentation}

### \[default: ""\] description : string {#description-prop}

A label containing secondary text that appears under the inherited text property.

This provides additional information shown in a faint gray color.

### fieldActiveFocus : bool {#fieldActiveFocus-prop}

This hold the [activeFocus](https://doc.qt.io/qt-6/qml-qtquick-item.html#activeFocus-prop) state of the internal [TextArea](https://doc.qt.io/qt-6/qml-qtquick-controls-textarea.html).

### inputMethodHints : enumeration {#inputMethodHints-prop}

This property holds the [inputMethodHints](https://doc.qt.io/qt-6/qml-qtquick-textedit.html#inputMethodHints-prop) of the internal [TextArea](https://doc.qt.io/qt-6/qml-qtquick-controls-textarea.html).

This consists of hints on the expected content or behavior of the text field, be it sensitive data, in a date format, or whether the characters will be hidden, for example.

*See also* [TextInput.inputMethodHints](https://doc.qt.io/qt-6/qml-qtquick-textinput.html#inputMethodHints-prop)

### \[required\] label : string {#label-prop}

A label containing primary text that appears above and to the left the text field.

### \[default: -1\] maximumLength : int {#maximumLength-prop}

The maximum length of the text inside the [TextArea](https://doc.qt.io/qt-6/qml-qtquick-controls-textarea.html) if maxLength \> 0.

### placeholderText : string {#placeholderText-prop}

This property holds the [placeholderText](https://doc.qt.io/qt-6/qml-qtquick-controls-textarea.html#placeholderText-prop) of the internal [TextArea](https://doc.qt.io/qt-6/qml-qtquick-controls-textarea.html).

This consists of secondary text shown by default on the text field if no text has been written in it.

### readOnly : bool {#readOnly-prop}

This hold the [readOnly](https://doc.qt.io/qt-6/qml-qtquick-textedit.html#readOnly-prop) state of the internal [TextArea](https://doc.qt.io/qt-6/qml-qtquick-controls-textarea.html).

### status : var {#status-prop}

This property holds the current status message type of the text field.

This consists of an inline message with a colorful background and an appropriate icon.

The status property will affect the color of [statusMessage](qml-org-kde-kirigamiaddons-formcard-formtextareadelegate.md#statusMessage-prop) used.

Accepted values:

| Constant | Description |
| --- | --- |
| Kirigami.MessageType.Information | (blue color) |
| Kirigami.MessageType.Positive | (green color) |
| Kirigami.MessageType.Warning | (orange color) |
| Kirigami.MessageType.Error | (red color) |

default: Kirigami.[MessageType](../kirigami/messagetype.md).Information if [statusMessage](qml-org-kde-kirigamiaddons-formcard-formtextareadelegate.md#statusMessage-prop) is set, nothing otherwise.

*See also* Kirigami.MessageType

### \[default: ""\] statusMessage : string {#statusMessage-prop}

This property holds the current status message of the text field.

If this property is not set, no status will be shown.

## Signal Documentation {#signal-documentation}

### editingFinished() {#editingFinished-signal}

This signal is emitted when the Return or Enter key is pressed or the text input loses focus.

Note that if there is a validator or inputMask set on the text input and enter/return is pressed, this signal will only be emitted if the input follows the inputMask and the validator returns an acceptable state.

> **Note:** The corresponding handler is `onEditingFinished`.

## Method Documentation {#method-documentation}

### clear() {#clear-method}

Clears the contents of the text input and resets partial text input from an input method.

### insert(*position*, *text*) {#insert-method}

Inserts `text` into the [TextInput](https://doc.qt.io/qt-6/qml-qtquick-textinput.html) at `position`.
