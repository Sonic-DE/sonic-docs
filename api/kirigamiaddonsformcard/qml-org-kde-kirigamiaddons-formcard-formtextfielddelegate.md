---
title: "FormTextFieldDelegate QML Type"
description: "A Form delegate that corresponds to a text field."
---

# FormTextFieldDelegate QML Type

A Form delegate that corresponds to a text field. [More...](#details)

- Import Statement: import org.kde.kirigamiaddons.formcard
- Inherits: [AbstractFormDelegate](qml-org-kde-kirigamiaddons-formcard-abstractformdelegate.md)

## Detailed Description {#details}

```qml
FormCard.FormHeader {
    title: "Information"
}

FormCard.FormCard {
    FormCard.FormTextFieldDelegate {
        label: "Account name"
    }

    FormCard.FormTextFieldDelegate {
        label: "Password"
        statusMessage: "Password incorrect"
        status: Kirigami.MessageType.Error
        echoMode: TextInput.Password
        text: "666666666"
    }

    FormCard.FormTextFieldDelegate {
        label: "Password"
        statusMessage: "Password match"
        text: "4242424242"
        status: Kirigami.MessageType.Positive
        echoMode: TextInput.Password
    }
}
```

## Property Documentation {#property-documentation}

### acceptableInput : bool {#acceptableInput-prop}

This property holds the [acceptableInput](https://doc.qt.io/qt-6/qml-qtquick-textinput.html#acceptableInput-prop) of the internal [TextField](https://doc.qt.io/qt-6/qml-qtquick-controls-textfield.html).

### cursorPosition : int {#cursorPosition-prop}

This property holds the [cursorPosition](https://doc.qt.io/qt-6/qml-qtquick-textinput.html#cursorPosition-prop) of the internal [TextField](https://doc.qt.io/qt-6/qml-qtquick-controls-textfield.html).

This property holds the position of the cursor in the text field. A value of 0 indicates that the cursor is at the beginning of the text field.

This property allows you to programmatically control and access the cursor position within the text field, which can be useful for integrating the [FormTextFieldDelegate](qml-org-kde-kirigamiaddons-formcard-formtextfielddelegate.md) component into your project.

*See also* [TextInput.cursorPosition](https://doc.qt.io/qt-6/qml-qtquick-textinput.html#cursorPosition-prop)

### \[default: ""\] description : string {#description-prop}

A label containing secondary text that appears under the inherited text property.

This provides additional information shown in a faint gray color.

### echoMode : enumeration {#echoMode-prop}

This property holds the [echoMode](https://doc.qt.io/qt-6/qml-qtquick-textinput.html#echoMode-prop) of the internal [TextField](https://doc.qt.io/qt-6/qml-qtquick-controls-textfield.html).

This consists of how the text inside the text field will be displayed to the user.

*See also* [TextInput.echoMode](https://doc.qt.io/qt-6/qml-qtquick-textinput.html#echoMode-prop)

### fieldActiveFocus : bool {#fieldActiveFocus-prop}

The [activeFocus](https://doc.qt.io/qt-6/qml-qtquick-item.html#activeFocus-prop) state of the internal [TextField](https://doc.qt.io/qt-6/qml-qtquick-controls-textfield.html).

### inputMethodHints : enumeration {#inputMethodHints-prop}

This property holds the [inputMethodHints](https://doc.qt.io/qt-6/qml-qtquick-textinput.html#inputMethodHints-prop) of the internal [TextField](https://doc.qt.io/qt-6/qml-qtquick-controls-textfield.html).

This consists of hints on the expected content or behavior of the text field, be it sensitive data, in a date format, or whether the characters will be hidden, for example.

*See also* [inputMethodHints](https://doc.qt.io/qt-6/qml-qtquick-textinput.html#inputMethodHints-prop)

### \[required\] label : string {#label-prop}

A label containing primary text that appears above the text field.

### maximumLength : int {#maximumLength-prop}

The [maximumLength](https://doc.qt.io/qt-6/qml-qtquick-textinput.html#maximumLength-prop) of the text inside the [TextField](https://doc.qt.io/qt-6/qml-qtquick-controls-textfield.html) if maxLength \> 0.

### placeholderText : string {#placeholderText-prop}

This property holds the [placeholderText](https://doc.qt.io/qt-6/qml-qtquick-controls-textfield.html#placeholderText-prop) of the internal [TextField](https://doc.qt.io/qt-6/qml-qtquick-controls-textfield.html).

This consists of secondary text shown by default on the text field if no text has been written in it.

### readOnly : bool {#readOnly-prop}

The [readOnly](https://doc.qt.io/qt-6/qml-qtquick-textinput.html#readOnly-prop) state of the internal [TextField](https://doc.qt.io/qt-6/qml-qtquick-controls-textfield.html).

### selectByMouse : bool {#selectByMouse-prop}

This property holds the [selectByMouse](https://doc.qt.io/qt-6/qml-qtquick-textinput.html#selectByMouse-prop) of the internal [TextField](https://doc.qt.io/qt-6/qml-qtquick-controls-textfield.html).

Defaults to true. If true, the user can use the mouse to select text in the usual way.

*See also* [TextInput.selectByMouse](https://doc.qt.io/qt-6/qml-qtquick-textinput.html#selectByMouse-prop)

### selectedText : string {#selectedText-prop}

This property holds the [selectedText](https://doc.qt.io/qt-6/qml-qtquick-textinput.html#selectedText-prop) of the internal [TextField](https://doc.qt.io/qt-6/qml-qtquick-controls-textfield.html).

This property holds the selected text in the text field.

*See also* [TextInput.selectedText](https://doc.qt.io/qt-6/qml-qtquick-textinput.html#selectedText-prop)

### selectionEnd : int {#selectionEnd-prop}

This property holds the [selectionEnd](https://doc.qt.io/qt-6/qml-qtquick-textinput.html#selectionEnd-prop) of the internal [TextField](https://doc.qt.io/qt-6/qml-qtquick-controls-textfield.html).

This property holds the cursor position after the last character in the current selection. This property is read-only.

*See also* [TextInput.selectionEnd](https://doc.qt.io/qt-6/qml-qtquick-textinput.html#selectionEnd-prop)

### selectionStart : int {#selectionStart-prop}

This property holds the [selectionStart](https://doc.qt.io/qt-6/qml-qtquick-textinput.html#selectionStart-prop) of the internal [TextField](https://doc.qt.io/qt-6/qml-qtquick-controls-textfield.html).

This property holds the cursor position before the first character in the current selection. This property is read-only.

*See also* [TextInput.selectionStart](https://doc.qt.io/qt-6/qml-qtquick-textinput.html#selectionStart-prop)

### status : var {#status-prop}

This property holds the current status message type of the text field.

This consists of an inline message with a colorful background and an appropriate icon.

The status property will affect the color of [statusMessage](qml-org-kde-kirigamiaddons-formcard-formtextfielddelegate.md#statusMessage-prop) used.

Accepted values:

| Constant | Description |
| --- | --- |
| Kirigami.MessageType.Information | (blue color) |
| Kirigami.MessageType.Positive | (green color) |
| Kirigami.MessageType.Warning | (orange color) |
| Kirigami.MessageType.Error | (red color) |

Default: Kirigami.[MessageType](../kirigami/messagetype.md).Information if [statusMessage](qml-org-kde-kirigamiaddons-formcard-formtextfielddelegate.md#statusMessage-prop) is set, nothing otherwise.

*See also* Kirigami.MessageType

### \[default: ""\] statusMessage : string {#statusMessage-prop}

This property holds the current status message of the text field.

If this property is not set, no status will be shown.

### trailing : alias {#trailing-prop}

This property holds child items to be displayed on the right of the text field.

### validator : Validator {#validator-prop}

This property holds the [validator](https://doc.qt.io/qt-6/qml-qtquick-textinput.html#validator-prop) of the internal [TextField](https://doc.qt.io/qt-6/qml-qtquick-controls-textfield.html).

## Signal Documentation {#signal-documentation}

### accepted() {#accepted-signal}

This signal is emitted when the Return or Enter key is pressed.

Note that if there is a [validator](qml-org-kde-kirigamiaddons-formcard-formtextfielddelegate.md#validator-prop) or [inputMask](https://doc.qt.io/qt-6/qml-qtquick-textinput.html#inputMask-prop) set on the text input, the signal will only be emitted if the input is in an acceptable state.

> **Note:** The corresponding handler is `onAccepted`.

### editingFinished() {#editingFinished-signal}

This signal is emitted when the Return or Enter key is pressed or the text input loses focus.

Note that if there is a [validator](qml-org-kde-kirigamiaddons-formcard-formtextfielddelegate.md#validator-prop) or [inputMask](https://doc.qt.io/qt-6/qml-qtquick-textinput.html#inputMask-prop) set on the text input and enter/return is pressed, this signal will only be emitted if the input follows the inputMask and the validator returns an acceptable state.

> **Note:** The corresponding handler is `onEditingFinished`.

### textEdited() {#textEdited-signal}

This signal is emitted whenever the text is edited.

Unlike textChanged(), this signal is not emitted when the text is changed programmatically, for example, by changing the value of the text property or by calling [clear](qml-org-kde-kirigamiaddons-formcard-formtextfielddelegate.md#clear-method)().

> **Note:** The corresponding handler is `onTextEdited`.

## Method Documentation {#method-documentation}

### clear() {#clear-method}

Clears the contents of the text input and resets partial text input from an input method.

### insert(*position*, *text*) {#insert-method}

Inserts `text` into the [TextInput](https://doc.qt.io/qt-6/qml-qtquick-textinput.html) at `position`.

### select(*start*, *end*) {#select-method}

Causes the text from `start` to `end` to be selected.

### selectAll() {#selectAll-method}

Causes all text to be selected.
