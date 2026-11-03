---
title: "KHolidays::AstroSeasons Class"
description: "Represents and manages the Astronomical Seasons (solstices and equinoxes)."
---

# KHolidays::AstroSeasons Class

Represents and manages the Astronomical Seasons (solstices and equinoxes). [More...](#details)

- **Header:** `#include <KHolidays/AstroSeasons>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS Holidays)`  
  `target_link_libraries(mytarget PRIVATE KF6::Holidays)`

[List of all members, including inherited members](kholidays-astroseasons-members.md)

## Public Types

- [enum AstroSeasons::Season](#Season-enum)

## Static Public Members

- [KHolidays::AstroSeasons::Season seasonAtDate(const QDate &date)](#seasonAtDate)
- [QDate seasonDate(KHolidays::AstroSeasons::Season season, int year)](#seasonDate)
- [QString seasonName(KHolidays::AstroSeasons::Season season)](#seasonName)
- [QString seasonNameAtDate(const QDate &date)](#seasonNameAtDate)

## Detailed Description {#details}

For the purposes of this class, we sometimes use the shorthand of "Season" where we really mean "Astronomical Season".

An Astronomical Season can be one of the following:

- June solstice
- December solstice
- March equinox
- September equinox

A very good description of the astronomical seasons can be read at the Wikipedia, https://en.wikipedia.org/wiki/Seasons

Note that this class represents the "Astronomical Seasons" and not the traditional "Seasons" which vary widely by culture.

## Member Type Documentation {#member-type-documentation}

### enum AstroSeasons::Season {#Season-enum}

| Constant |   |
| --- | --- |
| `KHolidays::AstroSeasons::JuneSolstice` | `0` |
| `KHolidays::AstroSeasons::DecemberSolstice` | `1` |
| `KHolidays::AstroSeasons::MarchEquinox` | `2` |
| `KHolidays::AstroSeasons::SeptemberEquinox` | `3` |
| `KHolidays::AstroSeasons::None` | `4` |

## Member Function Documentation {#member-function-documentation}

### \[static\] KHolidays::AstroSeasons::Season AstroSeasons::seasonAtDate(const QDate &*date*) {#seasonAtDate}

Return the season for the specified Gregorian date. The enum 'None' is returned if one of the supported seasons does not occur on the date.

`date` compute the season for the specified Gregorian date.

### \[static\] QDate AstroSeasons::seasonDate(KHolidays::AstroSeasons::Season *season*, int *year*) {#seasonDate}

Return the Gregorian date on which the season occurs in given year.

`season` Season to return a date for

`year` Year for which to return the date

### \[static\] QString AstroSeasons::seasonName(KHolidays::AstroSeasons::Season *season*) {#seasonName}

Return the string representation of season.

`season` astronomical season.

### \[static\] QString AstroSeasons::seasonNameAtDate(const QDate &*date*) {#seasonNameAtDate}

Return the season as a text string for the specified date. A null string is returned if one of the supported seasons does not occur on the date.

`date` compute the season for the specified Gregorian date.
