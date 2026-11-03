---
title: "KHolidays::LunarPhase Class"
description: "Represents and manages a Lunar Phase."
---

# KHolidays::LunarPhase Class

Represents and manages a Lunar Phase. [More...](#details)

- **Header:** `#include <KHolidays/LunarPhase>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS Holidays)`  
  `target_link_libraries(mytarget PRIVATE KF6::Holidays)`

[List of all members, including inherited members](kholidays-lunarphase-members.md)

## Public Types

- [enum LunarPhase::Phase](#Phase-enum)

## Static Public Members

- [KHolidays::LunarPhase::Phase phaseAtDate(const QDate &date)](#phaseAtDate)
- [QString phaseName(KHolidays::LunarPhase::Phase phase)](#phaseName)
- [QString phaseNameAtDate(const QDate &date)](#phaseNameAtDate)

## Detailed Description {#details}

A Lunar Phase can be one of the following:

- "new": the moon is not visible; or traditionally: first visible crescent of the Moon. For religious purposes, the new month begins when the first crescent moon can be seen. Thus, it is impossible to be certain in advance of when months will begin; in particular, the exact date on which Ramadan will begin is not known in advance. In Saudi Arabia, observers are sent up in airplanes if the weather is cloudy when the new moon is expected.
- "waxing crescent": between "new" and "first quarter".
- "first quarter": the right 50% of the moon is visible.
- "waxing gibbous": between "first quarter" and "full".
- "full": the moon is fully visible.
- "waning gibbous": between "full" and "last quarter".
- "last quarter": the left 50% of the moon is visible.
- "waning crescent": between "last quarter" and "new".

A very good description of the lunar phases can be read at the Wikipedia, https://en.wikipedia.org/wiki/Lunar_phase

The phase is computed for noon in the system timezone.

## Member Type Documentation {#member-type-documentation}

### enum LunarPhase::Phase {#Phase-enum}

Phases of the moon, in traditional English notation. The phase `None` is used only as an error indicator, for instance in phase().

| Constant | Value | Description |
| --- | --- | --- |
| `KHolidays::LunarPhase::NewMoon` | `0` | New moon phase |
| `KHolidays::LunarPhase::FirstQuarter` | `1` | First quarter of moon phase |
| `KHolidays::LunarPhase::LastQuarter` | `2` | Last quarter of moon phase |
| `KHolidays::LunarPhase::FullMoon` | `3` | Full moon phase |
| `KHolidays::LunarPhase::None` | `4` | Indication for error |
| `KHolidays::LunarPhase::WaxingCrescent (since Qt 5.94)` | `5` |   |
| `KHolidays::LunarPhase::WaxingGibbous (since Qt 5.94)` | `6` |   |
| `KHolidays::LunarPhase::WaningGibbous (since Qt 5.94)` | `7` |   |
| `KHolidays::LunarPhase::WaningCrescent (since Qt 5.94)` | `8` |   |

## Member Function Documentation {#member-function-documentation}

### \[static\] KHolidays::LunarPhase::Phase LunarPhase::phaseAtDate(const QDate &*date*) {#phaseAtDate}

Return the lunar phase for the specified Gregorian date. The enum 'None' is returned if one of the supported phases does not occur on the date.

`date` compute the lunar phase for the specified Gregorian date.

### \[static\] QString LunarPhase::phaseName(KHolidays::LunarPhase::Phase *phase*) {#phaseName}

Return the string representation of phase.

`phase` the lunar phase.

### \[static\] QString LunarPhase::phaseNameAtDate(const QDate &*date*) {#phaseNameAtDate}

Return the lunar phase as a text string for the specified date. A null string is returned if one of the supported phases does not occur on the date.

`date` compute the lunar phase for the specified Gregorian date.
