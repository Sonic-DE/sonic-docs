---
title: "KHolidays::Holiday Class"
description: "Represents a holiday event."
---

# KHolidays::Holiday Class

Represents a holiday event. [More...](#details)

- **Header:** `#include <KHolidays/Holiday>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS Holidays)`  
  `target_link_libraries(mytarget PRIVATE KF6::Holidays)`

[List of all members, including inherited members](kholidays-holiday-members.md)

## Public Types

- [enum Holiday::DayType](#DayType-enum)
- [Holiday::List](#List-typedef)

## Public Functions

- [Holiday()](#Holiday)
- [Holiday(const KHolidays::Holiday &other)](#Holiday-1)
- [QStringList categoryList() const](#categoryList)
- [KHolidays::Holiday::DayType dayType() const](#dayType)
- [QString description() const](#description)
- [int duration() const](#duration)
- [QString name() const](#name)
- [QDate observedEndDate() const](#observedEndDate)
- [QDate observedStartDate() const](#observedStartDate)
- [bool Holiday::operator\<(const KHolidays::Holiday &rhs) const](#operator-lt)
- [bool Holiday::operator\>(const KHolidays::Holiday &rhs) const](#operator-gt)

## Detailed Description {#details}

## Member Type Documentation {#member-type-documentation}

### enum Holiday::DayType {#DayType-enum}

Describes the date type of the holiday. If any of the holidays on a date are non-workdays types, then the entire day is non-working.

| Constant | Value | Description |
| --- | --- | --- |
| `KHolidays::Holiday::Workday` | `0` | The holiday is a workday |
| `KHolidays::Holiday::NonWorkday` | `1` | The holiday is a real holiday |

### Holiday::List {#List-typedef}

A list of holiday descriptions.

## Member Function Documentation {#member-function-documentation}

### Holiday::Holiday() {#Holiday}

Creates an empty holiday.

### Holiday::Holiday(const KHolidays::Holiday &*other*) {#Holiday-1}

Creates a holiday from an `other` holiday.

### QStringList Holiday::categoryList() const {#categoryList}

Returns a [QStringList](https://doc.qt.io/qt-6/qstringlist.html) of categories for the Holiday.

If the Holiday has no categories then an empty list is returned.

### KHolidays::Holiday::DayType Holiday::dayType() const {#dayType}

Returns the day type of the holiday.

### QString Holiday::description() const {#description}

Returns the description of the Holiday if available

### int Holiday::duration() const {#duration}

Returns the duration of the holiday in days.

### QString Holiday::name() const {#name}

Returns the name of the Holiday.

### QDate Holiday::observedEndDate() const {#observedEndDate}

Returns the observed end date of the holiday.

### QDate Holiday::observedStartDate() const {#observedStartDate}

Returns the observed start date of the holiday.

### bool Holiday::operator\<(const KHolidays::Holiday &*rhs*) const {#operator-lt}

### bool Holiday::operator\>(const KHolidays::Holiday &*rhs*) const {#operator-gt}
