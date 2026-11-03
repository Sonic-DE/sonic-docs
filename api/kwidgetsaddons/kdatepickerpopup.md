---
title: "KDatePickerPopup Class"
description: "This menu helps the user to select a date quickly."
---

# KDatePickerPopup Class

This menu helps the user to select a date quickly. [More...](#details)

- **Header:** `#include <KDatePickerPopup>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS WidgetsAddons)`  
  `target_link_libraries(mytarget PRIVATE KF6::WidgetsAddons)`
- **Inherits:** [QMenu](https://doc.qt.io/qt-6/qmenu.html)

[List of all members, including inherited members](kdatepickerpopup-members.md)

## Public Types

- [enum KDatePickerPopup::Mode](#Mode-enum)

## Properties

- [modes : Modes](#modes-prop)

## Public Functions

- [KDatePickerPopup(KDatePickerPopup::Modes modes = DatePicker, QDate date = currentDate(), QWidget \*parent = nullptr)](#KDatePickerPopup)
- [QMap\<QDate, QString\> dateMap() const](#dateMap)
- [KDatePicker \*datePicker() const](#datePicker)
- [KDatePickerPopup::Modes modes() const](#modes)
- [void setDateMap(const QMap\<QDate, QString\> &dateMap)](#setDateMap)
- [void setDateRange(const QDate &minDate, const QDate &maxDate)](#setDateRange)
- [void setModes(KDatePickerPopup::Modes modes)](#setModes)

## Public Slots

- [void setDate(QDate date)](#setDate)

## Signals

- [void dateChanged(const QDate &date)](#dateChanged)

## Detailed Description {#details}

This menu helps the user to select a date quickly. It offers various modes of selecting, e.g. with a [KDatePicker](kdatepicker.md) or with words like "Tomorrow".

The available modes are:

- [NoDate](kdatepickerpopup.md#Mode-enum): A menu-item with "No Date". If chosen, the datepicker will emit a null [QDate](https://doc.qt.io/qt-6/qdate.html).
- [DatePicker](kdatepickerpopup.md#Mode-enum): Shows a [KDatePicker](kdatepicker.md)-widget.
- Words: Shows items like "Today", "Tomorrow" or "Next Week".

## Member Type Documentation {#member-type-documentation}

### enum KDatePickerPopup::Mode {#Mode-enum}

**flags KDatePickerPopup::Modes**

Describes the available selection modes.

| Constant | Value | Description |
| --- | --- | --- |
| `KDatePickerPopup::NoDate` | `1` | A menu-item with "No Date". Will always return an invalid date. |
| `KDatePickerPopup::DatePicker` | `2` | A menu-item with a [KDatePicker](kdatepicker.md). |
| `KDatePickerPopup::Words` | `4` | A menu-item with list of words that describe a date. |

The `Modes` type is a typedef for `QFlags<Mode>. `It stores an OR combination of `Mode` values.

## Property Documentation {#property-documentation}

### modes : Modes {#modes-prop}

**Access functions:**

- `KDatePickerPopup::Modes` **[modes](kdatepickerpopup.md#modes)**() const
- `void` **[setModes](kdatepickerpopup.md#setModes)**(`KDatePickerPopup::Modes` *modes*)

## Member Function Documentation {#member-function-documentation}

### \[explicit\] KDatePickerPopup::KDatePickerPopup(KDatePickerPopup::Modes *modes* = DatePicker, QDate *date* = QDate::currentDate(), QWidget \**parent* = nullptr) {#KDatePickerPopup}

Creates a new date picker popup.

`modes` The selection modes that shall be offered

`date` The initial date of date picker widget.

`parent` The parent object.

### \[signal\] void KDatePickerPopup::dateChanged(const QDate &*date*) {#dateChanged}

This signal is emitted whenever the user has selected a new date.

`date` The new date.

### QMap\<QDate, QString\> KDatePickerPopup::dateMap() const {#dateMap}

Return the map of dates listed in the drop-down and their displayed string forms.

*See also* [setDateMap](kdatepickerpopup.md#setDateMap)()

### KDatePicker \*KDatePickerPopup::datePicker() const {#datePicker}

Returns the used [KDatePicker](kdatepicker.md) object.

### KDatePickerPopup::Modes KDatePickerPopup::modes() const {#modes}

Returns the currently used selection modes.

> **Note:** Getter function for property [modes](kdatepickerpopup.md#modes-prop).

*See also* [setModes](kdatepickerpopup.md#setModes)()

### \[slot\] void KDatePickerPopup::setDate(QDate *date*) {#setDate}

Sets the current `date`.

### void KDatePickerPopup::setDateMap(const QMap\<QDate, QString\> &*dateMap*) {#setDateMap}

Sets the list of dates in the drop-down menu that the user can select from and the text string to display for each date, e.g. "2010-01-01" and "Yesterday".

The list of date/string pairs is used as-is (invalid or duplicate dates aren't removed), and the order will not be changed (the map is sorted by key); also and the minimum and maximum dates will not be affected.

The `dateMap` is keyed by the date to be listed and the value is the string to be displayed. If you want the date to be displayed in the default date format then the string should be null. If you want a separator to be displayed then set the string to "separator".

`dateMap` the map of dates the user can select from

*See also* [dateMap](kdatepickerpopup.md#dateMap)()

### void KDatePickerPopup::setDateRange(const QDate &*minDate*, const QDate &*maxDate*) {#setDateRange}

Sets the range of dates that can be accepted.

Invalid dates can be used to define open-ended ranges. If both values are valid, the minimum date must be less than or equal to the maximum date, otherwise the date range will not be set.

`minDate` the minimum date

`maxDate` the maximum date

### void KDatePickerPopup::setModes(KDatePickerPopup::Modes *modes*) {#setModes}

Set the selection modes to use.

> **Note:** Setter function for property [modes](kdatepickerpopup.md#modes-prop).

*See also* [modes](kdatepickerpopup.md#modes)()
