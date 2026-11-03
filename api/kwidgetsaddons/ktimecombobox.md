---
title: "KTimeComboBox Class"
description: "A combobox for times."
---

# KTimeComboBox Class

A combobox for times. [More...](#details)

- **Header:** `#include <KTimeComboBox>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS WidgetsAddons)`  
  `target_link_libraries(mytarget PRIVATE KF6::WidgetsAddons)`
- **Inherits:** [QComboBox](https://doc.qt.io/qt-6/qcombobox.html)

[List of all members, including inherited members](ktimecombobox-members.md)

## Public Types

- [enum KTimeComboBox::Option](#Option-enum)

## Properties

- [maximumTime : QTime](#maximumTime-prop)
- [minimumTime : QTime](#minimumTime-prop)
- [options : Options](#options-prop)
- [time : QTime](#time-prop)
- [timeListInterval : int](#timeListInterval-prop)

## Public Functions

- [KTimeComboBox(QWidget \*parent = nullptr)](#KTimeComboBox)
- [QLocale::FormatType displayFormat() const](#displayFormat)
- [bool isNull() const](#isNull)
- [bool isValid() const](#isValid)
- [QTime maximumTime() const](#maximumTime)
- [QTime minimumTime() const](#minimumTime)
- [KTimeComboBox::Options options() const](#options)
- [void resetMaximumTime()](#resetMaximumTime)
- [void resetMinimumTime()](#resetMinimumTime)
- [void resetTimeRange()](#resetTimeRange)
- [void setTimeRange(const QTime &minTime, const QTime &maxTime, const QString &minWarnMsg = QString(), const QString &maxWarnMsg = QString())](#setTimeRange)
- [QTime time() const](#time)
- [QList\<QTime\> timeList() const](#timeList)
- [int timeListInterval() const](#timeListInterval)

## Public Slots

- [void setDisplayFormat(QLocale::FormatType format)](#setDisplayFormat)
- [void setMaximumTime(const QTime &maxTime, const QString &maxWarnMsg = QString())](#setMaximumTime)
- [void setMinimumTime(const QTime &minTime, const QString &minWarnMsg = QString())](#setMinimumTime)
- [void setOptions(KTimeComboBox::Options options)](#setOptions)
- [void setTime(const QTime &time)](#setTime)
- [void setTimeList(QList\<QTime\> timeList, const QString &minWarnMsg = QString(), const QString &maxWarnMsg = QString())](#setTimeList)
- [void setTimeListInterval(int minutes)](#setTimeListInterval)

## Signals

- [void timeChanged(const QTime &time)](#timeChanged)
- [void timeEdited(const QTime &time)](#timeEdited)
- [void timeEntered(const QTime &time)](#timeEntered)

## Protected Functions

- [void assignTime(const QTime &time)](#assignTime)

## Detailed Description {#details}

## Member Type Documentation {#member-type-documentation}

### enum KTimeComboBox::Option {#Option-enum}

**flags KTimeComboBox::Options**

Options provided by the widget

| Constant | Value | Description |
| --- | --- | --- |
| `KTimeComboBox::EditTime` | `0x0001` | Allow the user to manually edit the time in the combo line edit |
| `KTimeComboBox::SelectTime` | `0x0002` | Allow the user to select the time from a drop-down menu |
| `KTimeComboBox::ForceTime` | `0x0004` | Any set or entered time will be forced to one of the drop-down times |
| `KTimeComboBox::WarnOnInvalid` | `0x0008` | Show a warning box on focus out if the user enters an invalid time |

The `Options` type is a typedef for `QFlags<Option>. `It stores an OR combination of `Option` values.

*See also* [options](ktimecombobox.md#options), [setOptions](ktimecombobox.md#setOptions)

## Property Documentation {#property-documentation}

### maximumTime : QTime {#maximumTime-prop}

**Access functions:**

- `QTime` **[maximumTime](ktimecombobox.md#maximumTime)**() const
- `void` **[setMaximumTime](ktimecombobox.md#setMaximumTime)**(const `QTime` &*maxTime*, const `QString` &*maxWarnMsg* = QString())
- `void` **[resetMaximumTime](ktimecombobox.md#resetMaximumTime)**()

### minimumTime : QTime {#minimumTime-prop}

**Access functions:**

- `QTime` **[minimumTime](ktimecombobox.md#minimumTime)**() const
- `void` **[setMinimumTime](ktimecombobox.md#setMinimumTime)**(const `QTime` &*minTime*, const `QString` &*minWarnMsg* = QString())
- `void` **[resetMinimumTime](ktimecombobox.md#resetMinimumTime)**()

### options : Options {#options-prop}

**Access functions:**

- `KTimeComboBox::Options` **[options](ktimecombobox.md#options)**() const
- `void` **[setOptions](ktimecombobox.md#setOptions)**(`KTimeComboBox::Options` *options*)

### time : QTime {#time-prop}

**Access functions:**

- `QTime` **[time](ktimecombobox.md#time)**() const
- `void` **[setTime](ktimecombobox.md#setTime)**(const `QTime` &*time*)

**Notifier signal:**

- `void` **[timeChanged](ktimecombobox.md#timeChanged)**(const `QTime` &*time*)

### timeListInterval : int {#timeListInterval-prop}

**Access functions:**

- `int` **[timeListInterval](ktimecombobox.md#timeListInterval)**() const
- `void` **[setTimeListInterval](ktimecombobox.md#setTimeListInterval)**(`int` *minutes*)

## Member Function Documentation {#member-function-documentation}

### \[explicit\] KTimeComboBox::KTimeComboBox(QWidget \**parent* = nullptr) {#KTimeComboBox}

Create a new [KTimeComboBox](ktimecombobox.md) widget

### \[virtual protected\] void KTimeComboBox::assignTime(const QTime &*time*) {#assignTime}

Assign the time for the widget.

Virtual to allow sub-classes to apply extra validation rules.

`time` the new time

### QLocale::FormatType KTimeComboBox::displayFormat() const {#displayFormat}

Return the currently set time format

By default this is the Short Format

*See also* [setDisplayFormat](ktimecombobox.md#setDisplayFormat)()

### bool KTimeComboBox::isNull() const {#isNull}

Return if the current user input is null

*See also* [isValid](ktimecombobox.md#isValid)()

### bool KTimeComboBox::isValid() const {#isValid}

Return if the current user input is valid

If the user input is null then it is not valid

*See also* [isNull](ktimecombobox.md#isNull)()

### QTime KTimeComboBox::maximumTime() const {#maximumTime}

Return the current maximum time

> **Note:** Getter function for property [maximumTime](ktimecombobox.md#maximumTime-prop).

*See also* [setMaximumTime](ktimecombobox.md#setMaximumTime)()

### QTime KTimeComboBox::minimumTime() const {#minimumTime}

Return the current minimum time

> **Note:** Getter function for property [minimumTime](ktimecombobox.md#minimumTime-prop).

*See also* [setMinimumTime](ktimecombobox.md#setMinimumTime)()

### KTimeComboBox::Options KTimeComboBox::options() const {#options}

Return the currently set widget options

> **Note:** Getter function for property [options](ktimecombobox.md#options-prop).

*See also* [setOptions](ktimecombobox.md#setOptions)()

### void KTimeComboBox::resetMaximumTime() {#resetMaximumTime}

Reset the maximum time to the default of 23:59:59.999

> **Note:** Resetter function for property [maximumTime](ktimecombobox.md#maximumTime-prop).

### void KTimeComboBox::resetMinimumTime() {#resetMinimumTime}

Reset the minimum time to the default of 00:00:00.000

> **Note:** Resetter function for property [minimumTime](ktimecombobox.md#minimumTime-prop).

### void KTimeComboBox::resetTimeRange() {#resetTimeRange}

Reset the minimum and maximum time to the default values.

### \[slot\] void KTimeComboBox::setDisplayFormat(QLocale::FormatType *format*) {#setDisplayFormat}

Sets the time format to display.

By default is the Short Format.

`format` the time format to use

*See also* [displayFormat](ktimecombobox.md#displayFormat)()

### \[slot\] void KTimeComboBox::setMaximumTime(const QTime &*maxTime*, const QString &*maxWarnMsg* = QString()) {#setMaximumTime}

Set the maximum allowed time.

If the time is invalid, or less than current minimum, then the maximum will not be set.

`maxTime` the maximum time

`maxWarnMsg` the maximum warning message

> **Note:** Setter function for property [maximumTime](ktimecombobox.md#maximumTime-prop).

*See also* [minimumTime](ktimecombobox.md#minimumTime)(), [maximumTime](ktimecombobox.md#maximumTime)(), setMaximumTime(), [setTimeRange](ktimecombobox.md#setTimeRange)()

### \[slot\] void KTimeComboBox::setMinimumTime(const QTime &*minTime*, const QString &*minWarnMsg* = QString()) {#setMinimumTime}

Set the minimum allowed time.

If the time is invalid, or greater than current maximum, then the minimum will not be set.

`minTime` the minimum time

`minWarnMsg` the minimum warning message

> **Note:** Setter function for property [minimumTime](ktimecombobox.md#minimumTime-prop).

*See also* [minimumTime](ktimecombobox.md#minimumTime)(), [maximumTime](ktimecombobox.md#maximumTime)(), [setMaximumTime](ktimecombobox.md#setMaximumTime)(), [setTimeRange](ktimecombobox.md#setTimeRange)()

### \[slot\] void KTimeComboBox::setOptions(KTimeComboBox::Options *options*) {#setOptions}

Set the new widget options

`options` the new widget options

> **Note:** Setter function for property [options](ktimecombobox.md#options-prop).

*See also* [options](ktimecombobox.md#options)()

### \[slot\] void KTimeComboBox::setTime(const QTime &*time*) {#setTime}

Set the currently selected time

You can set an invalid time or a time outside the valid range, validity checking is only done via [isValid](ktimecombobox.md#isValid)().

`time` the new time

> **Note:** Setter function for property [time](ktimecombobox.md#time-prop).

*See also* [time](ktimecombobox.md#time)()

### \[slot\] void KTimeComboBox::setTimeList(QList\<QTime\> *timeList*, const QString &*minWarnMsg* = QString(), const QString &*maxWarnMsg* = QString()) {#setTimeList}

Set the list of times able to be selected from the drop-down.

Setting the time list will override any time interval previously set via [setTimeListInterval](ktimecombobox.md#setTimeListInterval)().

Any invalid or duplicate times will be ignored, and the list will be sorted.

The minimum and maximum time will automatically be set to the earliest and latest value in the list.

`timeList` the list of times able to be selected

`minWarnMsg` the minimum warning message

`maxWarnMsg` the maximum warning message

*See also* [timeList](ktimecombobox.md#timeList)()

### \[slot\] void KTimeComboBox::setTimeListInterval(int *minutes*) {#setTimeListInterval}

Set the interval between times able to be selected from the drop-down.

The combo drop-down will be populated with times every `minutes` apart, starting from the [minimumTime](ktimecombobox.md#minimumTime)() and ending at [maximumTime](ktimecombobox.md#maximumTime)().

If the ForceInterval option is set then any time manually typed into the combo line edit will be forced to the nearest interval.

This interval must be an exact divisor of the valid time range hours. For example with the default 24 hour range `interval` must divide 1440 minutes exactly, meaning 1, 6 and 90 are valid but 7, 31 and 91 are not.

Setting the time list interval will override any time list previously set via [setTimeList](ktimecombobox.md#setTimeList)().

`minutes` the time list interval to display

> **Note:** Setter function for property [timeListInterval](ktimecombobox.md#timeListInterval-prop).

*See also* [timeListInterval](ktimecombobox.md#timeListInterval)()

### void KTimeComboBox::setTimeRange(const QTime &*minTime*, const QTime &*maxTime*, const QString &*minWarnMsg* = QString(), const QString &*maxWarnMsg* = QString()) {#setTimeRange}

Set the minimum and maximum time range.

If either time is invalid, or min \> max then the range will not be set.

`minTime` the minimum time

`maxTime` the maximum time

`minWarnMsg` the minimum warning message

`maxWarnMsg` the maximum warning message

### QTime KTimeComboBox::time() const {#time}

Return the currently selected time

> **Note:** Getter function for property [time](ktimecombobox.md#time-prop).

*See also* [setTime](ktimecombobox.md#setTime)()

### \[signal\] void KTimeComboBox::timeChanged(const QTime &*time*) {#timeChanged}

Signal if the time has been changed either manually by the user or programmatically.

The returned time may be invalid.

`time` the new time

> **Note:** Notifier signal for property [time](ktimecombobox.md#time-prop).

### \[signal\] void KTimeComboBox::timeEdited(const QTime &*time*) {#timeEdited}

Signal if the time is being manually edited by the user.

The returned time may be invalid.

`time` the new time

### \[signal\] void KTimeComboBox::timeEntered(const QTime &*time*) {#timeEntered}

Signal if the time has been manually entered or selected by the user.

The returned time may be invalid.

`time` the new time

### QList\<QTime\> KTimeComboBox::timeList() const {#timeList}

Return the list of times able to be selected in the drop-down.

*See also* [setTimeList](ktimecombobox.md#setTimeList)(), [timeListInterval](ktimecombobox.md#timeListInterval)(), [setTimeListInterval](ktimecombobox.md#setTimeListInterval)()

### int KTimeComboBox::timeListInterval() const {#timeListInterval}

Return the interval in minutes between select time list entries if set by [setTimeListInterval](ktimecombobox.md#setTimeListInterval)().

Returns -1 if not set.

> **Note:** Getter function for property [timeListInterval](ktimecombobox.md#timeListInterval-prop).

*See also* [setTimeListInterval](ktimecombobox.md#setTimeListInterval)()
