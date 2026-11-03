---
title: "KHolidays::HolidayRegion Class"
description: "Represents a holiday region."
---

# KHolidays::HolidayRegion Class

Represents a holiday region. [More...](#details)

- **Header:** `#include <KHolidays/HolidayRegion>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS Holidays)`  
  `target_link_libraries(mytarget PRIVATE KF6::Holidays)`

[List of all members, including inherited members](kholidays-holidayregion-members.md)

## Public Functions

- [HolidayRegion(const QFileInfo &regionFile)](#HolidayRegion)
- [HolidayRegion(const QString &regionCode = QString())](#HolidayRegion-1)
- [QStringList categories() const](#categories) (since 6.26)
- [QString countryCode() const](#countryCode)
- [QString description() const](#description)
- [bool isHoliday(const QDate &date) const](#isHoliday)
- [bool isValid() const](#isValid)
- [QString languageCode() const](#languageCode)
- [QString name() const](#name)
- [Holiday::List rawHolidays(const QDate &startDate, const QDate &endDate) const](#rawHolidays)
- [Holiday::List rawHolidays(const QDate &startDate, const QDate &endDate, const QString &category) const](#rawHolidays-1)
- [Holiday::List rawHolidaysWithAstroSeasons(const QDate &date) const](#rawHolidaysWithAstroSeasons)
- [Holiday::List rawHolidaysWithAstroSeasons(int calendarYear) const](#rawHolidaysWithAstroSeasons-1)
- [Holiday::List rawHolidaysWithAstroSeasons(const QDate &startDate, const QDate &endDate) const](#rawHolidaysWithAstroSeasons-2)
- [QString regionCode() const](#regionCode)
- [void setCategories(const QStringList &categories)](#setCategories) (since 6.26)

## Static Public Members

- [QString countryCode(const QString &regionCode)](#countryCode-1)
- [QString defaultRegionCode(const QString &country = QString(), const QString &language = QString())](#defaultRegionCode)
- [QString description(const QString &regionCode)](#description-1)
- [bool isValid(const QString &regionCode)](#isValid-1)
- [QString languageCode(const QString &regionCode)](#languageCode-1)
- [QString name(const QString &regionCode)](#name-1)
- [QStringList regionCodes()](#regionCodes)

## Detailed Description {#details}

## Member Function Documentation {#member-function-documentation}

### \[explicit\] HolidayRegion::HolidayRegion(const QFileInfo &*regionFile*) {#HolidayRegion}

Creates a new Holiday Region object from a given holiday file. If file doesn't exist, an empty instance will be created.

`regionFile` The code for the Holiday Region.

### \[explicit\] HolidayRegion::HolidayRegion(const QString &*regionCode* = QString()) {#HolidayRegion-1}

Creates a new Holiday Region object for a given standard Region Code.

`regionCode` The code for the Holiday Region. If null or unknown, an empty instance will be created.

### \[since 6.26\] QStringList HolidayRegion::categories() const {#categories}

Returns the current categories filter list.

This function was introduced in Qt 6.26.

*See also* [setCategories](kholidays-holidayregion.md#setCategories)()

### QString HolidayRegion::countryCode() const {#countryCode}

Return the ISO 3166 country code of the file

May be either just a country code ("US" = USA) or may include a regional identifier ("US-CA" = California). Returns "XX" if not a country.

See https://en.wikipedia.org/wiki/ISO_3166-2

### \[static\] QString HolidayRegion::countryCode(const QString &*regionCode*) {#countryCode-1}

Return the ISO 3166 country code of a given Holiday Region

May be either just a country code ("US" = USA) or may include a regional identifier ("US-CA" = California). Returns "XX" if not a country.

See https://en.wikipedia.org/wiki/ISO_3166-2

`regionCode` The code for the Holiday Region.

> **Warning:** This methods is expensive as it involves parsing the corresponding holiday definition file. Prefer [HolidayRegion::countryCode](kholidays-holidayregion.md#countryCode)().

### \[static\] QString HolidayRegion::defaultRegionCode(const QString &*country* = QString(), const QString &*language* = QString()) {#defaultRegionCode}

Return a reasonable default Holiday Region code

If a required country/language is not provided then the current KDE country/language is used.

`country` The country or region to find a default Holiday Region for. This can be either an ISO 3166-1 or ISO 3166-2 code.

`language` The language to find a default Holiday Region for

Returns the full region code of the default file

> **Warning:** This methods is expensive as it involves parsing all holiday definition files.

### QString HolidayRegion::description() const {#description}

Return the description of the Holiday Region if available

### \[static\] QString HolidayRegion::description(const QString &*regionCode*) {#description-1}

Return the description of a given Holiday Region if available

### bool HolidayRegion::isHoliday(const QDate &*date*) const {#isHoliday}

Checks whether there is any holiday defined for a `date`. The category filter is applied if one is set.

### bool HolidayRegion::isValid() const {#isValid}

Returns whether the instance contains any holiday data.

### \[static\] bool HolidayRegion::isValid(const QString &*regionCode*) {#isValid-1}

Returns whether the Region Code is valid.

### QString HolidayRegion::languageCode() const {#languageCode}

Return the ISO 639-1 language code of the file

May be either just a language code ("en" = US English) or may include a country identifier ("en\_GB" = British English).

### \[static\] QString HolidayRegion::languageCode(const QString &*regionCode*) {#languageCode-1}

Return the ISO 639-1 language code of a given Holiday Region

May be either just a language code ("en" = US English) or may include a country identifier ("en\_GB" = British English).

`regionCode` The code for the Holiday Region.

> **Warning:** This methods is expensive as it involves parsing the corresponding holiday definition file. Prefer [HolidayRegion::languageCode](kholidays-holidayregion.md#languageCode)().

### QString HolidayRegion::name() const {#name}

Return the name of the Holiday Region. This may be a country, region, or type.

### \[static\] QString HolidayRegion::name(const QString &*regionCode*) {#name-1}

Return the name of a given Holiday Region

`regionCode` The code for the Holiday Region.

### Holiday::List HolidayRegion::rawHolidays(const QDate &*startDate*, const QDate &*endDate*) const {#rawHolidays}

Returns the list of holidays that occur between `startDate` and `endDate`. The category filter is applied if one is set.

### Holiday::List HolidayRegion::rawHolidays(const QDate &*startDate*, const QDate &*endDate*, const QString &*category*) const {#rawHolidays-1}

Returns the list of holidays that occur between `startDate` and `endDate` and with `category`. The category filter is ignored. Only the specified category is considered for filtering.

### Holiday::List HolidayRegion::rawHolidaysWithAstroSeasons(const QDate &*date*) const {#rawHolidaysWithAstroSeasons}

Returns the list of holidays and astronomical season dates (equinoxes and solstices) that occur on a `date`. The category filter is applied if one is set.

### Holiday::List HolidayRegion::rawHolidaysWithAstroSeasons(int *calendarYear*) const {#rawHolidaysWithAstroSeasons-1}

Returns the list of holidays and astronomical season dates (equinoxes and solstices) that occur in a Gregorian calendar year `calendarYear`. The category filter is applied if one is set.

### Holiday::List HolidayRegion::rawHolidaysWithAstroSeasons(const QDate &*startDate*, const QDate &*endDate*) const {#rawHolidaysWithAstroSeasons-2}

Returns the list of holidays and astronomical season dates (equinoxes and solstices) that occur between `startDate` and `endDate`. The category filter is applied if one is set.

### QString HolidayRegion::regionCode() const {#regionCode}

Returns the unique Holiday Region code.

Clients should not infer any meaning from the format of the code.

Returns region code, or null if the instance was constructed with an unknown region

### \[static\] QStringList HolidayRegion::regionCodes() {#regionCodes}

Return a list of all available Holiday Region codes.

One of these can then be passed to the constructor for a new [HolidayRegion](kholidays-holidayregion.md) object, or to [name](kholidays-holidayregion.md#name)() or language() to obtain the name and language of the region.

*See also* [name](kholidays-holidayregion.md#name)(), [languageCode](kholidays-holidayregion.md#languageCode)()

### \[since 6.26\] void HolidayRegion::setCategories(const QStringList &*categories*) {#setCategories}

Sets a list of categories to filter the types of holidays that are returned.

This function was introduced in Qt 6.26.

*See also* [categories](kholidays-holidayregion.md#categories)()
