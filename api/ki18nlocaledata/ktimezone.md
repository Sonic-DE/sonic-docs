---
title: "KTimeZone Namespace"
description: "Timezone localization methods."
---

# KTimeZone Namespace

Timezone localization methods. [More...](#details)

- **Header:** `#include <KTimeZone>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS I18n)`  
  `target_link_libraries(mytarget PRIVATE KF6::I18nLocaleData)`

## Detailed Description {#details}

## Function Documentation {#function-documentation}

### KCountry KTimeZone::country(const char \**ianaId*) {#country}

Returns the country a timezone is in.

This only returns a country if the timezone covers exactly one country (but not necessarily the entire country).

For obtaining any country covered by a timezone, see [QTimeZone::territory](https://doc.qt.io/qt-6/qtimezone.html#territory).

### const char \*KTimeZone::fromLocation(float *latitude*, float *longitude*) {#fromLocation}

Returns the timezone at the given geo coordinate.
