---
title: "KConfigGroup Class"
description: "A class for one specific group in a KConfig object."
---

# KConfigGroup Class

A class for one specific group in a [KConfig](kconfig.md) object. [More...](#details)

- **Header:** `#include <KConfigGroup>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS Config)`  
  `target_link_libraries(mytarget PRIVATE KF6::ConfigCore)`
- **Inherits:** [KConfigBase](kconfigbase.md)

[List of all members, including inherited members](kconfiggroup-members.md)

## Public Functions

- [KConfigGroup()](#KConfigGroup)
- [KConfigGroup(KConfigBase \*master, const QString &group)](#KConfigGroup-1)
- [KConfigGroup(const KConfigBase \*master, const QString &group)](#KConfigGroup-2)
- [KConfigGroup(const QExplicitlySharedDataPointer\<KSharedConfig\> &master, const QString &group)](#KConfigGroup-3)
- [KConfig \*config()](#config)
- [const KConfig \*config() const](#config-1)
- [void copyTo(KConfigBase \*other, KConfigBase::WriteConfigFlags pFlags = Normal) const](#copyTo)
- [void deleteEntry(const QString &pKey, KConfigBase::WriteConfigFlags pFlags = Normal)](#deleteEntry)
- [void deleteEntry(const char \*key, KConfigBase::WriteConfigFlags pFlags = Normal)](#deleteEntry-1)
- [void deleteGroup(KConfigBase::WriteConfigFlags pFlags = Normal)](#deleteGroup)
- [QMap\<QString, QString\> entryMap() const](#entryMap)
- [bool exists() const](#exists)
- [bool hasDefault(const QString &key) const](#hasDefault)
- [bool hasDefault(const char \*key) const](#hasDefault-1)
- [bool hasKey(const QString &key) const](#hasKey)
- [bool hasKey(const char \*key) const](#hasKey-1)
- [bool isEntryImmutable(const QString &key) const](#isEntryImmutable)
- [bool isEntryImmutable(const char \*key) const](#isEntryImmutable-1)
- [bool isImmutable() const](#isImmutable)
- [bool isValid() const](#isValid)
- [QStringList keyList() const](#keyList)
- [void moveValuesTo(KConfigGroup &other, KConfigBase::WriteConfigFlags pFlags = Normal)](#moveValuesTo) (since 6.3)
- [void moveValuesTo(const QList\<const char \*\> &keys, KConfigGroup &other, KConfigBase::WriteConfigFlags pFlags = Normal)](#moveValuesTo-1)
- [QString name() const](#name)
- [KConfigGroup parent() const](#parent)
- [template \<typename T\> QList\<T\> readEntry(const QString &key, const QList\<T\> &aDefault) const](#readEntry)
- [QString readEntry(const QString &key, const QString &aDefault) const](#readEntry-1)
- [QStringList readEntry(const QString &key, const QStringList &aDefault) const](#readEntry-2)
- [QVariant readEntry(const QString &key, const QVariant &aDefault) const](#readEntry-3)
- [template \<typename T\> T readEntry(const QString &key, const T &aDefault) const](#readEntry-4)
- [template \<typename Rep, typename Period\> std::chrono::duration\<Rep, Period\> readEntry(const QString &key, std::chrono::duration\<Rep, Period\> defaultValue) const](#readEntry-5) (since 6.22)
- [QVariantList readEntry(const QString &key, const QVariantList &aDefault) const](#readEntry-6)
- [QString readEntry(const QString &key, const char \*aDefault = nullptr) const](#readEntry-7)
- [template \<typename T\> QList\<T\> readEntry(const char \*key, const QList\<T\> &aDefault) const](#readEntry-8)
- [QString readEntry(const char \*key, const QString &aDefault) const](#readEntry-9)
- [QStringList readEntry(const char \*key, const QStringList &aDefault) const](#readEntry-10)
- [QVariant readEntry(const char \*key, const QVariant &aDefault) const](#readEntry-11)
- [QVariantList readEntry(const char \*key, const QVariantList &aDefault) const](#readEntry-12)
- [template \<typename T\> T readEntry(const char \*key, const T &aDefault) const](#readEntry-13)
- [QString readEntry(const char \*key, const char \*aDefault = nullptr) const](#readEntry-14)
- [template \<typename Rep, typename Period\> std::chrono::duration\<Rep, Period\> readEntry(const char \*key, std::chrono::duration\<Rep, Period\> defaultValue) const](#readEntry-15) (since 6.22)
- [QString readEntryUntranslated(const QString &pKey, const QString &aDefault = QString()) const](#readEntryUntranslated)
- [QString readEntryUntranslated(const char \*key, const QString &aDefault = QString()) const](#readEntryUntranslated-1)
- [QString readPathEntry(const QString &pKey, const QString &aDefault) const](#readPathEntry)
- [QStringList readPathEntry(const QString &pKey, const QStringList &aDefault) const](#readPathEntry-1)
- [QString readPathEntry(const char \*key, const QString &aDefault) const](#readPathEntry-2)
- [QStringList readPathEntry(const char \*key, const QStringList &aDefault) const](#readPathEntry-3)
- [QStringList readXdgListEntry(const QString &pKey, const QStringList &aDefault = QStringList()) const](#readXdgListEntry)
- [QStringList readXdgListEntry(const char \*key, const QStringList &aDefault = QStringList()) const](#readXdgListEntry-1)
- [void reparent(KConfigBase \*parent, KConfigBase::WriteConfigFlags pFlags = Normal)](#reparent)
- [void revertToDefault(const QString &key, KConfigBase::WriteConfigFlags pFlag = WriteConfigFlags())](#revertToDefault)
- [void revertToDefault(const char \*key, KConfigBase::WriteConfigFlags pFlag = WriteConfigFlags())](#revertToDefault-1)
- [void writeEntry(const QString &key, const QVariant &value, KConfigBase::WriteConfigFlags pFlags = Normal)](#writeEntry)
- [void writeEntry(const QString &key, const QByteArray &value, KConfigBase::WriteConfigFlags pFlags = Normal)](#writeEntry-1)
- [template \<typename T\> void writeEntry(const QString &key, const QList\<T\> &value, KConfigBase::WriteConfigFlags pFlags = Normal)](#writeEntry-2)
- [void writeEntry(const QString &key, const QString &value, KConfigBase::WriteConfigFlags pFlags = Normal)](#writeEntry-3)
- [void writeEntry(const QString &key, const QStringList &value, KConfigBase::WriteConfigFlags pFlags = Normal)](#writeEntry-4)
- [void writeEntry(const QString &key, const QVariantList &value, KConfigBase::WriteConfigFlags pFlags = Normal)](#writeEntry-5)
- [template \<typename T\> void writeEntry(const QString &key, const T &value, KConfigBase::WriteConfigFlags pFlags = Normal)](#writeEntry-6)
- [void writeEntry(const QString &key, const char \*value, KConfigBase::WriteConfigFlags pFlags = Normal)](#writeEntry-7)
- [template \<typename Rep, typename Period\> void writeEntry(const QString &key, std::chrono::duration\<Rep, Period\> value, KConfigBase::WriteConfigFlags pFlags = Normal)](#writeEntry-8) (since 6.22)
- [void writeEntry(const char \*key, const QByteArray &value, KConfigBase::WriteConfigFlags pFlags = Normal)](#writeEntry-9)
- [template \<typename T\> void writeEntry(const char \*key, const QList\<T\> &value, KConfigBase::WriteConfigFlags pFlags = Normal)](#writeEntry-10)
- [void writeEntry(const char \*key, const QString &value, KConfigBase::WriteConfigFlags pFlags = Normal)](#writeEntry-11)
- [void writeEntry(const char \*key, const QStringList &value, KConfigBase::WriteConfigFlags pFlags = Normal)](#writeEntry-12)
- [void writeEntry(const char \*key, const QVariant &value, KConfigBase::WriteConfigFlags pFlags = Normal)](#writeEntry-13)
- [void writeEntry(const char \*key, const QVariantList &value, KConfigBase::WriteConfigFlags pFlags = Normal)](#writeEntry-14)
- [template \<typename T\> void writeEntry(const char \*key, const T &value, KConfigBase::WriteConfigFlags pFlags = Normal)](#writeEntry-15)
- [void writeEntry(const char \*key, const char \*value, KConfigBase::WriteConfigFlags pFlags = Normal)](#writeEntry-16)
- [template \<typename Rep, typename Period\> void writeEntry(const char \*key, std::chrono::duration\<Rep, Period\> value, KConfigBase::WriteConfigFlags pFlags = Normal)](#writeEntry-17) (since 6.22)
- [void writePathEntry(const QString &pKey, const QString &path, KConfigBase::WriteConfigFlags pFlags = Normal)](#writePathEntry)
- [void writePathEntry(const QString &pKey, const QStringList &value, KConfigBase::WriteConfigFlags pFlags = Normal)](#writePathEntry-1)
- [void writePathEntry(const char \*Key, const QString &path, KConfigBase::WriteConfigFlags pFlags = Normal)](#writePathEntry-2)
- [void writePathEntry(const char \*key, const QStringList &value, KConfigBase::WriteConfigFlags pFlags = Normal)](#writePathEntry-3)
- [void writeXdgListEntry(const QString &pKey, const QStringList &value, KConfigBase::WriteConfigFlags pFlags = Normal)](#writeXdgListEntry)
- [void writeXdgListEntry(const char \*key, const QStringList &value, KConfigBase::WriteConfigFlags pFlags = Normal)](#writeXdgListEntry-1)

## Detailed Description {#details}

If you want to access the top-level entries of a [KConfig](kconfig.md) object which are not associated with any group, use an empty group name. For example:

```cpp
auto config = KSharedConfig::openConfig();
auto globalGroup = KConfigGroup(config, QString());
```

A [KConfigGroup](kconfiggroup.md) will be read-only if it is constructed from a const config object or from another read-only group.

## Member Function Documentation {#member-function-documentation}

### KConfigGroup::KConfigGroup() {#KConfigGroup}

Constructs an invalid group.

*See also* [isValid](kconfiggroup.md#isValid)

### KConfigGroup::KConfigGroup(KConfigBase \**master*, const QString &*group*) {#KConfigGroup-1}

Constructs a config group corresponding to `group` in `master`.

This allows the creation of subgroups by passing another group as `master`. For example:

```cpp
auto generalGroup = KConfigGroup(config, "General");
auto preferencesGroup = KConfigGroup(&generalGroup, "Preferences");
preferencesGroup.writeEntry("SomeKey", true);
```

Will render the following in the configuration file:

```cpp
[General][Preferences]
SomeKey=true
```

### KConfigGroup::KConfigGroup(const KConfigBase \**master*, const QString &*group*) {#KConfigGroup-2}

Constructs a read-only config group by passing a const config object.

A read-only group will silently ignore any attempts to write to it.

This allows the creation of subgroups by passing an existing group as `master`.

### KConfigGroup::KConfigGroup(const QExplicitlySharedDataPointer\<KSharedConfig\> &*master*, const QString &*group*) {#KConfigGroup-3}

This function overloads [KConfigGroup::KConfigGroup(const KConfigBase\*,const QString&)](kconfiggroup.md#KConfigGroup-2).

### KConfig \*KConfigGroup::config() {#config}

Returns the config object that this group belongs to.

### const KConfig \*KConfigGroup::config() const {#config-1}

Returns the read-only config object that this group belongs to.

### void KConfigGroup::copyTo(KConfigBase \**other*, KConfigBase::WriteConfigFlags *pFlags* = Normal) const {#copyTo}

Copies the entries in this group to `other` configuration object with the given `pFlags`.

> **Note:** The `other` config object can be either another group or a different file.

### void KConfigGroup::deleteEntry(const QString &*pKey*, KConfigBase::WriteConfigFlags *pFlags* = Normal) {#deleteEntry}

Deletes the entry specified by `pKey` in the current group with the given `pFlags`.

This also hides system wide defaults.

*See also* [deleteGroup](kconfiggroup.md#deleteGroup)(), [readEntry](kconfiggroup.md#readEntry)(), [writeEntry](kconfiggroup.md#writeEntry)()

### void KConfigGroup::deleteEntry(const char \**key*, KConfigBase::WriteConfigFlags *pFlags* = Normal) {#deleteEntry-1}

The `key` will be encoded in UTF-8.

This function overloads KConfigGroup::deleteEntry(const QString&, WriteConfigFlags).

### void KConfigGroup::deleteGroup(KConfigBase::WriteConfigFlags *pFlags* = Normal) {#deleteGroup}

Delete all entries in the entire group with the given `pFlags`.

*See also* [deleteEntry](kconfiggroup.md#deleteEntry)()

### QMap\<QString, QString\> KConfigGroup::entryMap() const {#entryMap}

Returns a map (tree) of entries for all entries in this group.

Only the actual entry string is returned, none of the other internal data should be included.

### bool KConfigGroup::exists() const {#exists}

Returns whether the containing [KConfig](kconfig.md) object actually contains a group with this name.

### bool KConfigGroup::hasDefault(const QString &*key*) const {#hasDefault}

Returns whether a default is specified for an entry `key` in either the system wide configuration file or the global KDE config file.

If an application computes a default value at runtime for a certain entry, like:

```cpp
QColor computedDefault = qApp->palette().color(QPalette::Active, QPalette::Text);
QColor color = group.readEntry(key, computedDefault);
```

then it may wish to make the following check before writing back changes:

```cpp
if ( (value == computedDefault) && !group.hasDefault(key) )
   group.revertToDefault(key);
else
   group.writeEntry(key, value);
```

This ensures that as long as the entry is not modified to differ from the computed default, the application will keep using the computed default and will follow changes the computed default makes over time.

### bool KConfigGroup::hasDefault(const char \**key*) const {#hasDefault-1}

The `key` will be encoded in UTF-8.

This function overloads KConfigGroup::hasDefault(const QString&) const.

### bool KConfigGroup::hasKey(const QString &*key*) const {#hasKey}

Returns whether the `key` exists in this group in any of the configuration sources.

If this returns `false` for a key, [readEntry](kconfiggroup.md#readEntry)() (and its variants) will return the default value passed to them.

*See also* [readEntry](kconfiggroup.md#readEntry)()

### bool KConfigGroup::hasKey(const char \**key*) const {#hasKey-1}

The `key` will be encoded in UTF-8.

This function overloads KConfigGroup::hasKey(const QString&) const.

### bool KConfigGroup::isEntryImmutable(const QString &*key*) const {#isEntryImmutable}

Returns whether it is possible to change the given entry `key`.

If [isImmutable](kconfiggroup.md#isImmutable)() returns `true`, then this method will return `true` for all inputs.

*See also* [KAuthorized](kauthorized.md), [Kiosk - Simple configuration management for large deployment](https://develop.kde.org/docs/administration/kiosk/)

### bool KConfigGroup::isEntryImmutable(const char \**key*) const {#isEntryImmutable-1}

The `key` will be encoded in UTF-8.

This function overloads KConfigGroup::isEntryImmutable(const QString&) const.

### \[override virtual\] bool KConfigGroup::isImmutable() const {#isImmutable}

Reimplements: [KConfigBase::isImmutable() const](kconfigbase.md#isImmutable).

Returns whether this group may be changed.

*See also* [KAuthorized](kauthorized.md), [Kiosk - Simple configuration management for large deployment](https://develop.kde.org/docs/administration/kiosk/)

### bool KConfigGroup::isValid() const {#isValid}

Returns whether the group is valid.

A group is invalid if it was constructed without arguments.

You should not call any functions on an invalid group.

### QStringList KConfigGroup::keyList() const {#keyList}

Returns a list of keys this group contains.

### \[since 6.3\] void KConfigGroup::moveValuesTo(KConfigGroup &*other*, KConfigBase::WriteConfigFlags *pFlags* = Normal) {#moveValuesTo}

Moves the key-value pairs from one config group to the `other` with the given `pFlags`.

This function was introduced in Qt 6.3.

### void KConfigGroup::moveValuesTo(const QList\<const char \*\> &*keys*, KConfigGroup &*other*, KConfigBase::WriteConfigFlags *pFlags* = Normal) {#moveValuesTo-1}

Moves the key-value pairs with specific `keys` from one config group to the `other` with the given `pFlags`.

In case the entries do not exist the key is ignored.

### QString KConfigGroup::name() const {#name}

The name of this group.

The root group is named "\<default\>".

### KConfigGroup KConfigGroup::parent() const {#parent}

Returns the parent group that this group belongs to, or an invalid group if this is a top-level group.

### template \<typename T\> QList\<T\> KConfigGroup::readEntry(const QString &*key*, const QList\<T\> &*aDefault*) const {#readEntry}

Reads a list of values of an entry specified by `key` in the current group, returning `aDefault` value if the key is not found.

*See also* [readXdgListEntry](kconfiggroup.md#readXdgListEntry)(), [writeEntry](kconfiggroup.md#writeEntry)(), [deleteEntry](kconfiggroup.md#deleteEntry)(), [hasKey](kconfiggroup.md#hasKey)()

### QString KConfigGroup::readEntry(const QString &*key*, const QString &*aDefault*) const {#readEntry-1}

Reads the string value of an entry specified by `key` in the current group, returning `aDefault` value if the key is not found.

If you want to read a path, use [readPathEntry](kconfiggroup.md#readPathEntry)().

*See also* [readPathEntry](kconfiggroup.md#readPathEntry)(), [writeEntry](kconfiggroup.md#writeEntry)(), [deleteEntry](kconfiggroup.md#deleteEntry)(), [hasKey](kconfiggroup.md#hasKey)()

### QStringList KConfigGroup::readEntry(const QString &*key*, const QStringList &*aDefault*) const {#readEntry-2}

Reads the string list values of an entry specified by `key` in the current group, returning `aDefault` value if the key is not found.

*See also* [readXdgListEntry](kconfiggroup.md#readXdgListEntry)(), [writeEntry](kconfiggroup.md#writeEntry)(), [deleteEntry](kconfiggroup.md#deleteEntry)(), [hasKey](kconfiggroup.md#hasKey)()

### QVariant KConfigGroup::readEntry(const QString &*key*, const QVariant &*aDefault*) const {#readEntry-3}

Reads the value of an entry specified by `key` in the current group, returning `aDefault` value if the key is not found.

*See also* [writeEntry](kconfiggroup.md#writeEntry)(), [deleteEntry](kconfiggroup.md#deleteEntry)(), [hasKey](kconfiggroup.md#hasKey)()

### template \<typename T\> T KConfigGroup::readEntry(const QString &*key*, const T &*aDefault*) const {#readEntry-4}

Reads the value of an entry specified by `key` in the current group, returning `aDefault` value if the key is not found.

This template method makes it possible to write:

```cpp
QString foo = readEntry("...", QString("default"));
```

and the same with all other types supported by [QVariant](https://doc.qt.io/qt-6/qvariant.html).

The return type of the method is simply the same as the type of the default value.

> **Note:** [readEntry](kconfiggroup.md#readEntry)("...", [Qt::white](https://doc.qt.io/qt-6/qt.html#GlobalColor-enum)) will not compile because [Qt::white](https://doc.qt.io/qt-6/qt.html#GlobalColor-enum) is an enum. You must turn it into [readEntry](kconfiggroup.md#readEntry)("...", QColor([Qt::white](https://doc.qt.io/qt-6/qt.html#GlobalColor-enum))).

> **Note:** Only the following [QVariant](https://doc.qt.io/qt-6/qvariant.html) types are allowed : String, StringList, List, Font, Point, PointF, Rect, RectF, Size, SizeF, Color, Int, UInt, Bool, Double, LongLong, ULongLong, DateTime and Date.

*See also* [writeEntry](kconfiggroup.md#writeEntry)(), [deleteEntry](kconfiggroup.md#deleteEntry)(), [hasKey](kconfiggroup.md#hasKey)()

### \[since 6.22\] template \<typename Rep, typename Period\> std::chrono::duration\<Rep, Period\> KConfigGroup::readEntry(const QString &*key*, std::chrono::duration\<Rep, Period\> *defaultValue*) const {#readEntry-5}

Reads a std::chrono duration of an entry specified by `key` in the current group, returning the `defaultValue` if the key is not found.

This function was introduced in Qt 6.22.

### QVariantList KConfigGroup::readEntry(const QString &*key*, const QVariantList &*aDefault*) const {#readEntry-6}

> **Warning:** This function doesn't convert the items returned to any type. It's actually a list of [QVariant](https://doc.qt.io/qt-6/qvariant.html) strings. If you want the items converted to a specific type use [readEntry](kconfiggroup.md#readEntry)(const char\*, const [QList](https://doc.qt.io/qt-6/qlist.html)\<T\>&) const

This is an overloaded function.

*See also* [readEntry](kconfiggroup.md#readEntry)()

### QString KConfigGroup::readEntry(const QString &*key*, const char \**aDefault* = nullptr) const {#readEntry-7}

This function overloads KConfigGroup::readEntry(const QString&, const QString&) const.

### template \<typename T\> QList\<T\> KConfigGroup::readEntry(const char \**key*, const QList\<T\> &*aDefault*) const {#readEntry-8}

The `key` name will be encoded in UTF-8.

This function overloads KConfigGroup::readEntry\<T\>(const QString&, const QList\<T\>&) const.

### QString KConfigGroup::readEntry(const char \**key*, const QString &*aDefault*) const {#readEntry-9}

The `key` name will be encoded in UTF-8.

This function overloads KConfigGroup::readEntry(const QString&, const QString&) const.

### QStringList KConfigGroup::readEntry(const char \**key*, const QStringList &*aDefault*) const {#readEntry-10}

The `key` name will be encoded in UTF-8.

This function overloads KConfigGroup::readEntry(const QString&, const QStringList&) const.

### QVariant KConfigGroup::readEntry(const char \**key*, const QVariant &*aDefault*) const {#readEntry-11}

The `key` name will be encoded in UTF-8.

This function overloads KConfigGroup::readEntry(const QString&, const QVariant&) const.

### QVariantList KConfigGroup::readEntry(const char \**key*, const QVariantList &*aDefault*) const {#readEntry-12}

The `key` name will be encoded in UTF-8.

This function overloads KConfigGroup::readEntry(const QString&, const QVariantList&) const.

### template \<typename T\> T KConfigGroup::readEntry(const char \**key*, const T &*aDefault*) const {#readEntry-13}

The `key` name will be encoded in UTF-8.

This function overloads KConfigGroup::readEntry\<T\>(const QString&, const T&) const.

### QString KConfigGroup::readEntry(const char \**key*, const char \**aDefault* = nullptr) const {#readEntry-14}

The `key` name will be encoded in UTF-8.

This function overloads KConfigGroup::readEntry(const QString&, const QString&) const.

### \[since 6.22\] template \<typename Rep, typename Period\> std::chrono::duration\<Rep, Period\> KConfigGroup::readEntry(const char \**key*, std::chrono::duration\<Rep, Period\> *defaultValue*) const {#readEntry-15}

The `key` name will be encoded in UTF-8.

This function overloads [readEntry(const QString&, std::chrono::duration\<Rep, Period\>)](kconfiggroup.md#readEntry-5).

This function was introduced in Qt 6.22.

### QString KConfigGroup::readEntryUntranslated(const QString &*pKey*, const QString &*aDefault* = QString()) const {#readEntryUntranslated}

Reads the untranslated string for an entry specified by `pKey` in the current group, returning `aDefault` value if the key is not found.

### QString KConfigGroup::readEntryUntranslated(const char \**key*, const QString &*aDefault* = QString()) const {#readEntryUntranslated-1}

The `key` name will be encoded in UTF-8.

This function overloads KConfigGroup::readEntryUntranslated(const QString&, const QString&) const.

### QString KConfigGroup::readPathEntry(const QString &*pKey*, const QString &*aDefault*) const {#readPathEntry}

Reads the path value of an entry specified by `pKey` in the current group, returning `aDefault` value if the key is not found. If `aDefault` is null, an empty QString() is returned.

Dollar expansion is activated for this value, so that for example $HOME gets expanded.

### QStringList KConfigGroup::readPathEntry(const QString &*pKey*, const QStringList &*aDefault*) const {#readPathEntry-1}

Reads the list of paths of an entry specified by `pKey` in the current group, returning `aDefault` value if the key is not found.

Dollar expansion is activated for this value, so that for example $HOME gets expanded.

### QString KConfigGroup::readPathEntry(const char \**key*, const QString &*aDefault*) const {#readPathEntry-2}

The `key` name will be encoded in UTF-8.

This function overloads KConfigGroup::readPathEntry(const QString&, const QString&) const.

### QStringList KConfigGroup::readPathEntry(const char \**key*, const QStringList &*aDefault*) const {#readPathEntry-3}

The `key` name will be encoded in UTF-8.

This function overloads KConfigGroup::readPathEntry(const QString&, const QStringList&) const.

### QStringList KConfigGroup::readXdgListEntry(const QString &*pKey*, const QStringList &*aDefault* = QStringList()) const {#readXdgListEntry}

Reads the list of strings of an entry specified by `pKey` in the current group, returning `aDefault` value if the key is not found.

*See also* [readEntry](kconfiggroup.md#readEntry-2)(const QString&, const QStringList&)

### QStringList KConfigGroup::readXdgListEntry(const char \**key*, const QStringList &*aDefault* = QStringList()) const {#readXdgListEntry-1}

The `key` name will be encoded in UTF-8.

This function overloads KConfigGroup::readXdgListEntry(const QString&, const QStringList&) const.

### void KConfigGroup::reparent(KConfigBase \**parent*, KConfigBase::WriteConfigFlags *pFlags* = Normal) {#reparent}

Changes the configuration object that this group belongs to to `parent` with the given `pFlags`.

> **Note:** If `parent` is already the parent of this group, this method will have no effect.

### void KConfigGroup::revertToDefault(const QString &*key*, KConfigBase::WriteConfigFlags *pFlag* = WriteConfigFlags()) {#revertToDefault}

Reverts an entry `key` to the default settings with the given `pFlag` in the current group.

The default settings will be either the system wide (default) value or the value specified in the global KDE config file.

To revert entries in the global KDE config file, the global KDE config file should be opened *explicitly* in a *separate* config object.

> **Note:** This is not the same as deleting the key, as instead the global setting will be copied to the configuration file that this object manipulates.

### void KConfigGroup::revertToDefault(const char \**key*, KConfigBase::WriteConfigFlags *pFlag* = WriteConfigFlags()) {#revertToDefault-1}

The `key` will be encoded in UTF-8.

This function overloads KConfigGroup::revertToDefault(const QString&, WriteConfigFlags).

### void KConfigGroup::writeEntry(const QString &*key*, const QVariant &*value*, KConfigBase::WriteConfigFlags *pFlags* = Normal) {#writeEntry}

Writes `key` and `value` to the configuration object with the given `pFlags`.

Changes to the file will only be synced with [KConfig::reparseConfiguration](kconfig.md#reparseConfiguration)() or [KConfigBase::sync](kconfigbase.md#sync)().

*See also* [readEntry](kconfiggroup.md#readEntry)(), [writeXdgListEntry](kconfiggroup.md#writeXdgListEntry)(), [deleteEntry](kconfiggroup.md#deleteEntry)()

### void KConfigGroup::writeEntry(const QString &*key*, const QByteArray &*value*, KConfigBase::WriteConfigFlags *pFlags* = Normal) {#writeEntry-1}

This function overloads KConfigGroup::writeEntry(const QString&, const QVariant&, WriteConfigFlags).

### template \<typename T\> void KConfigGroup::writeEntry(const QString &*key*, const QList\<T\> &*value*, KConfigBase::WriteConfigFlags *pFlags* = Normal) {#writeEntry-2}

This function overloads KConfigGroup::writeEntry(const QString&, const QVariant&, WriteConfigFlags).

### void KConfigGroup::writeEntry(const QString &*key*, const QString &*value*, KConfigBase::WriteConfigFlags *pFlags* = Normal) {#writeEntry-3}

The `key` will be encoded in UTF-8.

This function overloads KConfigGroup::writeEntry(const QString&, const QVariant&, WriteConfigFlags).

### void KConfigGroup::writeEntry(const QString &*key*, const QStringList &*value*, KConfigBase::WriteConfigFlags *pFlags* = Normal) {#writeEntry-4}

This function overloads KConfigGroup::writeEntry(const QString&, const QVariant&, WriteConfigFlags).

### void KConfigGroup::writeEntry(const QString &*key*, const QVariantList &*value*, KConfigBase::WriteConfigFlags *pFlags* = Normal) {#writeEntry-5}

This function overloads KConfigGroup::writeEntry(const QString&, const QVariant&, WriteConfigFlags).

### template \<typename T\> void KConfigGroup::writeEntry(const QString &*key*, const T &*value*, KConfigBase::WriteConfigFlags *pFlags* = Normal) {#writeEntry-6}

This function overloads KConfigGroup::writeEntry(const QString&, const QVariant&, WriteConfigFlags).

### void KConfigGroup::writeEntry(const QString &*key*, const char \**value*, KConfigBase::WriteConfigFlags *pFlags* = Normal) {#writeEntry-7}

This function overloads KConfigGroup::writeEntry(const QString&, const QVariant&, WriteConfigFlags).

### \[since 6.22\] template \<typename Rep, typename Period\> void KConfigGroup::writeEntry(const QString &*key*, std::chrono::duration\<Rep, Period\> *value*, KConfigBase::WriteConfigFlags *pFlags* = Normal) {#writeEntry-8}

This function overloads KConfigGroup::writeEntry(const QString&, const QVariant&, WriteConfigFlags).

This function was introduced in Qt 6.22.

### void KConfigGroup::writeEntry(const char \**key*, const QByteArray &*value*, KConfigBase::WriteConfigFlags *pFlags* = Normal) {#writeEntry-9}

The `key` will be encoded in UTF-8.

This function overloads KConfigGroup::writeEntry(const QString&, const QVariant&, WriteConfigFlags).

### template \<typename T\> void KConfigGroup::writeEntry(const char \**key*, const QList\<T\> &*value*, KConfigBase::WriteConfigFlags *pFlags* = Normal) {#writeEntry-10}

The `key` will be encoded in UTF-8.

This function overloads KConfigGroup::writeEntry(const QString&, const QVariant&, WriteConfigFlags).

### void KConfigGroup::writeEntry(const char \**key*, const QString &*value*, KConfigBase::WriteConfigFlags *pFlags* = Normal) {#writeEntry-11}

The `key` will be encoded in UTF-8.

This function overloads KConfigGroup::writeEntry(const QString&, const QVariant&, WriteConfigFlags).

### void KConfigGroup::writeEntry(const char \**key*, const QStringList &*value*, KConfigBase::WriteConfigFlags *pFlags* = Normal) {#writeEntry-12}

The `key` will be encoded in UTF-8.

This function overloads KConfigGroup::writeEntry(const QString&, const QVariant&, WriteConfigFlags).

### void KConfigGroup::writeEntry(const char \**key*, const QVariant &*value*, KConfigBase::WriteConfigFlags *pFlags* = Normal) {#writeEntry-13}

The `key` will be encoded in UTF-8.

This function overloads KConfigGroup::writeEntry(const QString&, const QVariant&, WriteConfigFlags).

### void KConfigGroup::writeEntry(const char \**key*, const QVariantList &*value*, KConfigBase::WriteConfigFlags *pFlags* = Normal) {#writeEntry-14}

The `key` will be encoded in UTF-8.

This function overloads KConfigGroup::writeEntry(const QString&, const QVariant&, WriteConfigFlags).

### template \<typename T\> void KConfigGroup::writeEntry(const char \**key*, const T &*value*, KConfigBase::WriteConfigFlags *pFlags* = Normal) {#writeEntry-15}

The `key` will be encoded in UTF-8.

This function overloads KConfigGroup::writeEntry(const QString&, const QVariant&, WriteConfigFlags).

### void KConfigGroup::writeEntry(const char \**key*, const char \**value*, KConfigBase::WriteConfigFlags *pFlags* = Normal) {#writeEntry-16}

The `key` will be encoded in UTF-8.

This function overloads KConfigGroup::writeEntry(const QString&, const QVariant&, WriteConfigFlags).

### \[since 6.22\] template \<typename Rep, typename Period\> void KConfigGroup::writeEntry(const char \**key*, std::chrono::duration\<Rep, Period\> *value*, KConfigBase::WriteConfigFlags *pFlags* = Normal) {#writeEntry-17}

The `key` will be encoded in UTF-8.

This function overloads KConfigGroup::writeEntry(const QString&, const QVariant&, WriteConfigFlags).

This function was introduced in Qt 6.22.

### void KConfigGroup::writePathEntry(const QString &*pKey*, const QString &*path*, KConfigBase::WriteConfigFlags *pFlags* = Normal) {#writePathEntry}

Writes `pKey` and `value` to the configuration object with the given `pFlags`, where the `value` matches a file path.

If the path includes the absolute name for $HOME, the user's home directory is replaced with "$HOME" in the persistent storage.

The path should therefore be read back with [readPathEntry](kconfiggroup.md#readPathEntry)().

*See also* [writeEntry](kconfiggroup.md#writeEntry)(), [readPathEntry](kconfiggroup.md#readPathEntry)()

### void KConfigGroup::writePathEntry(const QString &*pKey*, const QStringList &*value*, KConfigBase::WriteConfigFlags *pFlags* = Normal) {#writePathEntry-1}

Writes `pKey` and `value` to the configuration object with the given `pFlags`, where the `value` matches a file path.

If the path includes the absolute name for $HOME, the user's home directory is replaced with "$HOME" in the persistent storage.

The path should therefore be read back with [readPathEntry](kconfiggroup.md#readPathEntry)().

*See also* [writeEntry](kconfiggroup.md#writeEntry)(), [readPathEntry](kconfiggroup.md#readPathEntry)()

### void KConfigGroup::writePathEntry(const char \**Key*, const QString &*path*, KConfigBase::WriteConfigFlags *pFlags* = Normal) {#writePathEntry-2}

The `key` will be encoded in UTF-8.

This function overloads KConfigGroup::writePathEntry(const QString&, const QString&, WriteConfigFlags).

### void KConfigGroup::writePathEntry(const char \**key*, const QStringList &*value*, KConfigBase::WriteConfigFlags *pFlags* = Normal) {#writePathEntry-3}

The `key` will be encoded in UTF-8.

This function overloads KConfigGroup::writePathEntry(const QString&, const QStringList&, WriteConfigFlags).

### void KConfigGroup::writeXdgListEntry(const QString &*pKey*, const QStringList &*value*, KConfigBase::WriteConfigFlags *pFlags* = Normal) {#writeXdgListEntry}

Writes `pKey` and `value` to the configuration object with the given `pFlags`, where the `value` matches a list of strings following the XDG desktop entry specification.

*See also* [writeEntry](kconfiggroup.md#writeEntry)(), [readXdgListEntry](kconfiggroup.md#readXdgListEntry)()

### void KConfigGroup::writeXdgListEntry(const char \**key*, const QStringList &*value*, KConfigBase::WriteConfigFlags *pFlags* = Normal) {#writeXdgListEntry-1}

The `key` will be encoded in UTF-8.

This function overloads KConfigGroup::writeXdgListEntry(const QString&, const QStringList&, WriteConfigFlags).

## Macro Documentation {#macro-documentation}

### KCONFIGGROUP\_DECLARE\_ENUM\_QOBJECT(*Class*, *Enum*) {#KCONFIGGROUP_DECLARE_ENUM_QOBJECT}

To add support for your own enum `Enum` in [KConfig](kconfig.md), you can declare them with [Q\_ENUM](https://doc.qt.io/qt-6/qobject.html#Q_ENUM)() in a [QObject](https://doc.qt.io/qt-6/qobject.html) subclass `Class` (which will make moc generate the code to turn the enum into a string and vice-versa), and then (in the cpp code) use the macro

```cpp
KCONFIGGROUP_DECLARE_ENUM_QOBJECT(MyClass, MyEnum)
```

### KCONFIGGROUP\_DECLARE\_FLAGS\_QOBJECT(*Class*, *Flags*) {#KCONFIGGROUP_DECLARE_FLAGS_QOBJECT}

Similar to [KCONFIGGROUP\_DECLARE\_ENUM\_QOBJECT](kconfiggroup.md#KCONFIGGROUP_DECLARE_ENUM_QOBJECT) for adding your own `Flags` in [KConfig](kconfig.md) but for flags declared with [Q\_FLAG](https://doc.qt.io/qt-6/qobject.html#Q_FLAG)() for a [QObject](https://doc.qt.io/qt-6/qobject.html) subclass `Class`. (where multiple values can be set at the same time)
