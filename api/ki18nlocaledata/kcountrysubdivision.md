---
title: "KCountrySubdivision Class"
description: "Information about an ISO 3166-2 country subdivision."
---

# KCountrySubdivision Class

Information about an ISO 3166-2 country subdivision. [More...](#details)

- **Header:** `#include <KCountrySubdivision>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS I18n)`  
  `target_link_libraries(mytarget PRIVATE KF6::I18nLocaleData)`

[List of all members, including inherited members](kcountrysubdivision-members.md)

## Properties

- [\[read-only\] code : QString](#code-prop)
- [\[read-only\] country : KCountry](#country-prop)
- [\[read-only\] name : QString](#name-prop)
- [\[read-only\] parent : KCountrySubdivision](#parent-prop)
- [\[read-only\] subdivisions : QList\<KCountrySubdivision\>](#subdivisions-prop)
- [\[read-only\] timeZoneIds : QStringList](#timeZoneIds-prop)

## Public Functions

- [KCountrySubdivision()](#KCountrySubdivision)
- [QString code() const](#code)
- [KCountry country() const](#country)
- [bool isValid() const](#isValid)
- [QString name() const](#name)
- [KCountrySubdivision parent() const](#parent)
- [QList\<KCountrySubdivision\> subdivisions() const](#subdivisions)
- [QList\<const char \*\> timeZoneIds() const](#timeZoneIds)
- [bool KCountrySubdivision::operator==(const KCountrySubdivision &other) const](#operator-eq-eq)

## Static Public Members

- [KCountrySubdivision fromCode(QStringView code)](#fromCode)
- [KCountrySubdivision fromCode(const char \*code)](#fromCode-1)
- [KCountrySubdivision fromLocation(float latitude, float longitude)](#fromLocation)

## Detailed Description {#details}

> **Note:** This requires the \[iso-codes\](https://salsa.debian.org/iso-codes-team/iso-codes/) data files and translation catalogs to be available at runtime.

See [KCountry](kcountry.md) for the data sources.

## Property Documentation {#property-documentation}

### \[read-only\] code : QString {#code-prop}

**Access functions:**

- `QString` **[code](kcountrysubdivision.md#code)**() const

### \[read-only\] country : KCountry {#country-prop}

**Access functions:**

- `KCountry` **[country](kcountrysubdivision.md#country)**() const

### \[read-only\] name : QString {#name-prop}

**Access functions:**

- `QString` **[name](kcountrysubdivision.md#name)**() const

### \[read-only\] parent : KCountrySubdivision {#parent-prop}

**Access functions:**

- `KCountrySubdivision` **[parent](kcountrysubdivision.md#parent)**() const

### \[read-only\] subdivisions : QList\<KCountrySubdivision\> {#subdivisions-prop}

**Access functions:**

- `QList`\<`KCountrySubdivision`\> **[subdivisions](kcountrysubdivision.md#subdivisions)**() const

### \[read-only\] timeZoneIds : QStringList {#timeZoneIds-prop}

## Member Function Documentation {#member-function-documentation}

### KCountrySubdivision::KCountrySubdivision() {#KCountrySubdivision}

Creates an invalid/empty [KCountrySubdivision](kcountrysubdivision.md) instance. See the fromX() methods for creating a valid instance.

### QString KCountrySubdivision::code() const {#code}

ISO 3166-2 country subdivision code.

> **Note:** Getter function for property [code](kcountrysubdivision.md#code-prop).

### KCountry KCountrySubdivision::country() const {#country}

Country this subdivision belongs to.

> **Note:** Getter function for property [country](kcountrysubdivision.md#country-prop).

### \[static\] KCountrySubdivision KCountrySubdivision::fromCode(QStringView *code*) {#fromCode}

Create a [KCountrySubdivision](kcountrysubdivision.md) instance from an ISO 3166-2 code.

### \[static\] KCountrySubdivision KCountrySubdivision::fromCode(const char \**code*) {#fromCode-1}

Create a [KCountrySubdivision](kcountrysubdivision.md) instance from an ISO 3166-2 code.

### \[static\] KCountrySubdivision KCountrySubdivision::fromLocation(float *latitude*, float *longitude*) {#fromLocation}

Looks up the country subdivision at the given geographic coordinate. This can return an invalid object if the country subdivision could not be determined. This can happen in a number of cases:

- on oceans
- in polar regions
- close to a land border
- in disputed territories

> **Note:** It is possible for [KCountry::fromLocation](kcountry.md#fromLocation)() to return a valid result despite this method returning an invalid result.

### bool KCountrySubdivision::isValid() const {#isValid}

Returns `false` if this is an empty/invalid/default constructed instance, `true` otherwise.

### QString KCountrySubdivision::name() const {#name}

Translated country subdivision name.

> **Note:** Getter function for property [name](kcountrysubdivision.md#name-prop).

### KCountrySubdivision KCountrySubdivision::parent() const {#parent}

Parent subdivision, if this is a subdivision of another subdivision. Returns an invalid element for top-level subdivisions.

> **Note:** Getter function for property [parent](kcountrysubdivision.md#parent-prop).

### QList\<KCountrySubdivision\> KCountrySubdivision::subdivisions() const {#subdivisions}

Subdivisions of this subdivision, if any. This is only relevant for countries with multiple ISO 3166-2 subdivision levels.

> **Note:** Getter function for property [subdivisions](kcountrysubdivision.md#subdivisions-prop).

### QList\<const char \*\> KCountrySubdivision::timeZoneIds() const {#timeZoneIds}

Timezones in use in this country subdivision.

### bool KCountrySubdivision::operator==(const KCountrySubdivision &*other*) const {#operator-eq-eq}
