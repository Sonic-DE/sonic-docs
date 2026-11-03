---
title: "KDatePicker Class"
description: "A date selection widget."
---

# KDatePicker Class

A date selection widget. [More...](#details)

- **Header:** `#include <KDatePicker>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS WidgetsAddons)`  
  `target_link_libraries(mytarget PRIVATE KF6::WidgetsAddons)`
- **Inherits:** [QFrame](https://doc.qt.io/qt-6/qframe.html)

[List of all members, including inherited members](kdatepicker-members.md)

## Properties

- [closeButton : bool](#closeButton-prop)
- [date : QDate](#date-prop)
- [fontSize : int](#fontSize-prop)

## Public Functions

- [KDatePicker(QWidget \*parent = nullptr)](#KDatePicker)
- [KDatePicker(const QDate &dt, QWidget \*parent = nullptr)](#KDatePicker-1)
- [const QDate &date() const](#date)
- [int fontSize() const](#fontSize)
- [bool hasCloseButton() const](#hasCloseButton)
- [void setCloseButton(bool enable)](#setCloseButton)
- [bool setDate(const QDate &date)](#setDate)
- [void setDateRange(const QDate &minDate, const QDate &maxDate = QDate())](#setDateRange) (since 6.12)
- [void setFontSize(int)](#setFontSize)
- [QSize sizeHint() const](#sizeHint)

## Signals

- [void dateChanged(const QDate &date)](#dateChanged)
- [void dateEntered(const QDate &date)](#dateEntered)
- [void dateSelected(const QDate &date)](#dateSelected)
- [void tableClicked()](#tableClicked)

## Detailed Description {#details}

Provides a widget for calendar date input.

Different from the previous versions, it now emits two types of signals, either [dateSelected](kdatepicker.md#dateSelected)() or [dateEntered](kdatepicker.md#dateEntered)() (see documentation for both signals).

A line edit has been added in the newer versions to allow the user to select a date directly by entering numbers like 19990101 or 990101.

## Property Documentation {#property-documentation}

### closeButton : bool {#closeButton-prop}

**Access functions:**

- `bool` **[hasCloseButton](kdatepicker.md#hasCloseButton)**() const
- `void` **[setCloseButton](kdatepicker.md#setCloseButton)**(`bool` *enable*)

### date : QDate {#date-prop}

**Access functions:**

- const `QDate` &**[date](kdatepicker.md#date)**() const
- `bool` **[setDate](kdatepicker.md#setDate)**(const `QDate` &*date*)

**Notifier signal:**

- `void` **[dateChanged](kdatepicker.md#dateChanged)**(const `QDate` &*date*)

### fontSize : int {#fontSize-prop}

**Access functions:**

- `int` **[fontSize](kdatepicker.md#fontSize)**() const
- `void` **[setFontSize](kdatepicker.md#setFontSize)**(*int*)

## Member Function Documentation {#member-function-documentation}

### \[explicit\] KDatePicker::KDatePicker(QWidget \**parent* = nullptr) {#KDatePicker}

The constructor. The current date will be displayed initially.

### \[explicit\] KDatePicker::KDatePicker(const QDate &*dt*, QWidget \**parent* = nullptr) {#KDatePicker-1}

The constructor. The given date will be displayed initially.

### const QDate &KDatePicker::date() const {#date}

Returns the selected date.

> **Note:** Getter function for property [date](kdatepicker.md#date-prop).

*See also* [setDate](kdatepicker.md#setDate)()

### \[signal\] void KDatePicker::dateChanged(const QDate &*date*) {#dateChanged}

This signal is emitted each time the selected date is changed. Usually, this does not mean that the date has been entered, since the date also changes, for example, when another month is selected.

> **Note:** Notifier signal for property [date](kdatepicker.md#date-prop).

*See also* [dateSelected](kdatepicker.md#dateSelected)

### \[signal\] void KDatePicker::dateEntered(const QDate &*date*) {#dateEntered}

This signal is emitted when enter is pressed and a VALID date has been entered before into the line edit. Connect to both dateEntered() and [dateSelected](kdatepicker.md#dateSelected)() to receive all events where the user really enters a date.

### \[signal\] void KDatePicker::dateSelected(const QDate &*date*) {#dateSelected}

This signal is emitted each time a day has been selected by clicking on the table (hitting a day in the current month). It has the same meaning as dateSelected() in older versions of [KDatePicker](kdatepicker.md).

### int KDatePicker::fontSize() const {#fontSize}

Returns the font size of the widget elements.

> **Note:** Getter function for property [fontSize](kdatepicker.md#fontSize-prop).

*See also* [setFontSize](kdatepicker.md#setFontSize)()

### bool KDatePicker::hasCloseButton() const {#hasCloseButton}

Returns true if a [KDatePicker](kdatepicker.md) shows a close-button.

> **Note:** Getter function for property [closeButton](kdatepicker.md#closeButton-prop).

*See also* [setCloseButton](kdatepicker.md#setCloseButton)

### void KDatePicker::setCloseButton(bool *enable*) {#setCloseButton}

By calling this method with `enable` = true, [KDatePicker](kdatepicker.md) will show a little close-button in the upper button-row. Clicking the close-button will cause the [KDatePicker](kdatepicker.md)'s topLevelWidget()'s [close](https://doc.qt.io/qt-6/qwidget.html#close)() method being called. This is mostly useful for toplevel datepickers without a window manager decoration.

> **Note:** Setter function for property [closeButton](kdatepicker.md#closeButton-prop).

*See also* [hasCloseButton](kdatepicker.md#hasCloseButton)

### bool KDatePicker::setDate(const QDate &*date*) {#setDate}

Sets the date.

Returns `false` and does not change anything if the date given is invalid.

> **Note:** Setter function for property [date](kdatepicker.md#date-prop).

*See also* [date](kdatepicker.md#date)()

### \[since 6.12\] void KDatePicker::setDateRange(const QDate &*minDate*, const QDate &*maxDate* = QDate()) {#setDateRange}

Sets the range of dates that can be accepted.

Invalid dates can be used to define open-ended ranges. If both values are valid, the minimum date must be less than or equal to the maximum date, otherwise the date range will not be set.

`minDate` the minimum date

`maxDate` the maximum date

This function was introduced in Qt 6.12.

### void KDatePicker::setFontSize(*int*) {#setFontSize}

Sets the font size of the widgets elements.

> **Note:** Setter function for property [fontSize](kdatepicker.md#fontSize-prop).

*See also* [fontSize](kdatepicker.md#fontSize)()

### \[override virtual\] QSize KDatePicker::sizeHint() const {#sizeHint}

Reimplements: [QFrame::sizeHint() const](https://doc.qt.io/qt-6/qframe.html#sizeHint).

The size hint for date pickers. The size hint recommends the minimum size of the widget so that all elements may be placed without clipping. This sometimes looks ugly, so when using the size hint, try adding 28 to each of the reported numbers of pixels.

### \[signal\] void KDatePicker::tableClicked() {#tableClicked}

This signal is emitted when the day has been selected by clicking on it in the table.
