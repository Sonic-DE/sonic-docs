---
title: "KHolidays::Zodiac Class"
description: "Represents and manages the Zodiac calendar."
---

# KHolidays::Zodiac Class

Represents and manages the Zodiac calendar. [More...](#details)

- **Header:** `#include <KHolidays/Zodiac>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS Holidays)`  
  `target_link_libraries(mytarget PRIVATE KF6::Holidays)`

[List of all members, including inherited members](kholidays-zodiac-members.md)

## Public Types

- [enum Zodiac::ZodiacSigns](#ZodiacSigns-enum)
- [enum Zodiac::ZodiacType](#ZodiacType-enum)

## Public Functions

- [Zodiac(KHolidays::Zodiac::ZodiacType type)](#Zodiac)
- [KHolidays::Zodiac::ZodiacSigns signAtDate(const QDate &date) const](#signAtDate)
- [QString signNameAtDate(const QDate &date) const](#signNameAtDate)

## Static Public Members

- [QString signName(KHolidays::Zodiac::ZodiacSigns sign)](#signName)
- [QString signSymbol(KHolidays::Zodiac::ZodiacSigns sign)](#signSymbol)

## Detailed Description {#details}

The Tropical and Sidereal Zodiacs are supported.

A very good description of the Zodiac calendars can be read at the Wikipedia, https://en.wikipedia.org/wiki/Zodiac

Disclaimer: I am by no means a Zodiac expert. I put together this software based on some quick scanning of documents I found on the WWW. Feel free to contact me about this code if you have improvements.

```cpp
Sign         Symbol               Birthdates
                       Tropical              Sidereal
Aries        ram       Mar 21 - Apr 19       Apr 14 - May 14
Taurus       bull      Apr 20 - May 20       May 15 - Jun 14
Gemini       twins     May 21 - Jun 20       Jun 15 - Jul 16
Cancer       crab      Jun 21 - Jul 22       Jul 17 - Aug 16
Leo          lion      Jul 23 - Aug 22       Aug 17 - Sep 16
Virgo        virgin    Aug 23 - Sep 22       Sep 17 - Oct 17
Libra        scale     Sep 23 - Oct 22       Oct 18 - Nov 16
Scorpio      scorpion  Oct 23 - Nov 21       Nov 17 - Dec 15
Sagittarius  archer    Nov 22 - Dec 21       Dec 16 - Jan 14
Capricorn    goat      Dec 22 - Jan 19       Jan 15 - Feb 12
Aquarius     water     Jan 20 - Feb 18       Feb 13 - Mar 14
Pisces       fish      Feb 19 - Mar 20       Mar 15 - Apr 13
```

## Member Type Documentation {#member-type-documentation}

### enum Zodiac::ZodiacSigns {#ZodiacSigns-enum}

| Constant |   |
| --- | --- |
| `KHolidays::Zodiac::Aries` | `0` |
| `KHolidays::Zodiac::Taurus` | `1` |
| `KHolidays::Zodiac::Gemini` | `2` |
| `KHolidays::Zodiac::Cancer` | `3` |
| `KHolidays::Zodiac::Leo` | `4` |
| `KHolidays::Zodiac::Virgo` | `5` |
| `KHolidays::Zodiac::Libra` | `6` |
| `KHolidays::Zodiac::Scorpio` | `7` |
| `KHolidays::Zodiac::Sagittarius` | `8` |
| `KHolidays::Zodiac::Capricorn` | `9` |
| `KHolidays::Zodiac::Aquarius` | `10` |
| `KHolidays::Zodiac::Pisces` | `11` |
| `KHolidays::Zodiac::None` | `12` |

### enum Zodiac::ZodiacType {#ZodiacType-enum}

| Constant |   |
| --- | --- |
| `KHolidays::Zodiac::Tropical` | `0` |
| `KHolidays::Zodiac::Sidereal` | `1` |

## Member Function Documentation {#member-function-documentation}

### \[explicit\] Zodiac::Zodiac(KHolidays::Zodiac::ZodiacType *type*) {#Zodiac}

### KHolidays::Zodiac::ZodiacSigns Zodiac::signAtDate(const QDate &*date*) const {#signAtDate}

Return the Zodiac sign for the specified Gregorian date. The enum 'None' is returned if one of the supported signs does not occur on the date.

`date` compute the Zodiac sign for the specified Gregorian date.

### \[static\] QString Zodiac::signName(KHolidays::Zodiac::ZodiacSigns *sign*) {#signName}

Return the string representation of Zodiac sign.

`sign` Zodiac sign.

### QString Zodiac::signNameAtDate(const QDate &*date*) const {#signNameAtDate}

Return the Zodiac sign as a text string for the specified date. A null string is returned if one of the supported Zodiac signs does not occur on the date.

`date` compute the Zodiac sign for the specified Gregorian date.

### \[static\] QString Zodiac::signSymbol(KHolidays::Zodiac::ZodiacSigns *sign*) {#signSymbol}

Convert the Zodiac sign to a Zodiac symbol.
