---
title: "KDarkLightSchedule Class"
description: "The KDarkLightSchedule type represents a schedule for the dark-light cycle."
---

# KDarkLightSchedule Class

The [KDarkLightSchedule](kdarklightschedule.md) type represents a schedule for the dark-light cycle. [More...](#details)

- **Header:** `#include <KDarkLightSchedule>`
- **CMake:** `find_package(KNightTime REQUIRED)`  
  `target_link_libraries(mytarget PRIVATE KNightTime::KNightTime)`

[List of all members, including inherited members](kdarklightschedule-members.md)

## Public Functions

- [KDarkLightSchedule()](#KDarkLightSchedule)
- [KDarkLightSchedule(const QList\<KDarkLightCycle\> &cycles)](#KDarkLightSchedule-1)
- [QList\<KDarkLightCycle\> cycles() const](#cycles)
- [std::optional\<KDarkLightTransition\> nextTransition(const QDateTime &referenceDateTime) const](#nextTransition)
- [std::optional\<KDarkLightTransition\> previousTransition(const QDateTime &referenceDateTime) const](#previousTransition)
- [QString toState() const](#toState)

## Static Public Members

- [std::optional\<KDarkLightSchedule\> forecast(const QDateTime &dateTime, qreal latitude, qreal longitude, int cycleCount = 7)](#forecast)
- [KDarkLightSchedule forecast(const QDateTime &dateTime, QTime morning = QTime(6, 0), QTime evening = QTime(18, 0), std::chrono::milliseconds transitionDuration = std::minutes(30), int cycleCount = 7)](#forecast-1)
- [std::optional\<KDarkLightSchedule\> fromState(const QString &state)](#fromState)

## Detailed Description {#details}

Example usage:

```cpp
const auto schedule = KDarkLightSchedule::forecast(QDateTime::currentDateTime(), 50.45, 30.52);

qDebug() << "previous transition:" << schedule->previousTransition(QDateTime::currentDateTime());
qDebug() << "next transition:" << schedule->nextTransition(QDateTime::currentDateTime());
```

## Member Function Documentation {#member-function-documentation}

### KDarkLightSchedule::KDarkLightSchedule() {#KDarkLightSchedule}

Constructs a null schedule.

### KDarkLightSchedule::KDarkLightSchedule(const QList\<KDarkLightCycle\> &*cycles*) {#KDarkLightSchedule-1}

Constructs a schedule with the specified `cycles`.

### QList\<KDarkLightCycle\> KDarkLightSchedule::cycles() const {#cycles}

Retruns dark-light cycles stored in this schedule. A null schedule has no cycles in it.

### \[static\] std::optional\<KDarkLightSchedule\> KDarkLightSchedule::forecast(const QDateTime &*dateTime*, qreal *latitude*, qreal *longitude*, int *cycleCount* = 7) {#forecast}

Computes the dark-light schedule for the next `cycleCount` days. Dark-light cycles are computed based on the position of the Sun at the specified `dateTime` and location (`latitude`, `longitude`). The latitude and the longitude are specified in the decimal degrees.

This function may return `std::nullopt` at extreme latitudes if the Sun never rises or sets.

### \[static\] KDarkLightSchedule KDarkLightSchedule::forecast(const QDateTime &*dateTime*, QTime *morning* = QTime(6, 0), QTime *evening* = QTime(18, 0), std::chrono::milliseconds *transitionDuration* = std::chrono::minutes(30), int *cycleCount* = 7) {#forecast-1}

Computes the dark-light schedule for the next `cycleCount` days. The `dateTime` indicates the current date and time. The `morning` and `evening` indicate when the morning and the evening start, respectively. The `transitionDuration` indicates the duration of morning and evening.

### \[static\] std::optional\<KDarkLightSchedule\> KDarkLightSchedule::fromState(const QString &*state*) {#fromState}

Loads a schedule from the specified `state` string. If the `state` is empty or invalid, a std::nullopt value will be returned.

### std::optional\<KDarkLightTransition\> KDarkLightSchedule::nextTransition(const QDateTime &*referenceDateTime*) const {#nextTransition}

Finds the next transition for the specified `referenceDateTime`. If this schedule is null, a `std::nullopt` value will be returned.

### std::optional\<KDarkLightTransition\> KDarkLightSchedule::previousTransition(const QDateTime &*referenceDateTime*) const {#previousTransition}

Finds the previous transition for the specified `referenceDateTime`. If this schedule is null, a `std::nullopt` value will be returned.

### QString KDarkLightSchedule::toState() const {#toState}

Serializes the schedule in a string that can be stored in a config.
