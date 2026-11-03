---
title: "KConfigBase Class"
description: "Interface to interact with configuration."
---

# KConfigBase Class

Interface to interact with configuration. [More...](#details)

- **Header:** `#include <KConfigBase>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS Config)`  
  `target_link_libraries(mytarget PRIVATE KF6::ConfigCore)`
- **Inherited By:** [KConfig](kconfig.md) and [KConfigGroup](kconfiggroup.md)

[List of all members, including inherited members](kconfigbase-members.md)

## Public Types

- [enum KConfigBase::AccessMode](#AccessMode-enum)
- [enum KConfigBase::WriteConfigFlag](#WriteConfigFlag-enum)

## Public Functions

- [KConfigBase::AccessMode accessMode() const](#accessMode)
- [void deleteGroup(const QString &group, KConfigBase::WriteConfigFlags flags = Normal)](#deleteGroup)
- [KConfigGroup group(const QString &group)](#group)
- [const KConfigGroup group(const QString &group) const](#group-1)
- [QStringList groupList() const](#groupList)
- [bool hasGroup(const QString &group) const](#hasGroup)
- [bool isGroupImmutable(const QString &group) const](#isGroupImmutable)
- [bool isImmutable() const](#isImmutable)
- [void markAsClean()](#markAsClean)
- [bool sync()](#sync)

## Detailed Description {#details}

[KConfigBase](kconfigbase.md) allows a component of an application to persists its configuration without the component knowing if it is storing the configuration into a top level [KConfig](kconfig.md) or a [KConfigGroup](kconfiggroup.md) inside a [KConfig](kconfig.md) instance.

## Member Type Documentation {#member-type-documentation}

### enum KConfigBase::AccessMode {#AccessMode-enum}

Possible return values for [accessMode](kconfigbase.md#accessMode)().

| Constant |   |
| --- | --- |
| `KConfigBase::NoAccess` | `0` |
| `KConfigBase::ReadOnly` | `1` |
| `KConfigBase::ReadWrite` | `2` |

### enum KConfigBase::WriteConfigFlag {#WriteConfigFlag-enum}

**flags KConfigBase::WriteConfigFlags**

Flags to control write entry

| Constant | Value | Description |
| --- | --- | --- |
| `KConfigBase::Persistent` | `0x01` | Save this entry when saving the config object. |
| `KConfigBase::Global` | `0x02` | Save the entry to the global KDE config file instead of the application specific config file. |
| `KConfigBase::Localized` | `0x04` | Add the locale tag to the key when writing it. |
| `KConfigBase::Notify (since Qt 5.51)` | `0x08 | Persistent` | Notifies remote KConfigWatchers of changes (requires DBus support). Implies Persistent. |
| `KConfigBase::Normal` | `Persistent` | Save the entry to the application specific config file without a locale tag. This is the default. |

The `WriteConfigFlags` type is a typedef for `QFlags<WriteConfigFlag>. `It stores an OR combination of `WriteConfigFlag` values.

*See also* [KConfigGroup](kconfiggroup.md), [KConfigWatcher](kconfigwatcher.md), [KConfigSkeletonItem::setWriteFlags](kconfigskeletonitem.md#setWriteFlags)()

## Member Function Documentation {#member-function-documentation}

### \[pure virtual\] KConfigBase::AccessMode KConfigBase::accessMode() const {#accessMode}

Returns the access mode of the app-config object.

Possible return values are [NoAccess](kconfigbase.md#AccessMode-enum) (the application-specific config file could not be opened neither read-write nor read-only), [ReadOnly](kconfigbase.md#AccessMode-enum) (the application-specific config file is opened read-only, but not read-write) and [ReadWrite](kconfigbase.md#AccessMode-enum) (the application-specific config file is opened read-write).

### void KConfigBase::deleteGroup(const QString &*group*, KConfigBase::WriteConfigFlags *flags* = Normal) {#deleteGroup}

Delete `group`.

This marks `group` as deleted in the config object. This effectively removes any cascaded values from config files earlier in the stack.

### KConfigGroup KConfigBase::group(const QString &*group*) {#group}

Returns an object for the named subgroup.

`group` the group to open. Pass an empty string here to the [KConfig](kconfig.md) object to obtain a handle on the root group. Returns config group object for the given group name.

### const KConfigGroup KConfigBase::group(const QString &*group*) const {#group-1}

Const overload for group(const [QString](https://doc.qt.io/qt-6/qstring.html)&)

This is an overloaded function.

### \[pure virtual\] QStringList KConfigBase::groupList() const {#groupList}

Returns a list of groups that are known about.

### bool KConfigBase::hasGroup(const QString &*group*) const {#hasGroup}

Returns `true` if the specified group is known about.

`group` name of group to search for

### bool KConfigBase::isGroupImmutable(const QString &*group*) const {#isGroupImmutable}

Can changes be made to the entries in `group`?

`group` The group to check for immutability.

Returns `false` if the entries in `group` can be modified, otherwise `true`

### \[pure virtual\] bool KConfigBase::isImmutable() const {#isImmutable}

Checks whether this configuration object can be modified.

### \[pure virtual\] void KConfigBase::markAsClean() {#markAsClean}

Reset the dirty flags of all entries in the entry map, so the values will not be written to disk on a later call to [sync](kconfigbase.md#sync)().

### \[pure virtual\] bool KConfigBase::sync() {#sync}

Syncs the configuration object that this group belongs to.

Unrelated concurrent changes to the same file are merged and thus not overwritten. Note however, that this object is not automatically updated with those changes.
