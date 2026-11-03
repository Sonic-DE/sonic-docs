---
title: "KFormat Class"
description: "Class for formatting numbers and datetimes."
---

# KFormat Class

Class for formatting numbers and datetimes. [More...](#details)

- **Header:** `#include <KFormat>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS CoreAddons)`  
  `target_link_libraries(mytarget PRIVATE KF6::CoreAddons)`

[List of all members, including inherited members](kformat-members.md)

## Public Types

- [enum KFormat::BinarySizeUnits](#BinarySizeUnits-enum)
- [enum KFormat::BinaryUnitDialect](#BinaryUnitDialect-enum)
- [\[since 6.11\] enum KFormat::DistanceFormatOption](#DistanceFormatOption-enum)
- [enum KFormat::DurationFormatOption](#DurationFormatOption-enum)
- [\[since 6.15\] enum KFormat::TimeFormatOption](#TimeFormatOption-enum)
- [enum KFormat::Unit](#Unit-enum)
- [enum KFormat::UnitPrefix](#UnitPrefix-enum)

## Public Functions

- [KFormat(const QLocale &locale = QLocale())](#KFormat)
- [QString formatByteSize(double size, int precision = 1, KFormat::BinaryUnitDialect dialect = KFormat::DefaultBinaryDialect, KFormat::BinarySizeUnits units = KFormat::DefaultBinaryUnits) const](#formatByteSize)
- [QString formatDateTime(const QDateTime &dateTime, QLocale::FormatType format, KFormat::TimeFormatOptions options = KFormat::DoNotAddTimeZone) const](#formatDateTime) (since 6.31)
- [QString formatDecimalDuration(quint64 msecs, int decimalPlaces = 2) const](#formatDecimalDuration)
- [QString formatDistance(double distance, KFormat::DistanceFormatOptions = LocaleDistanceUnits) const](#formatDistance) (since 6.11)
- [QString formatDuration(quint64 msecs, KFormat::DurationFormatOptions options = KFormat::DefaultDuration) const](#formatDuration)
- [QString formatRelativeDate(const QDate &date, QLocale::FormatType format) const](#formatRelativeDate)
- [QString formatRelativeDateTime(const QDateTime &dateTime, QLocale::FormatType format) const](#formatRelativeDateTime)
- [QString formatSpelloutDuration(quint64 msecs) const](#formatSpelloutDuration)
- [QString formatTime(const QDateTime &dateTime, QLocale::FormatType format, KFormat::TimeFormatOptions options = KFormat::DoNotAddTimeZone) const](#formatTime) (since 6.15)
- [QString formatValue(double value, KFormat::Unit unit, int precision = 1, KFormat::UnitPrefix prefix = KFormat::UnitPrefix::AutoAdjust, KFormat::BinaryUnitDialect dialect = KFormat::DefaultBinaryDialect) const](#formatValue)
- [QString formatValue(double value, const QString &unit, int precision, KFormat::UnitPrefix prefix, KFormat::BinaryUnitDialect dialect) const](#formatValue-1)

## Detailed Description {#details}

[KFormat](kformat.md) provides support for formatting numbers and datetimes in formats that are not supported by [QLocale](https://doc.qt.io/qt-6/qlocale.html).

## Member Type Documentation {#member-type-documentation}

### enum KFormat::BinarySizeUnits {#BinarySizeUnits-enum}

These binary units are used in KDE by the [formatByteSize](kformat.md#formatByteSize)() function.

NOTE: There are several different units standards: 1) SI (i.e. metric), powers-of-10. 2) IEC, powers-of-2, with specific units KiB, MiB, etc. 3) JEDEC, powers-of-2, used for solid state memory sizing which is why you see flash cards labels as e.g. 4GB. These (ab)use the metric units. Although JEDEC only defines KB, MB, GB, if JEDEC is selected all units will be powers-of-2 with metric prefixes for clarity in the event of sizes larger than 1024 GB.

Although 3 different dialects are possible this enum only uses metric names since adding all 3 different names of essentially the same unit would be pointless. Use [BinaryUnitDialect](kformat.md#BinaryUnitDialect-enum) to control the exact units returned.

| Constant | Value | Description |
| --- | --- | --- |
| `KFormat::DefaultBinaryUnits` | `-1` | Auto-choose a unit such that the result is in the range \[0, 1000 or 1024) |
| `KFormat::UnitByte` | `0` | B 1 byte |
| `KFormat::UnitKiloByte` | `1` | KiB/KB/kB 1024/1000 bytes |
| `KFormat::UnitMegaByte` | `2` | MiB/MB/MB 2^20/10^06 bytes |
| `KFormat::UnitGigaByte` | `3` | GiB/GB/GB 2^30/10^09 bytes |
| `KFormat::UnitTeraByte` | `4` | TiB/TB/TB 2^40/10^12 bytes |
| `KFormat::UnitPetaByte` | `5` | PiB/PB/PB 2^50/10^15 bytes |
| `KFormat::UnitExaByte` | `6` | EiB/EB/EB 2^60/10^18 bytes |
| `KFormat::UnitZettaByte` | `7` | ZiB/ZB/ZB 2^70/10^21 bytes |
| `KFormat::UnitYottaByte` | `8` | YiB/YB/YB 2^80/10^24 bytes |

*See also* [BinaryUnitDialect](kformat.md#BinaryUnitDialect-enum), [formatByteSize](kformat.md#formatByteSize)

### enum KFormat::BinaryUnitDialect {#BinaryUnitDialect-enum}

This enum chooses what dialect is used for binary units.

Note: Although JEDEC abuses the metric prefixes and can therefore be confusing, it has been used to describe \*memory\* sizes for quite some time and programs should therefore use either Default, JEDEC, or IEC 60027-2 for memory sizes.

On the other hand network transmission rates are typically in metric so Default, Metric, or IEC (which is unambiguous) should be chosen.

Normally choosing DefaultBinaryDialect is the best option as that uses the user's selection for units. If the user has not selected a preference, IECBinaryDialect will typically be used.

| Constant | Value | Description |
| --- | --- | --- |
| `KFormat::DefaultBinaryDialect` | `-1` | Used if no specific preference |
| `KFormat::IECBinaryDialect` | `0` | KiB, MiB, etc. 2^(10\*n) |
| `KFormat::JEDECBinaryDialect` | `1` | KB, MB, etc. 2^(10\*n) |
| `KFormat::MetricBinaryDialect` | `2` | SI Units, kB, MB, etc. 10^(3\*n) |

*See also* [BinarySizeUnits](kformat.md#BinarySizeUnits-enum), [formatByteSize](kformat.md#formatByteSize)

### \[since 6.11\] enum KFormat::DistanceFormatOption {#DistanceFormatOption-enum}

**flags KFormat::DistanceFormatOptions**

Formatting options for [formatDistance](kformat.md#formatDistance)()

| Constant | Value | Description |
| --- | --- | --- |
| `KFormat::LocaleDistanceUnits` | `0x0` | Automatically select metric or imperial units based on the current locale |
| `KFormat::MetricDistanceUnits` | `0x1` | Force the use of metric unites regardless of the current locale |

This enum was introduced in Qt 6.11.

The `DistanceFormatOptions` type is a typedef for `QFlags<DistanceFormatOption>. `It stores an OR combination of `DistanceFormatOption` values.

### enum KFormat::DurationFormatOption {#DurationFormatOption-enum}

**flags KFormat::DurationFormatOptions**

Format flags for [formatDuration](kformat.md#formatDuration)()

| Constant | Value | Description |
| --- | --- | --- |
| `KFormat::DefaultDuration` | `0x0` | Default formatting in localized 1:23:45 format |
| `KFormat::InitialDuration` | `0x1` | Default formatting in localized 1h23m45s format |
| `KFormat::ShowMilliseconds` | `0x2` | Include milliseconds in format, e.g. 1:23:45.678 |
| `KFormat::HideSeconds` | `0x4` | Hide the seconds, e.g. 1:23 or 1h23m, overrides ShowMilliseconds |
| `KFormat::FoldHours` | `0x8` | Fold the hours into the minutes, e.g. 83:45 or 83m45s, overrides HideSeconds |
| `KFormat::AbbreviatedDuration (since Qt 6.11)` | `0x10` | Use abbreviated units (e.g. 1 hr 23 min), as a middle ground between just unit initials (InitialDuration) and fully spelled out units ([formatSpelloutDuration](kformat.md#formatSpelloutDuration)). This always includes up to 2 components. |

The `DurationFormatOptions` type is a typedef for `QFlags<DurationFormatOption>. `It stores an OR combination of `DurationFormatOption` values.

### \[since 6.15\] enum KFormat::TimeFormatOption {#TimeFormatOption-enum}

**flags KFormat::TimeFormatOptions**

Format flags for [formatTime](kformat.md#formatTime)()

| Constant | Value | Description |
| --- | --- | --- |
| `KFormat::DoNotAddTimeZone` | `0x0` | Equivalent to the [QLocale](https://doc.qt.io/qt-6/qlocale.html) time formatting, does not add any timezone information |
| `KFormat::AddTimezoneAbbreviation` | `0x1` | Adds the (translated) timezone abbreviation when timezone information is present, e.g. "12:23 CET" |
| `KFormat::AddTimezoneAbbreviationIfNeeded` | `0x2` | Adds the (translated) timezone abbreviation when timezone information is present and differs from the current local timezone. |

This enum was introduced in Qt 6.15.

The `TimeFormatOptions` type is a typedef for `QFlags<TimeFormatOption>. `It stores an OR combination of `TimeFormatOption` values.

### enum KFormat::Unit {#Unit-enum}

These units are used in KDE by the [formatValue](kformat.md#formatValue)() function.

| Constant | Value | Description |
| --- | --- | --- |
| `KFormat::Unit::Other` | `0` | other |
| `KFormat::Unit::Bit` | `1` | bit |
| `KFormat::Unit::Byte` | `2` | B |
| `KFormat::Unit::Meter` | `3` | m |
| `KFormat::Unit::Hertz` | `4` | Hz |

*See also* [formatValue](kformat.md#formatValue)

### enum KFormat::UnitPrefix {#UnitPrefix-enum}

These prefixes are used in KDE by the [formatValue](kformat.md#formatValue)() function.

IEC prefixes are only defined for integral units of information, e.g. bits and bytes.

| Constant | Value | Description |
| --- | --- | --- |
| `KFormat::UnitPrefix::AutoAdjust` | `-128` | Auto-choose a unit such that the result is in the range \[0, 1000 or 1024) |
| `KFormat::UnitPrefix::Yocto` | `0` | –/-/y 10^-24 |
| `KFormat::UnitPrefix::Zepto` | `1` | –/-/z 10^-21 |
| `KFormat::UnitPrefix::Atto` | `2` | –/-/a 10^-18 |
| `KFormat::UnitPrefix::Femto` | `3` | –/-/f 10^-15 |
| `KFormat::UnitPrefix::Pico` | `4` | –/-/p 10^-12 |
| `KFormat::UnitPrefix::Nano` | `5` | –/-/n 10^-9 |
| `KFormat::UnitPrefix::Micro` | `6` | –/-/µ 10^-6 |
| `KFormat::UnitPrefix::Milli` | `7` | –/-/m 10^-3 |
| `KFormat::UnitPrefix::Centi` | `8` | –/-/c 0.01 |
| `KFormat::UnitPrefix::Deci` | `9` | –/-/d 0.1 |
| `KFormat::UnitPrefix::Unity` | `10` | "" 1 |
| `KFormat::UnitPrefix::Deca` | `11` | –/-/da 10 |
| `KFormat::UnitPrefix::Hecto` | `12` | –/-/h 100 |
| `KFormat::UnitPrefix::Kilo` | `13` | Ki/K/k 1024/1000 |
| `KFormat::UnitPrefix::Mega` | `14` | Mi/M/M 2^20/10^06 |
| `KFormat::UnitPrefix::Giga` | `15` | Gi/G/G 2^30/10^09 |
| `KFormat::UnitPrefix::Tera` | `16` | Ti/T/T 2^40/10^12 |
| `KFormat::UnitPrefix::Peta` | `17` | Pi/P/P 2^50/10^15 |
| `KFormat::UnitPrefix::Exa` | `18` | Ei/E/E 2^60/10^18 |
| `KFormat::UnitPrefix::Zetta` | `19` | Zi/Z/Z 2^70/10^21 |
| `KFormat::UnitPrefix::Yotta` | `20` | Yi/Y/Y 2^80/10^24 |

*See also* [BinarySizeUnits](kformat.md#BinarySizeUnits-enum), [formatValue](kformat.md#formatValue)

## Member Function Documentation {#member-function-documentation}

### \[explicit\] KFormat::KFormat(const QLocale &*locale* = QLocale()) {#KFormat}

Constructs a [KFormat](kformat.md).

`locale` the locale to use, defaults to the system locale

### QString KFormat::formatByteSize(double *size*, int *precision* = 1, KFormat::BinaryUnitDialect *dialect* = KFormat::DefaultBinaryDialect, KFormat::BinarySizeUnits *units* = KFormat::DefaultBinaryUnits) const {#formatByteSize}

Converts `size` from bytes to the appropriate string representation using the binary unit dialect `dialect` and the specific units `units`.

Example:

```cpp
QString metric, iec, jedec, small;
metric = formatByteSize(1000, 1, KFormat::MetricBinaryDialect, KFormat::UnitKiloByte);
iec    = formatByteSize(1024, 1, KFormat::IECBinaryDialect, KFormat::UnitKiloByte);
jedec  = formatByteSize(1024, 1, KFormat::JEDECBinaryDialect, KFormat::UnitKiloByte);
small  = formatByteSize(100);
// metric == "1.0 kB", iec == "1.0 KiB", jedec == "1.0 KB", small == "100 B"
```

`size` size in bytes

`precision` number of places after the decimal point to use. KDE uses 1 by default so when in doubt use 1. Whenever [KFormat::UnitByte](kformat.md#BinarySizeUnits-enum) is used (either explicitly or autoselected from [KFormat::DefaultBinaryUnits](kformat.md#BinarySizeUnits-enum)), the fractional part is always omitted.

`dialect` binary unit standard to use. Use [DefaultBinaryDialect](kformat.md#BinaryUnitDialect-enum) to use the localized user selection unless you need to use a specific unit type (such as displaying a flash memory size in JEDEC).

`units` specific unit size to use in result. Use [DefaultBinaryUnits](kformat.md#BinarySizeUnits-enum) to automatically select a unit that will return a sanely-sized number.

Returns converted size as a translated string including the units. E.g. "1.23 KiB", "2 GB" (JEDEC), "4.2 kB" (Metric).

*See also* [BinarySizeUnits](kformat.md#BinarySizeUnits-enum), [BinaryUnitDialect](kformat.md#BinaryUnitDialect-enum)

### \[since 6.31\] QString KFormat::formatDateTime(const QDateTime &*dateTime*, QLocale::FormatType *format*, KFormat::TimeFormatOptions *options* = KFormat::DoNotAddTimeZone) const {#formatDateTime}

Returns a datetime value formatted as string considering the timezone.

This behaves like [QLocale::toString](https://doc.qt.io/qt-6/qlocale.html#toString)([QDateTime](https://doc.qt.io/qt-6/qdatetime.html), [QLocale::FormatType](https://doc.qt.io/qt-6/qlocale.html#FormatType-enum)) but can be made to add additional timezone information via `options`.

`dateTime` the datetime to be formatted. `format` the format used for formatting the time value `options` controls how timezone information should be formatted

This function was introduced in Qt 6.31.

### QString KFormat::formatDecimalDuration(quint64 *msecs*, int *decimalPlaces* = 2) const {#formatDecimalDuration}

Given a number of milliseconds, converts that to a string containing the localized equivalent to the requested decimal places.

e.g. given [formatDuration](kformat.md#formatDuration)(60000), returns "1.0 minutes"

`msecs` Time duration in milliseconds

`decimalPlaces` Decimal places to round off to, defaults to 2

Returns converted duration as a string - e.g. "5.5 seconds" "23.0 minutes"

### \[since 6.11\] QString KFormat::formatDistance(double *distance*, *KFormat::DistanceFormatOptions* = LocaleDistanceUnits) const {#formatDistance}

Format `distance` given in meters in a suitable unit for displaying.

For locales using metric units (or when forcing metric units explicitly) this will use meters and kilometers depending on the distance, for locales using imperial units this wil use miles and feet.

`distance` Distance value to be formatted, in meters.

`options` Formatting options.

Returns Formatted distance using locale- and distance-appropirate units.

This function was introduced in Qt 6.11.

### QString KFormat::formatDuration(quint64 *msecs*, KFormat::DurationFormatOptions *options* = KFormat::DefaultDuration) const {#formatDuration}

Given a number of milliseconds, converts that to a string containing the localized equivalent, e.g. 1:23:45

`msecs` Time duration in milliseconds

`options` options to use in the duration format

Returns converted duration as a string - e.g. "1:23:45" "1h23m"

### QString KFormat::formatRelativeDate(const QDate &*date*, QLocale::FormatType *format*) const {#formatRelativeDate}

Returns a string formatted to a relative date style.

If the `date` falls within 2 days before or after the current date then a relative date string will be returned, such as:

- Yesterday
- Today
- Tomorrow
- Two days ago
- In two days

If the `date` falls outside this period then the `format` is used.

`date` the date to be formatted

`format` the date format to use

Returns the date as a string

### QString KFormat::formatRelativeDateTime(const QDateTime &*dateTime*, QLocale::FormatType *format*) const {#formatRelativeDateTime}

Returns a string formatted to a relative datetime style.

If the `dateTime` falls within 2 days before or after the current date then a relative date string will be returned, such as:

- Yesterday at 3:00pm
- Today at 3:00pm
- Tomorrow at 3:00pm
- Two days ago at 3:00pm
- In Two days at 3:00pm

If the `dateTime` falls within one hour of the current time. Then a shorter version is displayed:

- Just a moment ago (for within the same minute)
- 15 minutes ago

If the `dateTime` falls outside this period then the date is rendered as:

- Monday, 7 September, 2021 at 7:00 PM : date formatted `format` + " at " + time formatted with `format`

With `format` LongFormat, time format used is set to ShortFormat (to omit timezone and seconds).

First character is capitalized.

`dateTime` the date to be formatted

`format` the date format to use

Returns the date as a string

### QString KFormat::formatSpelloutDuration(quint64 *msecs*) const {#formatSpelloutDuration}

Given a number of milliseconds, converts that to a spell-out string containing the localized equivalent.

e.g. given formatSpelloutDuration(60001) returns "1 minute" given formatSpelloutDuration(62005) returns "1 minute and 2 seconds" given formatSpelloutDuration(90060000) returns "1 day and 1 hour"

`msecs` Time duration in milliseconds

Returns converted duration as a string. Units not interesting to the user, for example seconds or minutes when the first unit is day, are not returned because they are irrelevant. The same applies for seconds when the first unit is hour.

### \[since 6.15\] QString KFormat::formatTime(const QDateTime &*dateTime*, QLocale::FormatType *format*, KFormat::TimeFormatOptions *options* = KFormat::DoNotAddTimeZone) const {#formatTime}

Returns a time value formatted as string considering the timezone.

This behaves like [QLocale::toString](https://doc.qt.io/qt-6/qlocale.html#toString)([QTime](https://doc.qt.io/qt-6/qtime.html), [QLocale::FormatType](https://doc.qt.io/qt-6/qlocale.html#FormatType-enum)) but can be made to add additional timezone information via `options`.

`dateTime` the time to be formatted, as a full [QDateTime](https://doc.qt.io/qt-6/qdatetime.html) object so timezone informations remain available. `format` the format used for formatting the time value `options` controls how timezone information should be formatted

This function was introduced in Qt 6.15.

### QString KFormat::formatValue(double *value*, KFormat::Unit *unit*, int *precision* = 1, KFormat::UnitPrefix *prefix* = KFormat::UnitPrefix::AutoAdjust, KFormat::BinaryUnitDialect *dialect* = KFormat::DefaultBinaryDialect) const {#formatValue}

Converts `value` to the appropriate string representation

Example:

```cpp
// sets formatted to "1.0 kbit"
auto formatted = format.formatValue(1000, KFormat::Unit::Bit, 1, KFormat::UnitPrefix::Kilo);
```

`value` value to be formatted

`precision` number of places after the decimal point to use. KDE uses 1 by default so when in doubt use 1.

`unit` unit to use in result.

`prefix` specific prefix to use in result. Use [UnitPrefix::AutoAdjust](kformat.md#UnitPrefix-enum) to automatically select an appropriate prefix.

`dialect` prefix standard to use. Use [DefaultBinaryDialect](kformat.md#BinaryUnitDialect-enum) to use the localized user selection unless you need to use a specific unit type. Only meaningful for [KFormat::Unit::Byte](kformat.md#Unit-enum), and ignored for all other units.

Returns converted size as a translated string including prefix and unit. E.g. "1.23 KiB", "2 GB" (JEDEC), "4.2 kB" (Metric), "1.2 kbit".

*See also* [Unit](kformat.md#Unit-enum), [UnitPrefix](kformat.md#UnitPrefix-enum), [BinaryUnitDialect](kformat.md#BinaryUnitDialect-enum)

### QString KFormat::formatValue(double *value*, const QString &*unit*, int *precision*, KFormat::UnitPrefix *prefix*, KFormat::BinaryUnitDialect *dialect*) const {#formatValue-1}

Converts `value` to the appropriate string representation.

Example:

```cpp
QString iec, jedec, metric;
// Sets iec to "1.0 KiB/s", jedec to "1.0 KB/s" and metric to "1.0 kB/s"
iec = format.formatValue(1024, QStringLiteral("B/s"), 1, KFormat::UnitPrefix::AutoAdjust, KFormat::IECBinaryDialect);
jedec = format.formatValue(1024, QStringLiteral("B/s"), 1, KFormat::UnitPrefix::AutoAdjust, KFormat::JEDECBinaryDialect);
metric = format.formatValue(1000, QStringLiteral("B/s"), 1, KFormat::UnitPrefix::AutoAdjust, KFormat::MetricBinaryDialect);
```

`value` value to be formatted

`precision` number of places after the decimal point to use. 1 is used by default; when in doubt use 1

`unit` unit to use in result

`prefix` specific prefix to use in result. Use [UnitPrefix::AutoAdjust](kformat.md#UnitPrefix-enum) to automatically select an appropriate prefix

`dialect` prefix standard to use. Use [DefaultBinaryDialect](kformat.md#BinaryUnitDialect-enum) to use the localized user selection unless you need to use a specific unit type

Returns converted size as a translated string including prefix and unit. E.g. "1.2 kbit", "2.4 kB", "12.3 Mbit/s"

*See also* [UnitPrefix](kformat.md#UnitPrefix-enum)
