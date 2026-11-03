---
title: "DatePopup QML Type"
description: "QML types for selecting dates and times.."
---

# DatePopup QML Type

QML types for selecting dates and times.. [More...](#details)

- Inherits: [Dialog](https://doc.qt.io/qt-6/qml-qtquick-controls-dialog.html)

## Detailed Description {#details}

A popup that prompts the user to select a date.

## Property Documentation {#property-documentation}

### autoAccept : bool {#autoAccept-prop}

This property holds whether the date popup will automatically select a date on selection or has a "Select" button.

By default, this is false.

### maximumDate : date {#maximumDate-prop}

This property holds the maximum date (inclusive) that the user can select.

By default, no limit is applied to the date selection.

### minimumDate : date {#minimumDate-prop}

This property holds the minimum date (inclusive) that the user can select.

By default, no limit is applied to the date selection.

### \[default: false\] resettable : bool {#resettable-prop}

This property holds whether a "Reset" button is shown, allowing the user to unset the value.

> **Note:** The button is not shown when [autoAccept](qml-datepopup.md#autoAccept-prop) is enabled.

When the user clicks it, [value](qml-datepopup.md#value-prop) is set to an invalid date, the [reset](https://doc.qt.io/qt-6/qml-qtquick-controls-dialog.html#reset-signal) signal is emitted and the popup is closed.

### value : date {#value-prop}

The current date and time selected by the user.
