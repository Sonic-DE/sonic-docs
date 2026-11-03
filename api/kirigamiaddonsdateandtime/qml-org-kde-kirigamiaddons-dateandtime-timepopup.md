---
title: "TimePopup QML Type"
description: "A dialog for selecting a time."
---

# TimePopup QML Type

A dialog for selecting a time. [More...](#details)

- Import Statement: import org.kde.kirigamiaddons.dateandtime
- Inherits: [Dialog](https://doc.qt.io/qt-6/qml-qtquick-controls-dialog.html)

## Detailed Description {#details}

Set [value](qml-org-kde-kirigamiaddons-dateandtime-timepopup.md#value-prop) to the initial date and time. When the user clicks Select, the dialog updates [value](qml-org-kde-kirigamiaddons-dateandtime-timepopup.md#value-prop) and emits [accepted](https://doc.qt.io/qt-6/qml-qtquick-controls-dialog.html#accepted-signal).

## Property Documentation {#property-documentation}

### \[default: false\] resettable : bool {#resettable-prop}

This property holds whether a "Reset" button is shown, allowing the user to unset the value.

When the user clicks it, [value](qml-org-kde-kirigamiaddons-dateandtime-timepopup.md#value-prop) is set to an invalid date, the [reset](https://doc.qt.io/qt-6/qml-qtquick-controls-dialog.html#reset-signal) signal is emitted and the popup is closed.

### value : date {#value-prop}

The date and time selected by the user. The time is updated when the user clicks Select.

## Signal Documentation {#signal-documentation}

### cancelled() {#cancelled-signal}

Emitted when the user clicks Cancel.

> **Note:** The corresponding handler is `onCancelled`.
