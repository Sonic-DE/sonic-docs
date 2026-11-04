---
title: "KHolidays Namespace"
description: "Dates for holidays and other special events."
---

# KHolidays Namespace

Dates for holidays and other special events. [More...](#details)

- **Header:** `#include <KHolidays>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS Holidays)`  
  `target_link_libraries(mytarget PRIVATE KF6::Holidays)`

## Detailed Description {#details}

## Classes {#classes}

### class [AstroSeasons](kholidays-astroseasons.md)

Represents and manages the Astronomical Seasons (solstices and equinoxes).

### class [Holiday](kholidays-holiday.md)

Represents a holiday event.

### class [HolidayRegion](kholidays-holidayregion.md)

Represents a holiday region.

### class [LunarPhase](kholidays-lunarphase.md)

Represents and manages a Lunar Phase.

### class [SunEvents](kholidays-sunevents.md)

The [SunEvents](kholidays-sunevents.md) type provides dates for solar events, for example sunset or sunrise.

### class [Zodiac](kholidays-zodiac.md)

Represents and manages the Zodiac calendar.

## Function Documentation {#function-documentation}

### \[since 6.26.0\] QStringList KHolidays::allHolidayCategories() {#allHolidayCategories}

Returns a list of all legal holiday categories.

This function was introduced in Qt 6.26.0.

### \[since 6.26\] QString KHolidays::holidayCategoryDescription(const QString &*category*) {#holidayCategoryDescription}

Returns a string containing a description of the specified category (for use in tooltips, for example). An empty [QString](https://doc.qt.io/qt-6/qstring.html) is returned for an illegal category.

This function was introduced in Qt 6.26.

### \[since 6.26.0\] bool KHolidays::isHolidayCategoryValid(const QString &*category*) {#isHolidayCategoryValid}

Returns if the specified string is a valid holiday category.

This function was introduced in Qt 6.26.0.

### \[since 6.26.0\] QString KHolidays::translateHolidayCategory(const QString &*category*) {#translateHolidayCategory}

Returns the translated string associated with the specified holiday category. An empty [QString](https://doc.qt.io/qt-6/qstring.html) is returned for an illegal category.

This function was introduced in Qt 6.26.0.
