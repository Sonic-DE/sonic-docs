---
title: "KCountry Class"
description: "Information about an ISO 3166-1 country."
---

# KCountry Class

Information about an ISO 3166-1 country. [More...](#details)

- **Header:** `#include <KCountry>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS I18n)`  
  `target_link_libraries(mytarget PRIVATE KF6::I18nLocaleData)`

[List of all members, including inherited members](kcountry-members.md)

## Properties

- [\[read-only\] alpha2 : QString](#alpha2-prop)
- [\[read-only\] alpha3 : QString](#alpha3-prop)
- [\[read-only\] currencyCode : QString](#currencyCode-prop)
- [\[read-only\] emojiFlag : QString](#emojiFlag-prop)
- [\[read-only\] name : QString](#name-prop)
- [\[read-only\] subdivisions : QList\<KCountrySubdivision\>](#subdivisions-prop)
- [\[read-only\] timeZoneIds : QStringList](#timeZoneIds-prop)

## Public Functions

- [KCountry()](#KCountry)
- [QString alpha2() const](#alpha2)
- [QString alpha3() const](#alpha3)
- [QLocale::Country country() const](#country)
- [QString currencyCode() const](#currencyCode)
- [QString emojiFlag() const](#emojiFlag)
- [bool isValid() const](#isValid)
- [QString name() const](#name)
- [QList\<KCountrySubdivision\> subdivisions() const](#subdivisions)
- [QList\<const char \*\> timeZoneIds() const](#timeZoneIds)
- [bool KCountry::operator==(const KCountry &other) const](#operator-eq-eq)

## Static Public Members

- [QList\<KCountry\> allCountries()](#allCountries)
- [KCountry fromAlpha2(QStringView alpha2Code)](#fromAlpha2)
- [KCountry fromAlpha2(const char \*alpha2Code)](#fromAlpha2-1)
- [KCountry fromAlpha3(QStringView alpha3Code)](#fromAlpha3)
- [KCountry fromAlpha3(const char \*alpha3Code)](#fromAlpha3-1)
- [KCountry fromLocation(float latitude, float longitude)](#fromLocation)
- [KCountry fromName(QStringView name)](#fromName)
- [KCountry fromQLocale(QLocale::Country country)](#fromQLocale)

## Detailed Description {#details}

The information provided here are aggregated from the following sources:

- [iso-codes](https://salsa.debian.org/iso-codes-team/iso-codes/)
- [timezone-boundary-builder](https://github.com/evansiroky/timezone-boundary-builder/)
- [OSM](https://openstreetmap.org)
- [CLDR](http://cldr.unicode.org/)

> **Note:** This requires the iso-codes data files and translation catalogs to be available at runtime.

## Property Documentation {#property-documentation}

### \[read-only\] alpha2 : QString {#alpha2-prop}

**Access functions:**

- `QString` **[alpha2](kcountry.md#alpha2)**() const

### \[read-only\] alpha3 : QString {#alpha3-prop}

**Access functions:**

- `QString` **[alpha3](kcountry.md#alpha3)**() const

### \[read-only\] currencyCode : QString {#currencyCode-prop}

**Access functions:**

- `QString` **[currencyCode](kcountry.md#currencyCode)**() const

### \[read-only\] emojiFlag : QString {#emojiFlag-prop}

**Access functions:**

- `QString` **[emojiFlag](kcountry.md#emojiFlag)**() const

### \[read-only\] name : QString {#name-prop}

**Access functions:**

- `QString` **[name](kcountry.md#name)**() const

### \[read-only\] subdivisions : QList\<KCountrySubdivision\> {#subdivisions-prop}

**Access functions:**

- `QList`\<`KCountrySubdivision`\> **[subdivisions](kcountry.md#subdivisions)**() const

### \[read-only\] timeZoneIds : QStringList {#timeZoneIds-prop}

## Member Function Documentation {#member-function-documentation}

### KCountry::KCountry() {#KCountry}

Creates an invalid/empty [KCountry](kcountry.md) instance. See the fromX() methods for creating a valid instance.

### \[static\] QList\<KCountry\> KCountry::allCountries() {#allCountries}

List all countries.

### QString KCountry::alpha2() const {#alpha2}

ISO 3166-1 alpha 2 country code.

> **Note:** Getter function for property [alpha2](kcountry.md#alpha2-prop).

### QString KCountry::alpha3() const {#alpha3}

ISO 3166-1 alpha 3 country code.

> **Note:** Getter function for property [alpha3](kcountry.md#alpha3-prop).

### QLocale::Country KCountry::country() const {#country}

Returns the [QLocale::Country](https://doc.qt.io/qt-6/qlocale.html#Country-enum) value matching this country, or [QLocale::AnyCountry](https://doc.qt.io/qt-6/qlocale.html#Country-enum) if there is none.

### QString KCountry::currencyCode() const {#currencyCode}

Currency used in this country as ISO 4217 code.

> **Note:** Getter function for property [currencyCode](kcountry.md#currencyCode-prop).

### QString KCountry::emojiFlag() const {#emojiFlag}

Returns the Unicode flag emoji for this country.

> **Note:** Getter function for property [emojiFlag](kcountry.md#emojiFlag-prop).

### \[static\] KCountry KCountry::fromAlpha2(QStringView *alpha2Code*) {#fromAlpha2}

Create a [KCountry](kcountry.md) instance from an ISO 3166-1 alpha 2 code.

### \[static\] KCountry KCountry::fromAlpha2(const char \**alpha2Code*) {#fromAlpha2-1}

Create a [KCountry](kcountry.md) instance from an ISO 3166-1 alpha 2 code.

### \[static\] KCountry KCountry::fromAlpha3(QStringView *alpha3Code*) {#fromAlpha3}

Create a [KCountry](kcountry.md) instance from an ISO 3166-1 alpha 3 code.

### \[static\] KCountry KCountry::fromAlpha3(const char \**alpha3Code*) {#fromAlpha3-1}

Create a [KCountry](kcountry.md) instance from an ISO 3166-1 alpha 3 code.

### \[static\] KCountry KCountry::fromLocation(float *latitude*, float *longitude*) {#fromLocation}

Looks up the country at the given geographic coordinate. This can return an invalid object if the country could not be determined. This can happen in a number of cases:

- on oceans
- in polar regions
- close to a land border
- in disputed territories

### \[static\] KCountry KCountry::fromName(QStringView *name*) {#fromName}

Attempts to identify the country from the given name. The name can be in any language.

### \[static\] KCountry KCountry::fromQLocale(QLocale::Country *country*) {#fromQLocale}

Returns a [KCountry](kcountry.md) instance matching the given [QLocale::Country](https://doc.qt.io/qt-6/qlocale.html#Country-enum) code.

### bool KCountry::isValid() const {#isValid}

Returns `false` if this is an empty/invalid/default constructed instance, `true` otherwise.

### QString KCountry::name() const {#name}

Translated country name.

> **Note:** Getter function for property [name](kcountry.md#name-prop).

### QList\<KCountrySubdivision\> KCountry::subdivisions() const {#subdivisions}

Highest level of ISO 3166-2 country subdivisions. If there is only one level of subdivisions this lists all of them, for countries with multiple levels, this only includes the top-level subdivisions (ie. those having no parent subdivision).

> **Note:** This can be empty.

> **Note:** Getter function for property [subdivisions](kcountry.md#subdivisions-prop).

### QList\<const char \*\> KCountry::timeZoneIds() const {#timeZoneIds}

Timezones in use in this country.

### bool KCountry::operator==(const KCountry &*other*) const {#operator-eq-eq}
