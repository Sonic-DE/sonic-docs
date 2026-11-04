---
title: "KHolidays::SunRiseSet Namespace"
description: "Methods for determining the sunrise and sunset times for a given date and Earth location. Use SunEvents instead. This namespace is deprecated since 6.15. We strongly advise against using it in new code."
---

# KHolidays::SunRiseSet Namespace

Methods for determining the sunrise and sunset times for a given date and Earth location. Use [SunEvents](kholidays-sunevents.md) instead. **This namespace is deprecated since 6.15. We strongly advise against using it in new code.** [More...](#details)

- **Header:** `#include <KHolidays/SunRiseSet>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS Holidays)`  
  `target_link_libraries(mytarget PRIVATE KF6::Holidays)`
- **Status:** Deprecated since 6.15

**This namespace is deprecated since 6.15. We strongly advise against using it in new code.**

## Detailed Description {#details}

## Function Documentation {#function-documentation}

### bool SunRiseSet::isPolarDay(const QDate &*date*, double *latitude*) {#isPolarDay}

Checks whether it is polar day on day `date` at `latitude`.

That is, the sun stays above -0.83° relative to the horizon at all times. Both sunrise/sunset and dawn/dusk times will be invalid for such a day.

`latitude` in degree (-90.0, 90.0)

*See also* [isPolarNight](kholidays-sunriseset.md#isPolarNight)(), [isPolarTwilight](kholidays-sunriseset.md#isPolarTwilight)(), [https://en.wikipedia.org/wiki/Midnight_sun](https://en.wikipedia.org/wiki/Midnight_sun)

### bool SunRiseSet::isPolarNight(const QDate &*date*, double *latitude*) {#isPolarNight}

Checks whether it is polar night on day `date` at `latitude`. That is, the sun stays below -6° relative to the horizon at all times. Both sunrise/sunset and dawn/dusk times will be invalid for such a day.

`latitude` in degree (-90.0, 90.0)

*See also* [isPolarDay](kholidays-sunriseset.md#isPolarDay)(), [isPolarTwilight](kholidays-sunriseset.md#isPolarTwilight)(), [https://en.wikipedia.org/wiki/Polar_night](https://en.wikipedia.org/wiki/Polar_night)

### bool SunRiseSet::isPolarTwilight(const QDate &*date*, double *latitude*) {#isPolarTwilight}

Checks whether it is polar twilight on day `date` at `latitude`. That is, the sun rises at least above -6° relative the horizon during the day, but remains below -0.83° at all times. Sunrise/sunset times will be invalid for such a day, but dawn/dusk times will be available.

`latitude` in degree (-90.0, 90.0)

*See also* [isPolarDay](kholidays-sunriseset.md#isPolarDay)(), [isPolarNight](kholidays-sunriseset.md#isPolarNight)(), [https://en.wikipedia.org/wiki/Polar_night](https://en.wikipedia.org/wiki/Polar_night)

### QTime SunRiseSet::utcDawn(const QDate &*date*, double *latitude*, double *longitude*) {#utcDawn}

Compute the civil dawn time (UTC) for a date and Earth location.

`date` is any valid [QDate](https://doc.qt.io/qt-6/qdate.html).

`latitude` is a floating point representing a valid latitude (-90.0, 90.0)

`longitude` is a floating point representing a valid longitude (-180.0, 180.0)

Returns the [QTime](https://doc.qt.io/qt-6/qtime.html) of the sunrise in UTC.

> **Note:** the latitude and longitude are truncated as needed to fit into their proper range.

*See also* [https://en.wikipedia.org/wiki/Twilight](https://en.wikipedia.org/wiki/Twilight)

### QTime SunRiseSet::utcDusk(const QDate &*date*, double *latitude*, double *longitude*) {#utcDusk}

Compute the civil dawn time (UTC) for a date and Earth location.

`date` is any valid [QDate](https://doc.qt.io/qt-6/qdate.html).

`latitude` is a floating point representing a valid latitude (-90.0, 90.0)

`longitude` is a floating point representing a valid longitude (-180.0, 180.0)

Returns the [QTime](https://doc.qt.io/qt-6/qtime.html) of the sunset in UTC.

> **Note:** the latitude and longitude are truncated as needed to fit into their proper range.

*See also* [https://en.wikipedia.org/wiki/Twilight](https://en.wikipedia.org/wiki/Twilight)

### QTime SunRiseSet::utcSunrise(const QDate &*date*, double *latitude*, double *longitude*) {#utcSunrise}

Compute the sunrise time (UTC) for a date and Earth location.

`date` is any valid [QDate](https://doc.qt.io/qt-6/qdate.html).

`latitude` is a floating point representing a valid latitude (-90.0, 90.0)

`longitude` is a floating point representing a valid longitude (-180.0, 180.0)

Returns the [QTime](https://doc.qt.io/qt-6/qtime.html) of the sunrise in UTC.

> **Note:** the latitude and longitude are truncated as needed to fit into their proper range.

### QTime SunRiseSet::utcSunset(const QDate &*date*, double *latitude*, double *longitude*) {#utcSunset}

Compute the sunset time (UTC) for a date and Earth location.

`date` is any valid [QDate](https://doc.qt.io/qt-6/qdate.html).

`latitude` is a floating point representing a valid latitude (-90.0, 90.0)

`longitude` is a floating point representing a valid longitude (-180.0, 180.0)

Returns the [QTime](https://doc.qt.io/qt-6/qtime.html) of the sunset in UTC.

> **Note:** the latitude and longitude are truncated as needed to fit into their proper range.
