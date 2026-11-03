---
title: "KDateComboBox Class"
description: "A combobox for dates."
---

# KDateComboBox Class

A combobox for dates. [More...](#details)

- **Header:** `#include <KDateComboBox>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS WidgetsAddons)`  
  `target_link_libraries(mytarget PRIVATE KF6::WidgetsAddons)`
- **Inherits:** [QComboBox](https://doc.qt.io/qt-6/qcombobox.html)

[List of all members, including inherited members](kdatecombobox-members.md)

## Public Types

- [enum KDateComboBox::Option](#Option-enum)

## Properties

- [date : QDate](#date-prop)
- [maximumDate : QDate](#maximumDate-prop)
- [minimumDate : QDate](#minimumDate-prop)
- [options : Options](#options-prop)

## Public Functions

- [KDateComboBox(QWidget \*parent = nullptr)](#KDateComboBox)
- [QDate date() const](#date)
- [QMap\<QDate, QString\> dateMap() const](#dateMap)
- [QLocale::FormatType displayFormat() const](#displayFormat)
- [bool isNull() const](#isNull)
- [bool isValid() const](#isValid)
- [QDate maximumDate() const](#maximumDate)
- [QDate minimumDate() const](#minimumDate)
- [KDateComboBox::Options options() const](#options)

## Public Slots

- [void resetDateRange()](#resetDateRange)
- [void resetMaximumDate()](#resetMaximumDate)
- [void resetMinimumDate()](#resetMinimumDate)
- [void setDate(const QDate &date)](#setDate)
- [void setDateMap(QMap\<QDate, QString\> dateMap)](#setDateMap)
- [void setDateRange(const QDate &minDate, const QDate &maxDate, const QString &minWarnMsg = QString(), const QString &maxWarnMsg = QString())](#setDateRange)
- [void setDisplayFormat(QLocale::FormatType format)](#setDisplayFormat)
- [void setMaximumDate(const QDate &maxDate, const QString &maxWarnMsg = QString())](#setMaximumDate)
- [void setMinimumDate(const QDate &minDate, const QString &minWarnMsg = QString())](#setMinimumDate)
- [void setOptions(KDateComboBox::Options options)](#setOptions)

## Signals

- [void dateChanged(const QDate &date)](#dateChanged)
- [void dateEdited(const QDate &date)](#dateEdited)
- [void dateEntered(const QDate &date)](#dateEntered)

## Protected Functions

- [void assignDate(const QDate &date)](#assignDate)

## Detailed Description {#details}

## Member Type Documentation {#member-type-documentation}

### enum KDateComboBox::Option {#Option-enum}

**flags KDateComboBox::Options**

Options provided by the widget

| Constant | Value | Description |
| --- | --- | --- |
| `KDateComboBox::EditDate` | `0x0001` | Allow the user to manually edit the date in the combo line edit |
| `KDateComboBox::SelectDate` | `0x0002` | Allow the user to select the date from a drop-down menu |
| `KDateComboBox::DatePicker` | `0x0004` | Show a date picker in the drop-down |
| `KDateComboBox::DateKeywords` | `0x0008` | Show date keywords in the drop-down |
| `KDateComboBox::WarnOnInvalid` | `0x0010` | Show a warning on focus out if the date is invalid |

The `Options` type is a typedef for `QFlags<Option>. `It stores an OR combination of `Option` values.

*See also* [options](kdatecombobox.md#options)(), [setOptions](kdatecombobox.md#setOptions)()

## Property Documentation {#property-documentation}

### date : QDate {#date-prop}

**Access functions:**

- `QDate` **[date](kdatecombobox.md#date)**() const
- `void` **[setDate](kdatecombobox.md#setDate)**(const `QDate` &*date*)

**Notifier signal:**

- `void` **[dateChanged](kdatecombobox.md#dateChanged)**(const `QDate` &*date*)

### maximumDate : QDate {#maximumDate-prop}

**Access functions:**

- `QDate` **[maximumDate](kdatecombobox.md#maximumDate)**() const
- `void` **[setMaximumDate](kdatecombobox.md#setMaximumDate)**(const `QDate` &*maxDate*, const `QString` &*maxWarnMsg* = QString())
- `void` **[resetMaximumDate](kdatecombobox.md#resetMaximumDate)**()

### minimumDate : QDate {#minimumDate-prop}

**Access functions:**

- `QDate` **[minimumDate](kdatecombobox.md#minimumDate)**() const
- `void` **[setMinimumDate](kdatecombobox.md#setMinimumDate)**(const `QDate` &*minDate*, const `QString` &*minWarnMsg* = QString())
- `void` **[resetMinimumDate](kdatecombobox.md#resetMinimumDate)**()

### options : Options {#options-prop}

**Access functions:**

- `KDateComboBox::Options` **[options](kdatecombobox.md#options)**() const
- `void` **[setOptions](kdatecombobox.md#setOptions)**(`KDateComboBox::Options` *options*)

## Member Function Documentation {#member-function-documentation}

### \[explicit\] KDateComboBox::KDateComboBox(QWidget \**parent* = nullptr) {#KDateComboBox}

Create a new [KDateComboBox](kdatecombobox.md) widget

By default the [EditDate](kdatecombobox.md#Option-enum), [SelectDate](kdatecombobox.md#Option-enum), [DatePicker](kdatecombobox.md#Option-enum) and [DateKeywords](kdatecombobox.md#Option-enum) options are enabled, the ShortDate format is used and the date is set to the current date.

### \[virtual protected\] void KDateComboBox::assignDate(const QDate &*date*) {#assignDate}

Assign the date for the widget.

Virtual to allow sub-classes to apply extra validation rules.

`date` the new date

### QDate KDateComboBox::date() const {#date}

Return the currently selected date

> **Note:** Getter function for property [date](kdatecombobox.md#date-prop).

*See also* [setDate](kdatecombobox.md#setDate)()

### \[signal\] void KDateComboBox::dateChanged(const QDate &*date*) {#dateChanged}

Signal if the date has been changed either manually by the user or programmatically.

The emitted date may be invalid.

`date` the new date

> **Note:** Notifier signal for property [date](kdatecombobox.md#date-prop).

### \[signal\] void KDateComboBox::dateEdited(const QDate &*date*) {#dateEdited}

Signal if the date is being manually edited by the user.

The emitted date may be invalid, or may not yet be what the user intends as the final date.

`date` the new date

### \[signal\] void KDateComboBox::dateEntered(const QDate &*date*) {#dateEntered}

Signal if the date has been manually entered (by typing a date and losing focus, or pressing Enter) or selected by the user (using the popup selector, or up, down, page up, page down keys, or the mouse wheel).

The emitted date may be invalid.

`date` the new date

### QMap\<QDate, QString\> KDateComboBox::dateMap() const {#dateMap}

Return the map of dates listed in the drop-down and their displayed string forms.

*See also* [setDateMap](kdatecombobox.md#setDateMap)()

### QLocale::FormatType KDateComboBox::displayFormat() const {#displayFormat}

Return the currently set date display format

By default this is the Short Format

*See also* [setDisplayFormat](kdatecombobox.md#setDisplayFormat)()

### bool KDateComboBox::isNull() const {#isNull}

Return if the current user input is null

*See also* [isValid](kdatecombobox.md#isValid)()

### bool KDateComboBox::isValid() const {#isValid}

Return if the current user input is valid

If the user input is null then it is not valid

*See also* [isNull](kdatecombobox.md#isNull)()

### QDate KDateComboBox::maximumDate() const {#maximumDate}

Return the current maximum date

> **Note:** Getter function for property [maximumDate](kdatecombobox.md#maximumDate-prop).

*See also* [setMaximumDate](kdatecombobox.md#setMaximumDate)()

### QDate KDateComboBox::minimumDate() const {#minimumDate}

Return the current minimum date

> **Note:** Getter function for property [minimumDate](kdatecombobox.md#minimumDate-prop).

*See also* [setMinimumDate](kdatecombobox.md#setMinimumDate)()

### KDateComboBox::Options KDateComboBox::options() const {#options}

Return the currently set widget options

> **Note:** Getter function for property [options](kdatecombobox.md#options-prop).

*See also* [setOptions](kdatecombobox.md#setOptions)()

### \[slot\] void KDateComboBox::resetDateRange() {#resetDateRange}

Reset the minimum and maximum date to the default values.

*See also* [setDateRange](kdatecombobox.md#setDateRange)()

### \[slot\] void KDateComboBox::resetMaximumDate() {#resetMaximumDate}

Reset the maximum date to the default

The default is to have no maximum date.

> **Note:** Resetter function for property [maximumDate](kdatecombobox.md#maximumDate-prop).

### \[slot\] void KDateComboBox::resetMinimumDate() {#resetMinimumDate}

Reset the minimum date to the default.

The default is to have no minimum date.

> **Note:** Resetter function for property [minimumDate](kdatecombobox.md#minimumDate-prop).

### \[slot\] void KDateComboBox::setDate(const QDate &*date*) {#setDate}

Set the currently selected date

You can set an invalid date or a date outside the valid range, validity checking is only done via [isValid](kdatecombobox.md#isValid)().

`date` the new date

> **Note:** Setter function for property [date](kdatecombobox.md#date-prop).

*See also* [date](kdatecombobox.md#date)()

### \[slot\] void KDateComboBox::setDateMap(QMap\<QDate, QString\> *dateMap*) {#setDateMap}

Set the list of dates able to be selected from the drop-down and the string form to display for those dates, e.g. "2010-01-01" and "Yesterday".

Any invalid or duplicate dates will be used, the list will NOT be sorted, and the minimum and maximum date will not be affected.

The `dateMap` is keyed by the date to be listed and the value is the string to be displayed. If you want the date to be displayed in the default date format then the string should be null. If you want a separator to be displayed then set the string to "separator".

`dateMap` the map of dates able to be selected

*See also* [dateMap](kdatecombobox.md#dateMap)()

### \[slot\] void KDateComboBox::setDateRange(const QDate &*minDate*, const QDate &*maxDate*, const QString &*minWarnMsg* = QString(), const QString &*maxWarnMsg* = QString()) {#setDateRange}

Set the valid date range to be applied by [isValid](kdatecombobox.md#isValid)().

Both dates must be valid and the minimum date must be less than or equal to the maximum date, otherwise the date range will not be set.

`minDate` the minimum date

`maxDate` the maximum date

`minWarnMsg` the minimum warning message

`maxWarnMsg` the maximum warning message

### \[slot\] void KDateComboBox::setDisplayFormat(QLocale::FormatType *format*) {#setDisplayFormat}

Sets the date format to display.

By default is the Short Format.

`format` the date format to use

*See also* [displayFormat](kdatecombobox.md#displayFormat)()

### \[slot\] void KDateComboBox::setMaximumDate(const QDate &*maxDate*, const QString &*maxWarnMsg* = QString()) {#setMaximumDate}

Set the maximum allowed date.

If the date is invalid, or less than current minimum, then the maximum will not be set.

`maxDate` the maximum date

`maxWarnMsg` the maximum warning message

> **Note:** Setter function for property [maximumDate](kdatecombobox.md#maximumDate-prop).

*See also* [minimumDate](kdatecombobox.md#minimumDate)(), [maximumDate](kdatecombobox.md#maximumDate)(), setMaximumDate(), [setDateRange](kdatecombobox.md#setDateRange)()

### \[slot\] void KDateComboBox::setMinimumDate(const QDate &*minDate*, const QString &*minWarnMsg* = QString()) {#setMinimumDate}

Set the minimum allowed date.

If the date is invalid, or greater than current maximum, then the minimum will not be set.

`minDate` the minimum date

`minWarnMsg` the minimum warning message

> **Note:** Setter function for property [minimumDate](kdatecombobox.md#minimumDate-prop).

*See also* [minimumDate](kdatecombobox.md#minimumDate)(), [maximumDate](kdatecombobox.md#maximumDate)(), [setMaximumDate](kdatecombobox.md#setMaximumDate)(), [setDateRange](kdatecombobox.md#setDateRange)()

### \[slot\] void KDateComboBox::setOptions(KDateComboBox::Options *options*) {#setOptions}

Set the new widget options

`options` the new widget options

> **Note:** Setter function for property [options](kdatecombobox.md#options-prop).

*See also* [options](kdatecombobox.md#options)()
