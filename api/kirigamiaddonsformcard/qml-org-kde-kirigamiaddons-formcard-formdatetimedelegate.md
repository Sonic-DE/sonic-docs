---
title: "FormDateTimeDelegate QML Type"
description: "FormDateTimeDelegate is a delegate for FormCard that lets the user enter either a date, a time or both."
---

# FormDateTimeDelegate QML Type

[FormDateTimeDelegate](qml-org-kde-kirigamiaddons-formcard-formdatetimedelegate.md) is a delegate for [FormCard](qml-org-kde-kirigamiaddons-formcard-formcard.md) that lets the user enter either a date, a time or both. [More...](#details)

- Import Statement: import org.kde.kirigamiaddons.formcard
- Inherits: [AbstractFormDelegate](qml-org-kde-kirigamiaddons-formcard-abstractformdelegate.md)

## Detailed Description {#details}

This component allows to define a [minimumDate](qml-org-kde-kirigamiaddons-formcard-formdatetimedelegate.md#minimumDate-prop) and [maximumDate](qml-org-kde-kirigamiaddons-formcard-formdatetimedelegate.md#maximumDate-prop) to restrict the date that the user is allowed to enter.

You should not add a label but instead use the above [FormHeader](qml-org-kde-kirigamiaddons-formcard-formheader.md) to specify what the form delegate refers to.

```qml
import org.kde.kirigamiaddons.formcard as FormCard

FormCard.FormCardPage {
    FormCard.FormHeader {
        title: "Departure"
    }

    FormCard.FormCard {
        FormCard.FormDateTimeDelegate {}

        FormCard.FormDelegateSeparator {}

        FormCard.FormTextFieldDelegate {
            label: "Location"
        }
    }
}
```

> **Note:** This component can also be used in a read only mode to display a date.

> **Warning:** This will use the native date and time picker from the platform if available. For example this happens on Android.

## Property Documentation {#property-documentation}

### dateTimeDisplay : int {#dateTimeDisplay-prop}

This property holds which part of the date and time selector are show to the user.

By default both the time and the date are shown.

Accepted values:

| Constant | Description |
| --- | --- |
| FormDateTimeDelegate.DateTimeDisplay.DateTime | Show the date and time. |
| FormDateTimeDelegate.DateTimeDisplay.Date | Show only the date. |
| FormDateTimeDelegate.DateTimeDisplay.Time | Show only the time. |

### \[default: ""\] description : string {#description-prop}

A label containing secondary text that appears under the inherited text property.

This provides additional information shown in a faint gray color.

### initialValue : date {#initialValue-prop}

This property holds the the date to use as initial default when editing an an unset date.

By default, this is the current date/time.

### maximumDate : date {#maximumDate-prop}

This property holds the maximum date (inclusive) that the user can select.

By default, no limit is applied to the date selection.

### minimumDate : date {#minimumDate-prop}

This property holds the minimum date (inclusive) that the user can select.

By default, no limit is applied to the date selection.

### \[default: ApplicationWindow.window\] popupParent : var {#popupParent-prop}

This property holds the parent used for the popups of this control.

### \[default: false\] readOnly : bool {#readOnly-prop}

This property holds whether this delegate is readOnly or whether the user can select a new time and date.

### \[default: false\] resettable : bool {#resettable-prop}

This property holds whether the user can reset the date and time to an unset value.

When enabled, a "Reset" button is added to the date and time pickers. Clicking it sets [value](qml-org-kde-kirigamiaddons-formcard-formdatetimedelegate.md#value-prop) to an invalid date, which is displayed as "Not set".

### status : var {#status-prop}

This property holds the current status message type of the text field.

This consists of an inline message with a colorful background and an appropriate icon.

The status property will affect the color of [statusMessage](qml-org-kde-kirigamiaddons-formcard-formdatetimedelegate.md#statusMessage-prop) used.

Accepted values:

| Constant | Description |
| --- | --- |
| Kirigami.MessageType.Information | (blue color) |
| Kirigami.MessageType.Positive | (green color) |
| Kirigami.MessageType.Warning | (orange color) |
| Kirigami.MessageType.Error | (red color) |

Default: Kirigami.[MessageType](../kirigami/messagetype.md).Information if [statusMessage](qml-org-kde-kirigamiaddons-formcard-formdatetimedelegate.md#statusMessage-prop) is set, nothing otherwise.

*See also* Kirigami.MessageType

### statusMessage : string {#statusMessage-prop}

This property holds the current status message of the text field.

If this property is not set, no [status](qml-org-kde-kirigamiaddons-formcard-formdatetimedelegate.md#status-prop) will be shown.

### value : date {#value-prop}

The current date and time selected by the user.
