---
title: "KNotifyConfig Class"
description: "Represent the configuration for an event."
---

# KNotifyConfig Class

Represent the configuration for an event. [More...](#details)

- **Header:** `#include <KNotifyConfig>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS Notifications)`  
  `target_link_libraries(mytarget PRIVATE KF6::Notifications)`

[List of all members, including inherited members](knotifyconfig-members.md)

## Public Types

- [\[since 6.30\] enum KNotifyConfig::Action](#Action-enum)

## Public Functions

- [KNotifyConfig(const QString &applicationName, const QString &eventId)](#KNotifyConfig)
- [KNotifyConfig::Actions actions() const](#actions) (since 6.30)
- [QString applicationName() const](#applicationName)
- [QString eventId() const](#eventId)
- [bool isValid() const](#isValid)
- [QString readEntry(const QString &key) const](#readEntry)
- [QString readGlobalEntry(const QString &key) const](#readGlobalEntry)
- [QString readPathEntry(const QString &key) const](#readPathEntry)

## Static Public Members

- [void reparseConfiguration()](#reparseConfiguration)
- [void reparseSingleConfiguration(const QString &app)](#reparseSingleConfiguration)

## Detailed Description {#details}

## Member Type Documentation {#member-type-documentation}

### \[since 6.30\] enum KNotifyConfig::Action {#Action-enum}

**flags KNotifyConfig::Actions**

| Constant | Value | Description |
| --- | --- | --- |
| `KNotifyConfig::Popup` | `0x1` | Show a popup |
| `KNotifyConfig::Sound` | `0x2` | Play a sound |

This enum was introduced in Qt 6.30.

The `Actions` type is a typedef for `QFlags<Action>. `It stores an OR combination of `Action` values.

## Member Function Documentation {#member-function-documentation}

### KNotifyConfig::KNotifyConfig(const QString &*applicationName*, const QString &*eventId*) {#KNotifyConfig}

Creates a notify config for the given application name and event id

`applicationName` The application name, typically the name of the notifyrc file without its extension.

`eventId` The notification event ID, i.e. the part after Event/ in its notifyrc file.

### \[since 6.30\] KNotifyConfig::Actions KNotifyConfig::actions() const {#actions}

The actions for this notification.

This function was introduced in Qt 6.30.

### QString KNotifyConfig::applicationName() const {#applicationName}

the name of the application that triggered the notification

### QString KNotifyConfig::eventId() const {#eventId}

the name of the notification

### bool KNotifyConfig::isValid() const {#isValid}

Whether there exists an event with the given id under the given application name.

### QString KNotifyConfig::readEntry(const QString &*key*) const {#readEntry}

Returns entry from the relevant Event/ notifyrc config group

This will return the configuration from the user for the given key. It first look into the user config file, and then in the global config file.

Returns a null string if the entry doesn't exist

### QString KNotifyConfig::readGlobalEntry(const QString &*key*) const {#readGlobalEntry}

Returns entry from the relevant Global notifyrc config group

This will return the configuration from the user for the given key. It first look into the user config file, and then in the global config file.

Returns a null string if the entry doesn't exist

### QString KNotifyConfig::readPathEntry(const QString &*key*) const {#readPathEntry}

Returns path entry from the relevant Event/ notifyrc config group

This will return the configuration from the user for the given key and interpret it as a path.

### \[static\] void KNotifyConfig::reparseConfiguration() {#reparseConfiguration}

reparse the cached configs. to be used when the config may have changed

### \[static\] void KNotifyConfig::reparseSingleConfiguration(const QString &*app*) {#reparseSingleConfiguration}
