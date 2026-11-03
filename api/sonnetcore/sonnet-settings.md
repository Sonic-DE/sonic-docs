---
title: "Sonnet::Settings Class"
description: "Spelling framework for Qt."
---

# Sonnet::Settings Class

Spelling framework for Qt. [More...](#details)

- **Header:** `#include <Sonnet/Settings>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS Sonnet)`  
  `target_link_libraries(mytarget PRIVATE KF6::SonnetCore)`
- **Inherits:** [QObject](https://doc.qt.io/qt-6/qobject.html)

[List of all members, including inherited members](sonnet-settings-members.md)  
[Deprecated members](sonnet-settings-obsolete.md)

## Public Types

- [enum Settings::DictionaryRoles](#DictionaryRoles-enum)

## Properties

- [autodetectLanguage : bool](#autodetectLanguage-prop)
- [backgroundCheckerEnabled : bool](#backgroundCheckerEnabled-prop)
- [checkerEnabledByDefault : bool](#checkerEnabledByDefault-prop)
- [currentIgnoreList : QStringList](#currentIgnoreList-prop)
- [\[read-only\] defaultAutodetectLanguage : const bool](#defaultAutodetectLanguage-prop)
- [\[read-only\] defaultBackgroundCheckerEnabled : const bool](#defaultBackgroundCheckerEnabled-prop)
- [\[read-only\] defaultCheckerEnabledByDefault : const bool](#defaultCheckerEnabledByDefault-prop)
- [\[read-only\] defaultDefaultLanguage : const QString](#defaultDefaultLanguage-prop)
- [\[read-only\] defaultIgnoreList : const QStringList](#defaultIgnoreList-prop)
- [defaultLanguage : QString](#defaultLanguage-prop)
- [\[read-only\] defaultPreferredLanguages : const QStringList](#defaultPreferredLanguages-prop)
- [\[read-only\] defaultSkipRunTogether : const bool](#defaultSkipRunTogether-prop)
- [\[read-only\] defaultSkipUppercase : const bool](#defaultSkipUppercase-prop)
- [\[read-only\] dictionaryModel : QAbstractListModel\* const](#dictionaryModel-prop)
- [\[read-only\] modified : bool](#modified-prop)
- [preferredLanguages : QStringList](#preferredLanguages-prop)
- [skipRunTogether : bool](#skipRunTogether-prop)
- [skipUppercase : bool](#skipUppercase-prop)

## Public Functions

- [Settings(QObject \*parent = nullptr)](#Settings)
- [void save()](#save)

## Detailed Description {#details}

## Member Type Documentation {#member-type-documentation}

### enum Settings::DictionaryRoles {#DictionaryRoles-enum}

Roles for [dictionaryModel](sonnet-settings.md#dictionaryModel-prop)

| Constant | Value | Description |
| --- | --- | --- |
| `Sonnet::Settings::LanguageCodeRole` | `Qt::UserRole + 1` | Language code of the language. This uses "languageCode" as roleNames. |
| `Sonnet::Settings::PreferredRole` | `258` | This role holds whether the language is one of the preferred languages. This uses "isPreferred" as roleNames. |
| `Sonnet::Settings::DefaultRole` | `259` | This role holds whether the language is the default language. This uses "isDefault" as roleNames. |

## Property Documentation {#property-documentation}

### autodetectLanguage : bool {#autodetectLanguage-prop}

This property holds whether Sonnet should autodetect language.

**Access functions:**

- `bool` **autodetectLanguage**() const
- `void` **setAutodetectLanguage**(*bool*)

**Notifier signal:**

- `void` **autodetectLanguageChanged**()

### backgroundCheckerEnabled : bool {#backgroundCheckerEnabled-prop}

This property holds whether Sonnet should run spellchecking checks in the background.

**Access functions:**

- `bool` **backgroundCheckerEnabled**() const
- `void` **setBackgroundCheckerEnabled**(*bool*)

**Notifier signal:**

- `void` **backgroundCheckerEnabledChanged**()

### checkerEnabledByDefault : bool {#checkerEnabledByDefault-prop}

This property holds whether Sonnet should be enabled by default.

**Access functions:**

- `bool` **checkerEnabledByDefault**() const
- `void` **setCheckerEnabledByDefault**(*bool*)

**Notifier signal:**

- `void` **checkerEnabledByDefaultChanged**()

### currentIgnoreList : QStringList {#currentIgnoreList-prop}

This property holds the list of ignored words.

**Access functions:**

- `QStringList` **currentIgnoreList**() const
- `void` **setCurrentIgnoreList**(const `QStringList` &*ignores*)

**Notifier signal:**

- `void` **currentIgnoreListChanged**()

### \[read-only\] defaultAutodetectLanguage : const bool {#defaultAutodetectLanguage-prop}

This property holds the default value for the autoDetectLanguage property.

**Access functions:**

- `bool` **defaultAutodetectLanguage**()

### \[read-only\] defaultBackgroundCheckerEnabled : const bool {#defaultBackgroundCheckerEnabled-prop}

This property holds the default value for the [backgroundCheckerEnabled](sonnet-settings.md#backgroundCheckerEnabled-prop) property.

**Access functions:**

- `bool` **defaultBackgroundCheckerEnabled**()

### \[read-only\] defaultCheckerEnabledByDefault : const bool {#defaultCheckerEnabledByDefault-prop}

This property holds the default value for the list [checkerEnabledByDefault](sonnet-settings.md#checkerEnabledByDefault-prop) property.

**Access functions:**

- `bool` **defaultCheckerEnabledByDefault**()

### \[read-only\] defaultDefaultLanguage : const QString {#defaultDefaultLanguage-prop}

This property holds the default value for the [defaultLanguage](sonnet-settings.md#defaultLanguage-prop) property.

**Access functions:**

- `QString` **defaultDefaultLanguage**()

### \[read-only\] defaultIgnoreList : const QStringList {#defaultIgnoreList-prop}

This property holds the default value for the [currentIgnoreList](sonnet-settings.md#currentIgnoreList-prop) property.

**Access functions:**

- `QStringList` **defaultIgnoreList**()

### defaultLanguage : QString {#defaultLanguage-prop}

This property holds the default language for spell checking.

**Access functions:**

- `QString` **defaultLanguage**() const
- `void` **setDefaultLanguage**(const `QString` &*lang*)

**Notifier signal:**

- `void` **defaultLanguageChanged**()

### \[read-only\] defaultPreferredLanguages : const QStringList {#defaultPreferredLanguages-prop}

This property holds the default value for the [preferredLanguages](sonnet-settings.md#preferredLanguages-prop) property.

**Access functions:**

- `QStringList` **defaultPreferredLanguages**()

### \[read-only\] defaultSkipRunTogether : const bool {#defaultSkipRunTogether-prop}

This property holds the default value for the [skipRunTogether](sonnet-settings.md#skipRunTogether-prop) property.

**Access functions:**

- `bool` **defaultSkipRunTogether**()

### \[read-only\] defaultSkipUppercase : const bool {#defaultSkipUppercase-prop}

This property holds the default value for the [skipUppercase](sonnet-settings.md#skipUppercase-prop) property.

**Access functions:**

- `bool` **defaultSkipUppercase**()

### \[read-only\] dictionaryModel : QAbstractListModel\* const {#dictionaryModel-prop}

This property holds a Qt Model containing all the preferred dictionaries with language description and theirs codes. This model makes the [Qt::DisplayRole](https://doc.qt.io/qt-6/qt.html#ItemDataRole-enum) as well as the roles defined in [DictionaryRoles](sonnet-settings.md#DictionaryRoles-enum) available.

**Access functions:**

- `QAbstractListModel` \***dictionaryModel**()

### \[read-only\] modified : bool {#modified-prop}

**Access functions:**

- `bool` **modified**() const

**Notifier signal:**

- `void` **modifiedChanged**()

### preferredLanguages : QStringList {#preferredLanguages-prop}

This property holds the list of preferred languages.

**Access functions:**

- `QStringList` **preferredLanguages**() const
- `void` **setPreferredLanguages**(const `QStringList` &*lang*)

**Notifier signal:**

- `void` **preferredLanguagesChanged**()

### skipRunTogether : bool {#skipRunTogether-prop}

This property holds whether Sonnet should skip checking compounds words.

**Access functions:**

- `bool` **skipRunTogether**() const
- `void` **setSkipRunTogether**(*bool*)

**Notifier signal:**

- `void` **skipRunTogetherChanged**()

### skipUppercase : bool {#skipUppercase-prop}

This property holds whether Sonnet should skip checkign words starting with an uppercase letter.

**Access functions:**

- `bool` **skipUppercase**() const
- `void` **setSkipUppercase**(*bool*)

**Notifier signal:**

- `void` **skipUppercaseChanged**()

## Member Function Documentation {#member-function-documentation}

### \[explicit\] Settings::Settings(QObject \**parent* = nullptr) {#Settings}

### \[invokable\] void Settings::save() {#save}

> **Note:** This function can be invoked via the meta-object system and from QML. See Q\_INVOKABLE.
