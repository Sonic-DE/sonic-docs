---
title: "KHolidays::SunEvents Class"
description: "The SunEvents type provides dates for solar events, for example sunset or sunrise. This class was introduced in Qt 6.15."
---

# KHolidays::SunEvents Class

The [SunEvents](kholidays-sunevents.md) type provides dates for solar events, for example sunset or sunrise. This class was introduced in Qt 6.15. [More...](#details)

- **Header:** `#include <KHolidays/SunEvents>`
- **Since:** Qt 6.15
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS Holidays)`  
  `target_link_libraries(mytarget PRIVATE KF6::Holidays)`

[List of all members, including inherited members](kholidays-sunevents-members.md)

## Public Functions

- [SunEvents(const QDateTime &dateTime, double latitude, double longitude)](#SunEvents-1)
- [SunEvents(const KHolidays::SunEvents &other)](#SunEvents)
- [~SunEvents()](#dtor.SunEvents)
- [QDateTime astronomicalDawn() const](#astronomicalDawn)
- [QDateTime astronomicalDusk() const](#astronomicalDusk)
- [QDateTime civilDawn() const](#civilDawn)
- [QDateTime civilDusk() const](#civilDusk)
- [bool isPolarDay() const](#isPolarDay)
- [bool isPolarNight() const](#isPolarNight)
- [bool isPolarTwilight() const](#isPolarTwilight)
- [QDateTime nauticalDawn() const](#nauticalDawn)
- [QDateTime nauticalDusk() const](#nauticalDusk)
- [QDateTime solarNoon() const](#solarNoon)
- [QDateTime sunrise() const](#sunrise)
- [QDateTime sunset() const](#sunset)
- [KHolidays::SunEvents &SunEvents::operator=(const KHolidays::SunEvents &other)](#operator-eq)

## Detailed Description {#details}

The [SunEvents](kholidays-sunevents.md) type allows you to find dates for solar events at the specified location and date, for example sunset or sunrise. It can also be used to determine whether midnight sun or polar night can be observed for the given time and location.

The following example shows how to use the [SunEvents](kholidays-sunevents.md) type to determine sunrise and sunset times in Kyiv:

```cpp
const SunEvents sunEvents(QDateTime::currentDateTime(), 50.45, 30.52);
qDebug() << "Sunrise at:" << sunEvents.sunrise().toUTC();
qDebug() << "Sunset at:" << sunEvents.sunset().toUTC();
```

> **Note:** Due to various approximations, the provided event times are not suitable for the scientific purposes. However, they are good enough for other purposes where accuracy is not critical, for example adjusting the screen color temperature depending on the elevation of the sun.

## Member Function Documentation {#member-function-documentation}

### SunEvents::SunEvents(const QDateTime &*dateTime*, double *latitude*, double *longitude*) {#SunEvents-1}

Constructs the [SunEvents](kholidays-sunevents.md) with the specified `dateTime`, `latitude`, and `longitude`.

The `dateTime` is used to find the closest solar noon. The times of solar events are provided relative to the closest solar noon.

The `latitude` is specified in decimal degrees between -90° and 90° inclusive. If the given latitude is outside the valid range, it will be clamped to fit into the \[-90, 90\] range.

The `longitude` is specified in decimal degrees between -180° and 180° inclusive. If the given longitude is outside the valid range, it will be clamped to fit into the \[-180, 180\] range.

### SunEvents::SunEvents(const KHolidays::SunEvents &*other*) {#SunEvents}

Constructs a copy of the `other` sun events.

### \[noexcept\] SunEvents::~SunEvents() {#dtor.SunEvents}

Destroys the sun events.

### QDateTime SunEvents::astronomicalDawn() const {#astronomicalDawn}

The date and time of astronomical sunrise when the sun is 18° below the horizon. At extreme latitudes, the sun may not rise during certain days, in which case, this function will return an invalid [QDateTime](https://doc.qt.io/qt-6/qdatetime.html).

Astronomical dawn is that point in time at which the sun starts lightening the sky. Prior to this time, the sky is completely dark.

*See also* [astronomicalDusk](kholidays-sunevents.md#astronomicalDusk)()

### QDateTime SunEvents::astronomicalDusk() const {#astronomicalDusk}

The date and time of astronomical sunset when the sun is 18° below the horizon. At extreme latitudes, the sun may not set during certain days, in which case, this function will return an invalid [QDateTime](https://doc.qt.io/qt-6/qdatetime.html).

Astronomical dusk is that point in time at which the sun no longer illuminates the sky.

*See also* [astronomicalDawn](kholidays-sunevents.md#astronomicalDawn)()

### QDateTime SunEvents::civilDawn() const {#civilDawn}

The date and time of astronomical sunrise when the sun is 6° below the horizon. At extreme latitudes, the sun may not rise during certain days, in which case, this function will return an invalid [QDateTime](https://doc.qt.io/qt-6/qdatetime.html).

Civil dawn is that point in time at which there is enough of light for most objects to be seen and outdoor activities may begin.

*See also* [civilDusk](kholidays-sunevents.md#civilDusk)()

### QDateTime SunEvents::civilDusk() const {#civilDusk}

The date and time of astronomical sunset when the sun is 6° below the horizon. At extreme latitudes, the sun may not set during certain days, in which case, this function will return an invalid [QDateTime](https://doc.qt.io/qt-6/qdatetime.html).

Civil dusk is that point in time at which the light starts to fade but no artificial light is needed for outdoor activities. The sky is often colored red and orange at this time.

*See also* [civilDawn](kholidays-sunevents.md#civilDawn)()

### bool SunEvents::isPolarDay() const {#isPolarDay}

Returns `true` if it is polar day, also known as midnight sun; otherwise returns `false`.

Polar day is a natural phenomenon when the sun stays above -0.83° relative to the horizon at all times. Both sunrise/sunset and dawn/dusk times will be invalid for such a day.

*See also* [isPolarNight](kholidays-sunevents.md#isPolarNight)(), [isPolarTwilight](kholidays-sunevents.md#isPolarTwilight)()

### bool SunEvents::isPolarNight() const {#isPolarNight}

Returns `true` if it is polar night; otherwise returns `false`.

Polar night is a natural phenomenon when the sun stays below -6° relative to the horizon at all times. Both sunrise/sunset and dawn/dusk times will be invalid for such a day.

*See also* [isPolarDay](kholidays-sunevents.md#isPolarDay)(), [isPolarTwilight](kholidays-sunevents.md#isPolarTwilight)()

### bool SunEvents::isPolarTwilight() const {#isPolarTwilight}

Returns `true` if it is polar twilight; otherwise returns `false`.

Polar twilight is a natural phenomenon when the sun rises at least above -6° relative the horizon during the day, but remains below -0.83° at all times. Sunrise/sunset times will be invalid for such a day, but dawn/dusk times will be available.

*See also* [isPolarDay](kholidays-sunevents.md#isPolarDay)(), [isPolarNight](kholidays-sunevents.md#isPolarNight)()

### QDateTime SunEvents::nauticalDawn() const {#nauticalDawn}

The date and time of astronomical sunrise when the sun is 12° below the horizon. At extreme latitudes, the sun may not rise during certain days, in which case, this function will return an invalid [QDateTime](https://doc.qt.io/qt-6/qdatetime.html).

Nautical dawn is that point in time at which the there is just enough of sunlight for objects to be distinguishable.

*See also* [nauticalDusk](kholidays-sunevents.md#nauticalDusk)()

### QDateTime SunEvents::nauticalDusk() const {#nauticalDusk}

The date and time of astronomical sunset when the sun is 12° below the horizon. At extreme latitudes, the sun may not set during certain days, in which case, this function will return an invalid [QDateTime](https://doc.qt.io/qt-6/qdatetime.html).

Nautical dusk is that point in time at which most stars become visible.

*See also* [nauticalDawn](kholidays-sunevents.md#nauticalDawn)()

### QDateTime SunEvents::solarNoon() const {#solarNoon}

The date and time when the sun is at its highest position in the sky. The provided date and time is always valid.

### QDateTime SunEvents::sunrise() const {#sunrise}

The date and time of astronomical sunrise when the sun is 0.833° below the horizon. At extreme latitudes, the sun may not rise during certain days, in which case, this function will return an invalid [QDateTime](https://doc.qt.io/qt-6/qdatetime.html).

*See also* [sunset](kholidays-sunevents.md#sunset)()

### QDateTime SunEvents::sunset() const {#sunset}

The date and time of astronomical sunset when the sun is 0.833° below the horizon. At extreme latitudes, the sun may not set during certain days, in which case, this function will return an invalid [QDateTime](https://doc.qt.io/qt-6/qdatetime.html).

*See also* [sunrise](kholidays-sunevents.md#sunrise)()

### KHolidays::SunEvents &SunEvents::operator=(const KHolidays::SunEvents &*other*) {#operator-eq}

Assigns `other` to these sun events and returns a reference to these sun events.
