---
title: "Format QML Type"
description: "Provides support for formatting numbers and datetimes in formats that are not supported by QLocale."
---

# Format QML Type

Provides support for formatting numbers and datetimes in formats that are not supported by [QLocale](https://doc.qt.io/qt-6/qlocale.html). [More...](#details)

- Import Statement: import org.kde.coreaddons

## Detailed Description {#details}

*See also* [KFormat](../kcoreaddons/kformat.md)

## Method Documentation {#method-documentation}

### string formatByteSize(double *size*, int *precision* = 1) {#formatByteSize-method}

Converts `size` from bytes to the appropriate string representation

### \[since 6.31\] string formatDateTime(var *object*, string *propertyName*, int *format*, int *options*) {#formatDateTime-method}

Applies time formatting to the [QDateTime](https://doc.qt.io/qt-6/qdatetime.html) value found in the property `propertyName` in object `object`. This indirection is necessary to avoid the [QDateTime](https://doc.qt.io/qt-6/qdatetime.html) value to ever be exposed to QML's JS runtime, which would destroy its timezone information. The formatting itself is done via [KFormat::formatDateTime](../kcoreaddons/kformat.md#formatDateTime), see that for `format` and `options`.

This method was introduced in Qt 6.31.

### string formatDecimalDuration(int *msecs*, int *decimalPlaces* = 2) {#formatDecimalDuration-method}

Given a number of milliseconds, converts that to a string containing the localized equivalent to the requested decimal places.

e.g. given [formatDuration](qml-org-kde-coreaddons-format.md#formatDuration-method)(60000), returns "1.0 minutes"

### string formatDistance(real *distance*, enumeration *options*) {#formatDistance-method}

Formats a distance value given in meters in appropriate units for displaying.

Unless explicitly forced to metric units this uses units approrpiate for the current locale.

### string formatDuration(int *msecs*, KFormat::DurationFormatOptions *options* = KFormat::DefaultDuration) {#formatDuration-method}

Given a number of milliseconds, converts that to a string containing the localized equivalent, e.g. 1:23:45

### string formatRelativeDate(QDateTime *date*, *format*) {#formatRelativeDate-method}

Returns a string formatted to a relative datetime style.

If the dateTime falls within 2 days before or after the current date then a relative date string will be returned, such as:

- Yesterday, 3:00pm
- Today, 3:00pm
- Tomorrow, 3:00pm
- Two days ago, 3:00pm
- In Two days, 3:00pm

If the datetime falls outside this period then the format is used

### string formatRelativeDate(date *date*, *format*) {#formatRelativeDate-method-1}

Returns a string formatted to a relative date style.

If the date falls within 2 days before or after the current date then a relative date string will be returned, such as:

- Yesterday
- Today
- Tomorrow
- Two days ago
- In Two days

If the date falls outside this period then the format is used

### string formatSpelloutDuration(int *msecs*) {#formatSpelloutDuration-method}

Given a number of milliseconds, converts that to a spell-out string containing the localized equivalent.

e.g. given formatSpelloutDuration(60001) returns "1 minute" given formatSpelloutDuration(62005) returns "1 minute and 2 seconds" given formatSpelloutDuration(90060000) returns "1 day and 1 hour"

Units not interesting to the user, for example seconds or minutes when the first unit is day, are not returned because they are irrelevant. The same applies for seconds when the first unit is hour.

### \[since 6.16\] string formatTime(var *object*, string *propertyName*, int *format*, int *options*) {#formatTime-method}

Applies time formatting to the [QDateTime](https://doc.qt.io/qt-6/qdatetime.html) value found in the property `propertyName` in object `object`. This indirection is necessary to avoid the [QDateTime](https://doc.qt.io/qt-6/qdatetime.html) value to ever be exposed to QML's JS runtime, which would destroy its timezone information. The formatting itself is done via [KFormat::formatTime](../kcoreaddons/kformat.md#formatTime), see that for `format` and `options`.

This method was introduced in Qt 6.16.
