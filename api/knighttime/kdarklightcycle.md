---
title: "KDarkLightCycle Class"
description: "The KDarkLightCycle provides information about the light-dark cycle for a single day."
---

# KDarkLightCycle Class

The [KDarkLightCycle](kdarklightcycle.md) provides information about the light-dark cycle for a single day. [More...](#details)

- **Header:** `#include <KDarkLightCycle>`
- **CMake:** `find_package(KNightTime REQUIRED)`  
  `target_link_libraries(mytarget PRIVATE KNightTime::KNightTime)`

[List of all members, including inherited members](kdarklightcycle-members.md)

## Public Functions

- [KDarkLightCycle()](#KDarkLightCycle)
- [KDarkLightCycle(const QDateTime &noonDateTime, const KDarkLightTransition &morning, const KDarkLightTransition &evening)](#KDarkLightCycle-1)
- [KDarkLightTransition evening() const](#evening)
- [KDarkLightCycle extrapolated(const QDateTime &referenceDateTime) const](#extrapolated)
- [KDarkLightTransition morning() const](#morning)
- [std::optional\<KDarkLightTransition\> nextTransition(const QDateTime &dateTime) const](#nextTransition)
- [QDateTime noonDateTime() const](#noonDateTime)
- [std::optional\<KDarkLightTransition\> previousTransition(const QDateTime &dateTime) const](#previousTransition)

## Detailed Description {#details}

## Member Function Documentation {#member-function-documentation}

### KDarkLightCycle::KDarkLightCycle() {#KDarkLightCycle}

Constructs an invalid [KDarkLightCycle](kdarklightcycle.md).

### KDarkLightCycle::KDarkLightCycle(const QDateTime &*noonDateTime*, const KDarkLightTransition &*morning*, const KDarkLightTransition &*evening*) {#KDarkLightCycle-1}

Construcuts an [KDarkLightCycle](kdarklightcycle.md) with specified `noonDateTime`, `morning`, and `evening`.

### KDarkLightTransition KDarkLightCycle::evening() const {#evening}

Returns the evening transition.

### KDarkLightCycle KDarkLightCycle::extrapolated(const QDateTime &*referenceDateTime*) const {#extrapolated}

Computes a new dark-light cycle that includes the specified `referenceDateTime` based on the data in this cycle.

### KDarkLightTransition KDarkLightCycle::morning() const {#morning}

Returns the morning transition.

### std::optional\<KDarkLightTransition\> KDarkLightCycle::nextTransition(const QDateTime &*dateTime*) const {#nextTransition}

Returns the next transition for the specified `dateTime`. If the given date and time comes after the evening, a `std::nullopt` value will be returned.

### QDateTime KDarkLightCycle::noonDateTime() const {#noonDateTime}

Returns the date and time of the noon.

### std::optional\<KDarkLightTransition\> KDarkLightCycle::previousTransition(const QDateTime &*dateTime*) const {#previousTransition}

Returns the previous transition for the specified `dateTime`. If the given date and time comes before the morning, a `std::nullopt` value will be returned.
