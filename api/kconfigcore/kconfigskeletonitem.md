---
title: "KConfigSkeletonItem Class"
description: "Class for storing a preferences setting."
---

# KConfigSkeletonItem Class

Class for storing a preferences setting. [More...](#details)

- **Header:** `#include <KCoreConfigSkeleton>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS Config)`  
  `target_link_libraries(mytarget PRIVATE KF6::ConfigCore)`
- **Inherited By:** [KConfigSkeletonGenericItem](kconfigskeletongenericitem.md) and [KPropertySkeletonItem](kpropertyskeletonitem.md)

[List of all members, including inherited members](kconfigskeletonitem-members.md)

## Public Types

- [KConfigSkeletonItem::Dict](#Dict-typedef)
- [KConfigSkeletonItem::DictIterator](#DictIterator-typedef)
- [KConfigSkeletonItem::List](#List-typedef)

## Public Functions

- [KConfigSkeletonItem(const QString &\_group, const QString &\_key)](#KConfigSkeletonItem)
- [KConfigGroup configGroup(KConfig \*config) const](#configGroup)
- [QVariant getDefault() const](#getDefault)
- [QString group() const](#group)
- [bool isDefault() const](#isDefault)
- [bool isEqual(const QVariant &p) const](#isEqual)
- [bool isImmutable() const](#isImmutable)
- [bool isSaveNeeded() const](#isSaveNeeded)
- [QString key() const](#key)
- [QString label() const](#label)
- [QVariant maxValue() const](#maxValue)
- [QVariant minValue() const](#minValue)
- [QString name() const](#name)
- [QVariant property() const](#property)
- [void readConfig(KConfig \*)](#readConfig)
- [void readDefault(KConfig \*)](#readDefault)
- [void setDefault()](#setDefault)
- [void setGroup(const KConfigGroup &cg)](#setGroup)
- [void setGroup(const QString &\_group)](#setGroup-1)
- [void setKey(const QString &\_key)](#setKey)
- [void setLabel(const QString &l)](#setLabel)
- [void setName(const QString &\_name)](#setName)
- [void setProperty(const QVariant &p)](#setProperty)
- [void setToolTip(const QString &t)](#setToolTip)
- [void setWhatsThis(const QString &w)](#setWhatsThis)
- [void setWriteFlags(KConfigBase::WriteConfigFlags flags)](#setWriteFlags)
- [void swapDefault()](#swapDefault)
- [QString toolTip() const](#toolTip)
- [QString whatsThis() const](#whatsThis)
- [void writeConfig(KConfig \*)](#writeConfig)
- [KConfigBase::WriteConfigFlags writeFlags() const](#writeFlags)

## Protected Functions

- [void readImmutability(const KConfigGroup &group)](#readImmutability)

## Detailed Description {#details}

This class represents one preferences setting as used by [KCoreConfigSkeleton](kcoreconfigskeleton.md). Subclasses of [KConfigSkeletonItem](kconfigskeletonitem.md) implement storage functions for a certain type of setting. Normally you don't have to use this class directly. Use the special addItem() functions of [KCoreConfigSkeleton](kcoreconfigskeleton.md) instead. If you subclass this class you will have to register instances with the function [KCoreConfigSkeleton::addItem](kcoreconfigskeleton.md#addItem)().

*See also* [KCoreConfigSkeleton](kcoreconfigskeleton.md)

## Member Type Documentation {#member-type-documentation}

### KConfigSkeletonItem::Dict {#Dict-typedef}

### KConfigSkeletonItem::DictIterator {#DictIterator-typedef}

### KConfigSkeletonItem::List {#List-typedef}

## Member Function Documentation {#member-function-documentation}

### KConfigSkeletonItem::KConfigSkeletonItem(const QString &*\_group*, const QString &*\_key*) {#KConfigSkeletonItem}

Constructs a skeleton item instance with the given Config file `_group` and `_key`.

### KConfigGroup KConfigSkeletonItem::configGroup(KConfig \**config*) const {#configGroup}

Returns a [KConfigGroup](kconfiggroup.md), the one provided by [setGroup](kconfigskeletonitem.md#setGroup)(const [KConfigGroup](kconfiggroup.md)&) if it's valid, or make one from `config` and item's group.

*See also* [setGroup](kconfigskeletonitem.md#setGroup)()

### QVariant KConfigSkeletonItem::getDefault() const {#getDefault}

Returns the default value.

### QString KConfigSkeletonItem::group() const {#group}

Returns the name of the config file group.

*See also* [setGroup](kconfigskeletonitem.md#setGroup)()

### bool KConfigSkeletonItem::isDefault() const {#isDefault}

Returns if this item is set to its default value.

### \[pure virtual\] bool KConfigSkeletonItem::isEqual(const QVariant &*p*) const {#isEqual}

Checks whether the item is equal to `p`.

Use this function to compare items that use custom types, because QVariant::operator== will not work for those.

Returns `true` if the item is equal to `p`, `false` otherwise

### bool KConfigSkeletonItem::isImmutable() const {#isImmutable}

Returns if the entry can be modified.

### bool KConfigSkeletonItem::isSaveNeeded() const {#isSaveNeeded}

Returns if the item has a different value than the previously loaded value.

### QString KConfigSkeletonItem::key() const {#key}

Returns the config file key.

*See also* [setKey](kconfigskeletonitem.md#setKey)()

### QString KConfigSkeletonItem::label() const {#label}

Returns the label of the item.

*See also* [setLabel](kconfigskeletonitem.md#setLabel)()

### \[virtual\] QVariant KConfigSkeletonItem::maxValue() const {#maxValue}

Returns the maximum value of this item or invalid if not specified.

### \[virtual\] QVariant KConfigSkeletonItem::minValue() const {#minValue}

Returns the minimum value of this item or invalid if not specified.

### QString KConfigSkeletonItem::name() const {#name}

Returns the internal name of the settings entry.

*See also* [setName](kconfigskeletonitem.md#setName)()

### \[pure virtual\] QVariant KConfigSkeletonItem::property() const {#property}

Returns this item as a property.

*See also* [setProperty](kconfigskeletonitem.md#setProperty)()

### \[pure virtual\] void KConfigSkeletonItem::readConfig(*KConfig \**) {#readConfig}

This function is called by [KCoreConfigSkeleton](kcoreconfigskeleton.md) to read the value for this setting from a config file.

### \[pure virtual\] void KConfigSkeletonItem::readDefault(*KConfig \**) {#readDefault}

Reads the global default value.

### \[protected\] void KConfigSkeletonItem::readImmutability(const KConfigGroup &*group*) {#readImmutability}

Sets mIsImmutable to `true` if mKey in config is immutable.

`group` [KConfigGroup](kconfiggroup.md) to check if mKey is immutable in

### \[pure virtual\] void KConfigSkeletonItem::setDefault() {#setDefault}

Sets the current value to the default value.

*See also* [isDefault](kconfigskeletonitem.md#isDefault)()

### void KConfigSkeletonItem::setGroup(const KConfigGroup &*cg*) {#setGroup}

Sets a config file group by giving the [KConfigGroup](kconfiggroup.md) `cg`.

Allow the item to be in nested groups.

*See also* [group](kconfigskeletonitem.md#group)()

### void KConfigSkeletonItem::setGroup(const QString &*\_group*) {#setGroup-1}

Sets the config file `_group`.

### void KConfigSkeletonItem::setKey(const QString &*\_key*) {#setKey}

Sets the config file `_key`.

*See also* [key](kconfigskeletonitem.md#key)()

### void KConfigSkeletonItem::setLabel(const QString &*l*) {#setLabel}

Sets the label `l` providing a translated one-line description of the item.

*See also* [label](kconfigskeletonitem.md#label)()

### void KConfigSkeletonItem::setName(const QString &*\_name*) {#setName}

Sets the internal name of the settings entry with the given `_name`.

*See also* [name](kconfigskeletonitem.md#name)()

### \[pure virtual\] void KConfigSkeletonItem::setProperty(const QVariant &*p*) {#setProperty}

Sets the settings item to the property `p`.

*See also* [property](kconfigskeletonitem.md#property)()

### void KConfigSkeletonItem::setToolTip(const QString &*t*) {#setToolTip}

Sets the ToolTip `t` description of this item.

*See also* [toolTip](kconfigskeletonitem.md#toolTip)()

### void KConfigSkeletonItem::setWhatsThis(const QString &*w*) {#setWhatsThis}

Sets WhatsThis description `w` of this item.

*See also* [whatsThis](kconfigskeletonitem.md#whatsThis)()

### void KConfigSkeletonItem::setWriteFlags(KConfigBase::WriteConfigFlags *flags*) {#setWriteFlags}

Sets the write `flags` to be used when writing the configuration.

*See also* [writeFlags](kconfigskeletonitem.md#writeFlags)(), [KConfigBase::WriteConfigFlags](kconfigbase.md#WriteConfigFlag-enum), [KConfigWatcher](kconfigwatcher.md)

### \[pure virtual\] void KConfigSkeletonItem::swapDefault() {#swapDefault}

Exchanges the current value with the default value.

Used by [KCoreConfigSkeleton::useDefaults](kcoreconfigskeleton.md#useDefaults)(bool).

### QString KConfigSkeletonItem::toolTip() const {#toolTip}

Returns the ToolTip description of this item.

*See also* [setToolTip](kconfigskeletonitem.md#setToolTip)()

### QString KConfigSkeletonItem::whatsThis() const {#whatsThis}

Returns the WhatsThis description of item.

*See also* [setWhatsThis](kconfigskeletonitem.md#setWhatsThis)()

### \[pure virtual\] void KConfigSkeletonItem::writeConfig(*KConfig \**) {#writeConfig}

This function is called by [KCoreConfigSkeleton](kcoreconfigskeleton.md) to write the value of this setting to a config file. Make sure to pass [writeFlags](kconfigskeletonitem.md#writeFlags)() to every call of [KConfigGroup::writeEntry](kconfiggroup.md#writeEntry)() and [KConfigGroup::revertToDefault](kconfiggroup.md#revertToDefault)().

### KConfigBase::WriteConfigFlags KConfigSkeletonItem::writeFlags() const {#writeFlags}

Returns write flags to be used when writing the configuration.

They should be passed to every call of [KConfigGroup::writeEntry](kconfiggroup.md#writeEntry)() and [KConfigGroup::revertToDefault](kconfiggroup.md#revertToDefault)().

*See also* [setWriteFlags](kconfigskeletonitem.md#setWriteFlags)()
