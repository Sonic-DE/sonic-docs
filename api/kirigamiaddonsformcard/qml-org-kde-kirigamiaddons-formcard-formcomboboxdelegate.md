---
title: "FormComboBoxDelegate QML Type"
description: "A Form delegate that corresponds to a ComboBox."
---

# FormComboBoxDelegate QML Type

A Form delegate that corresponds to a [ComboBox](https://doc.qt.io/qt-6/qml-qtquick-controls-combobox.html). [More...](#details)

- Import Statement: import org.kde.kirigamiaddons.formcard
- Inherits: [AbstractFormDelegate](qml-org-kde-kirigamiaddons-formcard-abstractformdelegate.md)

## Detailed Description {#details}

This component is used for individual settings that can have multiple possible values shown in a vertical list, typically defined in a model.

Many of its properties require familiarity with [ComboBox](https://doc.qt.io/qt-6/qml-qtquick-controls-combobox.html).

Use the inherited [AbstractButton.text](https://doc.qt.io/qt-6/qml-qtquick-controls-abstractbutton.html#text-prop) property to define the main text of the combobox.

If you need a purely on/off toggle, use a [FormSwitchDelegate](qml-org-kde-kirigamiaddons-formcard-formswitchdelegate.md) instead.

If you need an on/off/tristate toggle, use a [FormCheckDelegate](qml-org-kde-kirigamiaddons-formcard-formcheckdelegate.md) instead.

If you need multiple toggles instead of multiple values for the same setting, consider using a [FormRadioDelegate](qml-org-kde-kirigamiaddons-formcard-formradiodelegate.md).

*See also* [AbstractButton](https://doc.qt.io/qt-6/qml-qtquick-controls-abstractbutton.html), [FormSwitchDelegate](qml-org-kde-kirigamiaddons-formcard-formswitchdelegate.md), [FormCheckDelegate](qml-org-kde-kirigamiaddons-formcard-formcheckdelegate.md), [FormRadioDelegate](qml-org-kde-kirigamiaddons-formcard-formradiodelegate.md)

## Property Documentation {#property-documentation}

### comboBoxDelegate : Component {#comboBoxDelegate-prop}

The delegate component to use as entries in the [ComboBox](https://doc.qt.io/qt-6/qml-qtquick-controls-combobox.html) display mode.

### count : int {#count-prop}

This property holds the [count](https://doc.qt.io/qt-6/qml-qtquick-controls-combobox.html#count-prop) of the internal [ComboBox](https://doc.qt.io/qt-6/qml-qtquick-controls-combobox.html).

### currentIndex : int {#currentIndex-prop}

This property holds the [currentIndex](https://doc.qt.io/qt-6/qml-qtquick-controls-combobox.html#currentIndex-prop) of the internal [ComboBox](https://doc.qt.io/qt-6/qml-qtquick-controls-combobox.html).

Default: `-1` when the model has no data, `0` otherwise

### currentText : string {#currentText-prop}

This property holds the [currentText](https://doc.qt.io/qt-6/qml-qtquick-controls-combobox.html#currentText-prop) of the internal [ComboBox](https://doc.qt.io/qt-6/qml-qtquick-controls-combobox.html).

*See also* [displayText](qml-org-kde-kirigamiaddons-formcard-formcomboboxdelegate.md#displayText-prop)

### currentValue : var {#currentValue-prop}

This property holds the [currentValue](https://doc.qt.io/qt-6/qml-qtquick-controls-combobox.html#currentValue-prop) of the internal [ComboBox](https://doc.qt.io/qt-6/qml-qtquick-controls-combobox.html).

### \[default: ""\] description : string {#description-prop}

A label that contains secondary text that appears under the inherited text property.

This provides additional information shown in a faint gray color.

This is supposed to be a short text and the API user should avoid making it longer than two lines.

### dialog : Component {#dialog-prop}

The dialog component used for the [ComboBox](https://doc.qt.io/qt-6/qml-qtquick-controls-combobox.html).

This property allows one to override the internal dialog with a custom component.

### dialogDelegate : Component {#dialogDelegate-prop}

The delegate component to use as entries for each value in the dialog and page display mode.

### \[default: FormComboBoxDelegate.ComboBox\] displayMode : int {#displayMode-prop}

This property holds what display mode the delegate should show as.

Set this property to the desired DisplayMode.

On mobile, displayMode defaults to `FormComboBoxDelegate.Dialog`.

| Constant | Description |
| --- | --- |
| FormComboBoxDelegate.ComboBox | A standard [ComboBox](https://doc.qt.io/qt-6/qml-qtquick-controls-combobox.html) component containing a vertical list of values. |
| FormComboBoxDelegate.Dialog | A button with similar appearance to a [ComboBox](https://doc.qt.io/qt-6/qml-qtquick-controls-combobox.html) that, when clicked, shows a [Kirigami.OverlaySheet](../kirigami/qml-org-kde-kirigami-overlaysheet.md) at the middle of the window containing a vertical list of values. |
| FormComboBoxDelegate.Page | A button with similar appearance to a [ComboBox](https://doc.qt.io/qt-6/qml-qtquick-controls-combobox.html) that, when clicked, shows a [Kirigami.ScrollablePage](../kirigami/qml-org-kde-kirigami-scrollablepage.md) in a new window containing a vertical list of values. |

### displayText : string {#displayText-prop}

This property holds the [displayText](https://doc.qt.io/qt-6/qml-qtquick-controls-combobox.html#displayText-prop) of the internal [ComboBox](https://doc.qt.io/qt-6/qml-qtquick-controls-combobox.html).

This can be used to slightly modify the text to be displayed in the combobox, for instance, by adding a string with the [currentText](qml-org-kde-kirigamiaddons-formcard-formcomboboxdelegate.md#currentText-prop).

### editText : string {#editText-prop}

This property holds the [editText](https://doc.qt.io/qt-6/qml-qtquick-controls-combobox.html#editText-prop) property of the internal [ComboBox](https://doc.qt.io/qt-6/qml-qtquick-controls-combobox.html).

### editable : bool {#editable-prop}

This property holds the [editable](https://doc.qt.io/qt-6/qml-qtquick-controls-combobox.html#editable-prop) property of the internal [ComboBox](https://doc.qt.io/qt-6/qml-qtquick-controls-combobox.html).

This turns the combobox editable, allowing the user to specify existing values or add new ones.

Use this only when [displayMode](qml-org-kde-kirigamiaddons-formcard-formcomboboxdelegate.md#displayMode-prop) is set to [FormComboBoxDelegate](qml-org-kde-kirigamiaddons-formcard-formcomboboxdelegate.md).[ComboBox](https://doc.qt.io/qt-6/qml-qtquick-controls-combobox.html).

### highlightedIndex : int {#highlightedIndex-prop}

This property holds the [highlightedIndex](https://doc.qt.io/qt-6/qml-qtquick-controls-combobox.html#highlightedIndex-prop) of the internal [ComboBox](https://doc.qt.io/qt-6/qml-qtquick-controls-combobox.html).

### model : var {#model-prop}

This property holds the [model](https://doc.qt.io/qt-6/qml-qtquick-controls-combobox.html#model-prop) providing data for the [ComboBox](https://doc.qt.io/qt-6/qml-qtquick-controls-combobox.html).

*See also* [displayText](qml-org-kde-kirigamiaddons-formcard-formcomboboxdelegate.md#displayText-prop), [Models and Views in QtQuick](https://doc.qt.io/qt-6/qtquick-modelviewsdata-modelview.html)

### page : Component {#page-prop}

The page component used for the [ComboBox](https://doc.qt.io/qt-6/qml-qtquick-controls-combobox.html), if applicable.

This property allows one to override the internal [Kirigami.ScrollablePage](../kirigami/qml-org-kde-kirigami-scrollablepage.md) with a custom component.

### status : var {#status-prop}

This property holds the current status message type of the text field.

This consists of an inline message with a colorful background and an appropriate icon.

The status property will affect the color of [statusMessage](qml-org-kde-kirigamiaddons-formcard-formcomboboxdelegate.md#statusMessage-prop) used.

Accepted values:

| Constant | Description |
| --- | --- |
| Kirigami.MessageType.Information | (blue color) |
| Kirigami.MessageType.Positive | (green color) |
| Kirigami.MessageType.Warning | (orange color) |
| Kirigami.MessageType.Error | (red color) |

Default: Kirigami.[MessageType](../kirigami/messagetype.md).Information if [statusMessage](qml-org-kde-kirigamiaddons-formcard-formcomboboxdelegate.md#statusMessage-prop) is set, nothing otherwise.

*See also* Kirigami.MessageType

### statusMessage : string {#statusMessage-prop}

This property holds the current status message of the text field.

If this property is not set, no status will be shown.

### textRole : string {#textRole-prop}

This property holds the [textRole](https://doc.qt.io/qt-6/qml-qtquick-controls-combobox.html#textRole-prop) of the internal [ComboBox](https://doc.qt.io/qt-6/qml-qtquick-controls-combobox.html).

### \[default: null\] trailing : Item {#trailing-prop}

This property holds an item that will be displayed after the delegate's contents.

### valueRole : string {#valueRole-prop}

This property holds the [valueRole](https://doc.qt.io/qt-6/qml-qtquick-controls-combobox.html#valueRole-prop) of the internal [ComboBox](https://doc.qt.io/qt-6/qml-qtquick-controls-combobox.html).

## Signal Documentation {#signal-documentation}

### accepted() {#accepted-signal}

This signal is emitted when the Return or Enter key is pressed while an editable combo box is focused.

> **Note:** The corresponding handler is `onAccepted`.

*See also* [editable](qml-org-kde-kirigamiaddons-formcard-formcomboboxdelegate.md#editable-prop)

### activated(int *index*) {#activated-signal}

This signal is emitted when the item at `index` is activated by the user.

> **Note:** The corresponding handler is `onActivated`.

## Method Documentation {#method-documentation}

### closeDialog() {#closeDialog-method}

Closes the dialog or layer.

This function can be used when reimplementing the page or dialog.
