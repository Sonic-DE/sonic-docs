---
title: "KEMailSettings Class"
description: "Access to e-mail settings."
---

# KEMailSettings Class

Access to e-mail settings. [More...](#details)

- **Header:** `#include <KEMailSettings>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS Config)`  
  `target_link_libraries(mytarget PRIVATE KF6::ConfigCore)`

[List of all members, including inherited members](kemailsettings-members.md)

## Public Types

- [enum KEMailSettings::Setting](#Setting-enum)

## Public Functions

- [KEMailSettings()](#KEMailSettings)
- [QString defaultProfileName() const](#defaultProfileName)
- [QString getSetting(KEMailSettings::Setting s) const](#getSetting)
- [QStringList profiles() const](#profiles)
- [void setDefault(const QString &def)](#setDefault)
- [void setProfile(const QString &s)](#setProfile)
- [void setSetting(KEMailSettings::Setting s, const QString &v)](#setSetting)

## Detailed Description {#details}

Facilitates accessing e-mail settings and allows any program to manage multiple e-mail profiles.

The default profile is automatically selected in the constructor.

## Member Type Documentation {#member-type-documentation}

### enum KEMailSettings::Setting {#Setting-enum}

| Constant |   |
| --- | --- |
| `KEMailSettings::ClientProgram` | `0` |
| `KEMailSettings::ClientTerminal` | `1` |
| `KEMailSettings::RealName` | `2` |
| `KEMailSettings::EmailAddress` | `3` |
| `KEMailSettings::ReplyToAddress` | `4` |
| `KEMailSettings::Organization` | `5` |

*See also* [getSetting](kemailsettings.md#getSetting)(), [setSetting](kemailsettings.md#setSetting)()

## Member Function Documentation {#member-function-documentation}

### KEMailSettings::KEMailSettings() {#KEMailSettings}

Constructs a new [KEMailSettings](kemailsettings.md) with the default profile.

### QString KEMailSettings::defaultProfileName() const {#defaultProfileName}

Returns the name of the default profile.

### QString KEMailSettings::getSetting(KEMailSettings::Setting *s*) const {#getSetting}

Returns a setting `s` from the predefined "basic" settings, or QString() if unset.

*See also* [Setting](kemailsettings.md#Setting-enum)

### QStringList KEMailSettings::profiles() const {#profiles}

Returns the list of profiles available.

### void KEMailSettings::setDefault(const QString &*def*) {#setDefault}

Sets a new default profile `def`.

### void KEMailSettings::setProfile(const QString &*s*) {#setProfile}

Sets the current profile to the new name `s`.

### void KEMailSettings::setSetting(KEMailSettings::Setting *s*, const QString &*v*) {#setSetting}

Sets the setting `s` from the predefined "basic" settings to the new value `v`.

*See also* [Setting](kemailsettings.md#Setting-enum)
