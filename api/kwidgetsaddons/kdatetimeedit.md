---
title: "KDateTimeEdit Class"
description: "A widget for editing date and time."
---

# KDateTimeEdit Class

A widget for editing date and time. [More...](#details)

- **Header:** `#include <KDateTimeEdit>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS WidgetsAddons)`  
  `target_link_libraries(mytarget PRIVATE KF6::WidgetsAddons)`
- **Inherits:** [QWidget](https://doc.qt.io/qt-6/qwidget.html)

[List of all members, including inherited members](kdatetimeedit-members.md)

## Public Types

- [enum KDateTimeEdit::Option](#Option-enum)

## Properties

- [date : QDate](#date-prop)
- [options : Options](#options-prop)
- [time : QTime](#time-prop)
- [timeListInterval : int](#timeListInterval-prop)

## Public Functions

- [KDateTimeEdit(QWidget \*parent = nullptr)](#KDateTimeEdit)
- [QList\<QLocale\> calendarLocalesList() const](#calendarLocalesList)
- [QDate date() const](#date)
- [QLocale::FormatType dateDisplayFormat() const](#dateDisplayFormat)
- [QMap\<QDate, QString\> dateMap() const](#dateMap)
- [QDateTime dateTime() const](#dateTime)
- [bool isNull() const](#isNull)
- [bool isNullDate() const](#isNullDate)
- [bool isNullTime() const](#isNullTime)
- [bool isValid() const](#isValid)
- [bool isValidDate() const](#isValidDate)
- [bool isValidTime() const](#isValidTime)
- [QDateTime maximumDateTime() const](#maximumDateTime)
- [QDateTime minimumDateTime() const](#minimumDateTime)
- [KDateTimeEdit::Options options() const](#options)
- [QTime time() const](#time)
- [QLocale::FormatType timeDisplayFormat() const](#timeDisplayFormat)
- [QList\<QTime\> timeList() const](#timeList)
- [int timeListInterval() const](#timeListInterval)
- [QTimeZone timeZone() const](#timeZone)
- [QList\<QTimeZone\> timeZones() const](#timeZones)

## Public Slots

- [void resetDateTimeRange()](#resetDateTimeRange)
- [void resetMaximumDateTime()](#resetMaximumDateTime)
- [void resetMinimumDateTime()](#resetMinimumDateTime)
- [void setCalendarLocalesList(const QList\<QLocale\> &calendarLocales)](#setCalendarLocalesList)
- [void setDate(const QDate &date)](#setDate)
- [void setDateDisplayFormat(QLocale::FormatType format)](#setDateDisplayFormat)
- [void setDateMap(QMap\<QDate, QString\> dateMap)](#setDateMap)
- [void setDateTime(const QDateTime &dateTime)](#setDateTime)
- [void setDateTimeRange(const QDateTime &minDateTime, const QDateTime &maxDateTime, const QString &minWarnMsg = QString(), const QString &maxWarnMsg = QString())](#setDateTimeRange)
- [void setMaximumDateTime(const QDateTime &maxDateTime, const QString &maxWarnMsg = QString())](#setMaximumDateTime)
- [void setMinimumDateTime(const QDateTime &minDateTime, const QString &minWarnMsg = QString())](#setMinimumDateTime)
- [void setOptions(KDateTimeEdit::Options options)](#setOptions)
- [void setTime(const QTime &time)](#setTime)
- [void setTimeDisplayFormat(QLocale::FormatType format)](#setTimeDisplayFormat)
- [void setTimeList(QList\<QTime\> timeList, const QString &minWarnMsg = QString(), const QString &maxWarnMsg = QString())](#setTimeList)
- [void setTimeListInterval(int minutes)](#setTimeListInterval)
- [void setTimeZone(const QTimeZone &zone)](#setTimeZone)
- [void setTimeZones(const QList\<QTimeZone\> &zones)](#setTimeZones)

## Signals

- [void calendarChanged(const QLocale &calendarLocale)](#calendarChanged)
- [void calendarEntered(const QLocale &calendarLocale)](#calendarEntered)
- [void dateChanged(const QDate &date)](#dateChanged)
- [void dateEdited(const QDate &date)](#dateEdited)
- [void dateEntered(const QDate &date)](#dateEntered)
- [void dateTimeChanged(const QDateTime &dateTime)](#dateTimeChanged)
- [void dateTimeEdited(const QDateTime &dateTime)](#dateTimeEdited)
- [void dateTimeEntered(const QDateTime &dateTime)](#dateTimeEntered)
- [void timeChanged(const QTime &time)](#timeChanged)
- [void timeEdited(const QTime &time)](#timeEdited)
- [void timeEntered(const QTime &time)](#timeEntered)
- [void timeZoneChanged(const QTimeZone &zone)](#timeZoneChanged)
- [void timeZoneEntered(const QTimeZone &zone)](#timeZoneEntered)

## Protected Functions

- [void assignDate(const QDate &date)](#assignDate)
- [void assignDateTime(const QDateTime &dateTime)](#assignDateTime)
- [void assignTime(const QTime &time)](#assignTime)
- [void assignTimeZone(const QTimeZone &zone)](#assignTimeZone)

## Detailed Description {#details}

## Member Type Documentation {#member-type-documentation}

### enum KDateTimeEdit::Option {#Option-enum}

**flags KDateTimeEdit::Options**

Options provided by the widget

| Constant | Value | Description |
| --- | --- | --- |
| `KDateTimeEdit::ShowCalendar` | `0x00001` | If the Calendar System edit is displayed |
| `KDateTimeEdit::ShowDate` | `0x00002` | If the Date is displayed |
| `KDateTimeEdit::ShowTime` | `0x00004` | If the Time is displayed |
| `KDateTimeEdit::ShowTimeZone` | `0x00008` | If the Time Zone is displayed |
| `KDateTimeEdit::EditDate` | `0x00020` | Allow the user to manually edit the date |
| `KDateTimeEdit::EditTime` | `0x00040` | Allow the user to manually edit the time |
| `KDateTimeEdit::SelectCalendar` | `0x00100` | Allow the user to select a calendar |
| `KDateTimeEdit::SelectDate` | `0x00200` | Allow the user to select a date |
| `KDateTimeEdit::SelectTime` | `0x00400` | Allow the user to select a time |
| `KDateTimeEdit::SelectTimeZone` | `0x00800` | Allow the user to select a time zone |
| `KDateTimeEdit::DatePicker` | `0x01000` | Show a date picker |
| `KDateTimeEdit::DateKeywords` | `0x02000` | Show date keywords |
| `KDateTimeEdit::ForceTime` | `0x04000` | The entered time can only be a selected time |
| `KDateTimeEdit::WarnOnInvalid` | `0x08000` | Show a warning on focus out if the date or time is invalid |

The `Options` type is a typedef for `QFlags<Option>. `It stores an OR combination of `Option` values.

*See also* [options](kdatetimeedit.md#options), [setOptions](kdatetimeedit.md#setOptions), Options

## Property Documentation {#property-documentation}

### date : QDate {#date-prop}

**Access functions:**

- `QDate` **[date](kdatetimeedit.md#date)**() const
- `void` **[setDate](kdatetimeedit.md#setDate)**(const `QDate` &*date*)

**Notifier signal:**

- `void` **[dateChanged](kdatetimeedit.md#dateChanged)**(const `QDate` &*date*)

### options : Options {#options-prop}

**Access functions:**

- `KDateTimeEdit::Options` **[options](kdatetimeedit.md#options)**() const
- `void` **[setOptions](kdatetimeedit.md#setOptions)**(`KDateTimeEdit::Options` *options*)

### time : QTime {#time-prop}

**Access functions:**

- `QTime` **[time](kdatetimeedit.md#time)**() const
- `void` **[setTime](kdatetimeedit.md#setTime)**(const `QTime` &*time*)

**Notifier signal:**

- `void` **[timeChanged](kdatetimeedit.md#timeChanged)**(const `QTime` &*time*)

### timeListInterval : int {#timeListInterval-prop}

**Access functions:**

- `int` **[timeListInterval](kdatetimeedit.md#timeListInterval)**() const
- `void` **[setTimeListInterval](kdatetimeedit.md#setTimeListInterval)**(`int` *minutes*)

## Member Function Documentation {#member-function-documentation}

### \[explicit\] KDateTimeEdit::KDateTimeEdit(QWidget \**parent* = nullptr) {#KDateTimeEdit}

Create a new [KDateTimeEdit](kdatetimeedit.md) widget

### \[virtual protected\] void KDateTimeEdit::assignDate(const QDate &*date*) {#assignDate}

Assign the date for the widget.

Virtual to allow sub-classes to apply extra validation rules, but reimplementations must call the parent method at the end.

`date` the new date

### \[virtual protected\] void KDateTimeEdit::assignDateTime(const QDateTime &*dateTime*) {#assignDateTime}

Assign the date, time and time zone for the widget.

Virtual to allow sub-classes to apply extra validation rules, but reimplementations must call the parent method at the end.

`dateTime` the new date and time

### \[virtual protected\] void KDateTimeEdit::assignTime(const QTime &*time*) {#assignTime}

Assign the time for the widget.

Virtual to allow sub-classes to apply extra validation rules, but reimplementations must call the parent method at the end.

`time` the new time

### \[protected\] void KDateTimeEdit::assignTimeZone(const QTimeZone &*zone*) {#assignTimeZone}

Assign the time zone for the widget.

Virtual to allow sub-classes to apply extra validation rules, but reimplementations must call the parent method at the end.

`zone` the new time zone

### \[signal\] void KDateTimeEdit::calendarChanged(const QLocale &*calendarLocale*) {#calendarChanged}

Signal if the Calendar Locale has been changed either manually by the user or programmatically.

`calendarLocale` the new calendar locale

### \[signal\] void KDateTimeEdit::calendarEntered(const QLocale &*calendarLocale*) {#calendarEntered}

Signal if the Calendar Locale has been manually entered by the user.

`calendarLocale` the new calendar locale

### QList\<QLocale\> KDateTimeEdit::calendarLocalesList() const {#calendarLocalesList}

Returns the list of Calendar Locales displayed.

*See also* [setCalendarLocalesList](kdatetimeedit.md#setCalendarLocalesList)()

### QDate KDateTimeEdit::date() const {#date}

Return the currently selected date

> **Note:** Getter function for property [date](kdatetimeedit.md#date-prop).

*See also* [setDate](kdatetimeedit.md#setDate)()

### \[signal\] void KDateTimeEdit::dateChanged(const QDate &*date*) {#dateChanged}

Signal if the date has been changed either manually by the user or programmatically.

The returned date may be invalid.

`date` the new date

> **Note:** Notifier signal for property [date](kdatetimeedit.md#date-prop).

### QLocale::FormatType KDateTimeEdit::dateDisplayFormat() const {#dateDisplayFormat}

Return the currently set date display format

By default this is the Short Format

*See also* [setDateDisplayFormat](kdatetimeedit.md#setDateDisplayFormat)()

### \[signal\] void KDateTimeEdit::dateEdited(const QDate &*date*) {#dateEdited}

Signal if the date is being manually edited by the user.

The returned date may be invalid.

`date` the new date

### \[signal\] void KDateTimeEdit::dateEntered(const QDate &*date*) {#dateEntered}

Signal if the date has been manually entered by the user.

The returned date may be invalid.

`date` the new date

### QMap\<QDate, QString\> KDateTimeEdit::dateMap() const {#dateMap}

Return the map of dates listed in the drop-down and their displayed string forms.

*See also* [setDateMap](kdatetimeedit.md#setDateMap)()

### QDateTime KDateTimeEdit::dateTime() const {#dateTime}

Return the currently selected date, time and time zone

*See also* [setDateTime](kdatetimeedit.md#setDateTime)()

### \[signal\] void KDateTimeEdit::dateTimeChanged(const QDateTime &*dateTime*) {#dateTimeChanged}

Signal if the date or time has been changed either manually by the user or programmatically.

The returned date and time may be invalid.

`dateTime` the new date, time and time zone

### \[signal\] void KDateTimeEdit::dateTimeEdited(const QDateTime &*dateTime*) {#dateTimeEdited}

Signal if the date or time is being manually edited by the user.

The returned date and time may be invalid.

`dateTime` the new date, time and time zone

### \[signal\] void KDateTimeEdit::dateTimeEntered(const QDateTime &*dateTime*) {#dateTimeEntered}

Signal if the date or time has been manually entered by the user.

The returned date and time may be invalid.

`dateTime` the new date, time and time zone

### bool KDateTimeEdit::isNull() const {#isNull}

Return if the current user input is null

*See also* [isValid](kdatetimeedit.md#isValid)()

### bool KDateTimeEdit::isNullDate() const {#isNullDate}

Return if the current user input date is null

*See also* [isValidDate](kdatetimeedit.md#isValidDate)()

### bool KDateTimeEdit::isNullTime() const {#isNullTime}

Return if the current user input time is null

*See also* [isValidTime](kdatetimeedit.md#isValidTime)()

### bool KDateTimeEdit::isValid() const {#isValid}

Return if the current user input is valid

If the user input is null then it is not valid

*See also* [isNull](kdatetimeedit.md#isNull)()

### bool KDateTimeEdit::isValidDate() const {#isValidDate}

Return if the current user input date is valid

If the user input date is null then it is not valid

*See also* [isNullDate](kdatetimeedit.md#isNullDate)()

### bool KDateTimeEdit::isValidTime() const {#isValidTime}

Return if the current user input time is valid

If the user input time is null then it is not valid

*See also* [isNullTime](kdatetimeedit.md#isNullTime)()

### QDateTime KDateTimeEdit::maximumDateTime() const {#maximumDateTime}

Return the current maximum date and time

*See also* [setMaximumDateTime](kdatetimeedit.md#setMaximumDateTime)()

### QDateTime KDateTimeEdit::minimumDateTime() const {#minimumDateTime}

Return the current minimum date and time

*See also* [setMinimumDateTime](kdatetimeedit.md#setMinimumDateTime)()

### KDateTimeEdit::Options KDateTimeEdit::options() const {#options}

Return the currently set widget options

> **Note:** Getter function for property [options](kdatetimeedit.md#options-prop).

*See also* [setOptions](kdatetimeedit.md#setOptions)()

### \[slot\] void KDateTimeEdit::resetDateTimeRange() {#resetDateTimeRange}

Reset the minimum and maximum date and time to the default

### \[slot\] void KDateTimeEdit::resetMaximumDateTime() {#resetMaximumDateTime}

Reset the minimum date and time to the default

### \[slot\] void KDateTimeEdit::resetMinimumDateTime() {#resetMinimumDateTime}

Reset the minimum date and time to the default

### \[slot\] void KDateTimeEdit::setCalendarLocalesList(const QList\<QLocale\> &*calendarLocales*) {#setCalendarLocalesList}

Set the list of Calendar Locales to display.

`calendarLocales` the list of calendar locales to display

*See also* [calendarLocalesList](kdatetimeedit.md#calendarLocalesList)()

### \[slot\] void KDateTimeEdit::setDate(const QDate &*date*) {#setDate}

Set the currently selected date

`date` the new date

> **Note:** Setter function for property [date](kdatetimeedit.md#date-prop).

*See also* [date](kdatetimeedit.md#date)()

### \[slot\] void KDateTimeEdit::setDateDisplayFormat(QLocale::FormatType *format*) {#setDateDisplayFormat}

Sets the date format to display.

By default is the Short Format.

`format` the date format to use

*See also* [dateDisplayFormat](kdatetimeedit.md#dateDisplayFormat)()

### \[slot\] void KDateTimeEdit::setDateMap(QMap\<QDate, QString\> *dateMap*) {#setDateMap}

Set the list of dates able to be selected from the drop-down and the string form to display for those dates, e.g. "2010-01-01" and "Yesterday".

Any invalid or duplicate dates will be used, the list will NOT be sorted, and the minimum and maximum date will not be affected.

The `dateMap` is keyed by the date to be listed and the value is the string to be displayed. If you want the date to be displayed in the default date format then the string should be null. If you want a separator to be displayed then set the string to "separator".

`dateMap` the map of dates able to be selected

*See also* [dateMap](kdatetimeedit.md#dateMap)()

### \[slot\] void KDateTimeEdit::setDateTime(const QDateTime &*dateTime*) {#setDateTime}

Set the currently selected date, time and time zone

`dateTime` the new date, time and time zone

*See also* [dateTime](kdatetimeedit.md#dateTime)()

### \[slot\] void KDateTimeEdit::setDateTimeRange(const QDateTime &*minDateTime*, const QDateTime &*maxDateTime*, const QString &*minWarnMsg* = QString(), const QString &*maxWarnMsg* = QString()) {#setDateTimeRange}

Set the minimum and maximum date and time range

To enable range checking provide two valid dates. To disable range checking provide two invalid dates, or call clearDateRange;

`minDateTime` the minimum date and time

`maxDateTime` the maximum date and time

`minWarnMsg` the minimum warning message

`maxWarnMsg` the maximum warning message

### \[slot\] void KDateTimeEdit::setMaximumDateTime(const QDateTime &*maxDateTime*, const QString &*maxWarnMsg* = QString()) {#setMaximumDateTime}

Set the maximum allowed date.

If the date is invalid, or less than current minimum, then the maximum will not be set.

`maxDateTime` the maximum date

`maxWarnMsg` the maximum warning message

*See also* [maximumDateTime](kdatetimeedit.md#maximumDateTime)(), [setMinimumDateTime](kdatetimeedit.md#setMinimumDateTime)(), setDateRange()

### \[slot\] void KDateTimeEdit::setMinimumDateTime(const QDateTime &*minDateTime*, const QString &*minWarnMsg* = QString()) {#setMinimumDateTime}

Set the minimum allowed date.

If the date is invalid, or more than current maximum, then the minimum will not be set.

`minDateTime` the minimum date

`minWarnMsg` the minimum warning message

*See also* [minimumDateTime](kdatetimeedit.md#minimumDateTime)(), [setMaximumDateTime](kdatetimeedit.md#setMaximumDateTime)(), setDateRange()

### \[slot\] void KDateTimeEdit::setOptions(KDateTimeEdit::Options *options*) {#setOptions}

Set the new widget options

`options` the new widget options

> **Note:** Setter function for property [options](kdatetimeedit.md#options-prop).

*See also* [options](kdatetimeedit.md#options)()

### \[slot\] void KDateTimeEdit::setTime(const QTime &*time*) {#setTime}

Set the currently selected time

`time` the new time

> **Note:** Setter function for property [time](kdatetimeedit.md#time-prop).

*See also* [time](kdatetimeedit.md#time)()

### \[slot\] void KDateTimeEdit::setTimeDisplayFormat(QLocale::FormatType *format*) {#setTimeDisplayFormat}

Sets the time format to display.

By default is the Short Format.

`format` the time format to use

*See also* [timeDisplayFormat](kdatetimeedit.md#timeDisplayFormat)()

### \[slot\] void KDateTimeEdit::setTimeList(QList\<QTime\> *timeList*, const QString &*minWarnMsg* = QString(), const QString &*maxWarnMsg* = QString()) {#setTimeList}

Set the list of times able to be selected from the drop-down.

Setting the time list will override any time interval previously set via [setTimeListInterval](kdatetimeedit.md#setTimeListInterval)().

Any invalid or duplicate times will be ignored, and the list will be sorted.

The minimum and maximum time will automatically be set to the earliest and latest value in the list.

`timeList` the list of times able to be selected

`minWarnMsg` the minimum warning message

`maxWarnMsg` the maximum warning message

*See also* [timeList](kdatetimeedit.md#timeList)()

### \[slot\] void KDateTimeEdit::setTimeListInterval(int *minutes*) {#setTimeListInterval}

Set the interval between times able to be selected from the drop-down.

The combo drop-down will be populated with times every `minutes` apart, starting from the minimumTime() and ending at maximumTime().

If the ForceInterval option is set then any time manually typed into the combo line edit will be forced to the nearest interval.

This interval must be an exact divisor of the valid time range hours. For example with the default 24 hour range `interval` must divide 1440 minutes exactly, meaning 1, 6 and 90 are valid but 7, 31 and 91 are not.

Setting the time list interval will override any time list previously set via [setTimeList](kdatetimeedit.md#setTimeList)().

`minutes` the time list interval to display

> **Note:** Setter function for property [timeListInterval](kdatetimeedit.md#timeListInterval-prop).

*See also* [timeListInterval](kdatetimeedit.md#timeListInterval)()

### \[slot\] void KDateTimeEdit::setTimeZone(const QTimeZone &*zone*) {#setTimeZone}

Set the current time zone

`zone` the new zone

*See also* [timeZone](kdatetimeedit.md#timeZone)()

### \[slot\] void KDateTimeEdit::setTimeZones(const QList\<QTimeZone\> &*zones*) {#setTimeZones}

Set the time zones able to be selected

`zones` the time zones to display

*See also* [timeZones](kdatetimeedit.md#timeZones)()

### QTime KDateTimeEdit::time() const {#time}

Return the currently selected time

> **Note:** Getter function for property [time](kdatetimeedit.md#time-prop).

*See also* [setTime](kdatetimeedit.md#setTime)()

### \[signal\] void KDateTimeEdit::timeChanged(const QTime &*time*) {#timeChanged}

Signal if the time has been changed either manually by the user or programmatically.

The returned time may be invalid.

`time` the new time

> **Note:** Notifier signal for property [time](kdatetimeedit.md#time-prop).

### QLocale::FormatType KDateTimeEdit::timeDisplayFormat() const {#timeDisplayFormat}

Return the currently set time format

By default this is the Short Format

*See also* [setTimeDisplayFormat](kdatetimeedit.md#setTimeDisplayFormat)()

### \[signal\] void KDateTimeEdit::timeEdited(const QTime &*time*) {#timeEdited}

Signal if the time is being manually edited by the user.

The returned time may be invalid.

`time` the new time

### \[signal\] void KDateTimeEdit::timeEntered(const QTime &*time*) {#timeEntered}

Signal if the time has been manually entered by the user.

The returned time may be invalid.

`time` the new time

### QList\<QTime\> KDateTimeEdit::timeList() const {#timeList}

Return the list of times able to be selected in the drop-down.

*See also* [setTimeList](kdatetimeedit.md#setTimeList)(), [timeListInterval](kdatetimeedit.md#timeListInterval)(), [setTimeListInterval](kdatetimeedit.md#setTimeListInterval)()

### int KDateTimeEdit::timeListInterval() const {#timeListInterval}

Return the time list interval able to be selected

> **Note:** Getter function for property [timeListInterval](kdatetimeedit.md#timeListInterval-prop).

*See also* [setTimeListInterval](kdatetimeedit.md#setTimeListInterval)()

### QTimeZone KDateTimeEdit::timeZone() const {#timeZone}

Return the currently selected time zone

*See also* [setTimeZone](kdatetimeedit.md#setTimeZone)()

### \[signal\] void KDateTimeEdit::timeZoneChanged(const QTimeZone &*zone*) {#timeZoneChanged}

Signal if the time zone has been changed either manually by the user or programmatically.

`zone` the new time zone

### \[signal\] void KDateTimeEdit::timeZoneEntered(const QTimeZone &*zone*) {#timeZoneEntered}

Signal if the time zone has been changed manually by the user.

`zone` the new time zone

### QList\<QTimeZone\> KDateTimeEdit::timeZones() const {#timeZones}

Return the list of time zones able to be selected

*See also* [setTimeZones](kdatetimeedit.md#setTimeZones)()
