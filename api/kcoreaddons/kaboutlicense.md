---
title: "KAboutLicense Class"
description: "This class is used to store information about a license."
---

# KAboutLicense Class

This class is used to store information about a license. [More...](#details)

- **Header:** `#include <KAboutData>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS CoreAddons)`  
  `target_link_libraries(mytarget PRIVATE KF6::CoreAddons)`

[List of all members, including inherited members](kaboutlicense-members.md)

## Public Types

- [enum KAboutLicense::LicenseKey](#LicenseKey-enum)
- [\[since 6.0\] enum KAboutLicense::NameFormat](#NameFormat-enum)
- [\[since 6.0\] enum KAboutLicense::VersionRestriction](#VersionRestriction-enum)

## Properties

- [\[read-only\] key : const KAboutLicense::LicenseKey](#key-prop)
- [\[read-only\] name : const QString](#name-prop)
- [\[read-only\] spdx : const QString](#spdx-prop)
- [\[read-only\] text : const QString](#text-prop)

## Public Functions

- [KAboutLicense()](#KAboutLicense)
- [KAboutLicense(const KAboutLicense &other)](#KAboutLicense-1)
- [KAboutLicense::LicenseKey key() const](#key)
- [QString name(KAboutLicense::NameFormat formatName = ShortName) const](#name)
- [QString spdx() const](#spdx)
- [QString text() const](#text)

## Static Public Members

- [KAboutLicense byKeyword(const QString &keyword)](#byKeyword)

## Detailed Description {#details}

The license can be one of some predefined, one given as text or one that can be loaded from a file. This class is used in the [KAboutData](kaboutdata.md) class. Explicitly creating a [KAboutLicense](kaboutlicense.md) object is not possible. If the license is wanted for a KDE component having [KAboutData](kaboutdata.md) object, use [KAboutData::licenses](kaboutdata.md#licenses)() to get the licenses for that component. If the license is for a non-code resource and given by a keyword (e.g. in .desktop files), try using [KAboutLicense::byKeyword](kaboutlicense.md#byKeyword)().

## Member Type Documentation {#member-type-documentation}

### enum KAboutLicense::LicenseKey {#LicenseKey-enum}

Describes the license of the software; for more information see: https://spdx.org/licenses/

| Constant | Value | Description |
| --- | --- | --- |
| `KAboutLicense::Custom` | `-2` | Custom license |
| `KAboutLicense::File` | `-1` | License set from text file, see setLicenseFromPath() |
| `KAboutLicense::Unknown` | `0` | Unknown license |
| `KAboutLicense::GPL` | `1` | GPL |
| `KAboutLicense::GPL_V2` | `GPL` | GPL\_V2, this has the same value as LicenseKey::GPL, see https://spdx.org/licenses/GPL-2.0.html |
| `KAboutLicense::LGPL` | `2` | LGPL |
| `KAboutLicense::LGPL_V2` | `LGPL` | LGPL\_V2, this has the same value as LicenseKey::LGPL, see https://spdx.org/licenses/LGPL-2.0-only.html |
| `KAboutLicense::BSDL` | `3` | BSDL, see https://spdx.org/licenses/BSD-2-Clause.html. Deprecated, use BSD\_2\_Clause |
| `KAboutLicense::BSD_2_Clause` | `3` | = BSD\_2\_CLAUSE, see https://spdx.org/licenses/BSD-2-Clause.html |
| `KAboutLicense::Artistic` | `4` | Artistic, see https://spdx.org/licenses/Artistic-2.0.html |
| `KAboutLicense::GPL_V3` | `5` | GPL\_V3, see https://spdx.org/licenses/GPL-3.0.html |
| `KAboutLicense::LGPL_V3` | `6` | LGPL\_V3, see https://spdx.org/licenses/LGPL-3.0-only.html |
| `KAboutLicense::LGPL_V2_1 (since Qt 5.25)` | `7` | LGPL\_V2\_1, see https://spdx.org/licenses/LGPL-2.1-only.html |
| `KAboutLicense::MIT (since Qt 6.0)` | `8` | , see https://spdx.org/licenses/MIT.html |
| `KAboutLicense::ODbL_V1 (since Qt 6.9)` | `9` | ODbL\_V1, see https://spdx.org/licenses/ODbL-1.0.html |
| `KAboutLicense::Apache_V2 (since Qt 6.9)` | `10` | Apache\_V2, see https://spdx.org/licenses/Apache-2.0.html |
| `KAboutLicense::FTL (since Qt 6.9)` | `11` | FTL, see https://spdx.org/licenses/FTL.html |
| `KAboutLicense::BSL_V1 (since Qt 6.9)` | `12` | BSL\_V1, see https://spdx.org/licenses/BSL-1.0.html |
| `KAboutLicense::BSD_3_Clause (since Qt 6.9)` | `13` | BSD\_3\_CLAUSE, see https://spdx.org/licenses/BSD-3-Clause.html |
| `KAboutLicense::CC0_V1 (since Qt 6.9)` | `14` | CC0\_V1, see https://spdx.org/licenses/CC0-1.0.html |
| `KAboutLicense::MPL_V2 (since Qt 6.11)` | `15` | MPL\_V2, see https://spdx.org/licenses/MPL-2.0.html |

### \[since 6.0\] enum KAboutLicense::NameFormat {#NameFormat-enum}

Format of the license name.

| Constant | Value | Description |
| --- | --- | --- |
| `KAboutLicense::ShortName` | `0` | Short format |
| `KAboutLicense::FullName` | `1` | Full name |

This enum was introduced in Qt 6.0.

### \[since 6.0\] enum KAboutLicense::VersionRestriction {#VersionRestriction-enum}

Whether later versions of the license are allowed.

| Constant | Value | Description |
| --- | --- | --- |
| `KAboutLicense::OnlyThisVersion` | `0` | Only this version of the license is allowed |
| `KAboutLicense::OrLaterVersions` | `1` | Any later version of the license is allowed |

This enum was introduced in Qt 6.0.

## Property Documentation {#property-documentation}

### \[read-only\] key : const KAboutLicense::LicenseKey {#key-prop}

**Access functions:**

- `KAboutLicense::LicenseKey` **[key](kaboutlicense.md#key)**() const

### \[read-only\] name : const QString {#name-prop}

**Access functions:**

- `QString` **[name](kaboutlicense.md#name)**(`KAboutLicense::NameFormat` *formatName* = ShortName) const

### \[read-only\] spdx : const QString {#spdx-prop}

**Access functions:**

- `QString` **[spdx](kaboutlicense.md#spdx)**() const

### \[read-only\] text : const QString {#text-prop}

**Access functions:**

- `QString` **[text](kaboutlicense.md#text)**() const

## Member Function Documentation {#member-function-documentation}

### \[explicit\] KAboutLicense::KAboutLicense() {#KAboutLicense}

### KAboutLicense::KAboutLicense(const KAboutLicense &*other*) {#KAboutLicense-1}

Copy constructor. Performs a deep copy.

`other` object to copy

### \[static\] KAboutLicense KAboutLicense::byKeyword(const QString &*keyword*) {#byKeyword}

Fetch a known license by a keyword/spdx ID

Frequently the license data is provided by a terse keyword-like string, e.g. by a field in a .desktop file. Using this method, an application can get hold of a proper [KAboutLicense](kaboutlicense.md) object, providing that the license is one of the several known to KDE, and use it to present more human-readable information to the user.

Keywords are matched by stripping all whitespace and lowercasing. The known keywords correspond to the [KAboutLicense::LicenseKey](kaboutlicense.md#LicenseKey-enum) enumeration, e.g. any of "LGPLV3", "LGPLv3", "LGPL v3" would match [KAboutLicense::LGPL\_V3](kaboutlicense.md#LicenseKey-enum). If there is no match for the keyword, a valid license object is still returned, with its name and text informing about a custom license, and its key equal to [KAboutLicense::Custom](kaboutlicense.md#LicenseKey-enum).

`keyword` The license keyword.

Returns the license object.

*See also* [KAboutLicense::LicenseKey](kaboutlicense.md#LicenseKey-enum)

### KAboutLicense::LicenseKey KAboutLicense::key() const {#key}

Returns The license key as element of [KAboutLicense::LicenseKey](kaboutlicense.md#LicenseKey-enum) enum.

> **Note:** Getter function for property [key](kaboutlicense.md#key-prop).

### QString KAboutLicense::name(KAboutLicense::NameFormat *formatName* = ShortName) const {#name}

Returns the license name.

Default argument since 5.53

> **Note:** Getter function for property [name](kaboutlicense.md#name-prop).

### QString KAboutLicense::spdx() const {#spdx}

Returns the SPDX license expression of this license. If the underlying license cannot be expressed as a SPDX expression a null string is returned.

> **Note:** SPDX expression are expansive constructs. If you parse the return value, do it in a SPDX specification compliant manner by splitting on whitespaces to discard unwanted information or by using a complete SPDX license expression parser.

> **Note:** SPDX identifiers are case-insensitive. Do not use case-sensitive checks on the return value.

See [https://spdx.org/licenses](https://spdx.org/licenses) Returns SPDX license expression or QString() if the license has no identifier. Compliant with SPDX 2.1.

> **Note:** Getter function for property [spdx](kaboutlicense.md#spdx-prop).

### QString KAboutLicense::text() const {#text}

Returns the full license text. If the licenseType argument of the constructor has been used, any text defined by setLicenseText is ignored, and the standard text for the chosen license will be returned.

> **Note:** Getter function for property [text](kaboutlicense.md#text-prop).
