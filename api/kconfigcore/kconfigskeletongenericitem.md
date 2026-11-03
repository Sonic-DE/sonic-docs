---
title: "KConfigSkeletonGenericItem Class"
description: "Base class for storing a preferences setting of type T."
---

# KConfigSkeletonGenericItem Class

Base class for storing a preferences setting of type `T`.

- **Header:** `#include <KCoreConfigSkeleton>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS Config)`  
  `target_link_libraries(mytarget PRIVATE KF6::ConfigCore)`
- **Inherits:** [KConfigSkeletonItem](kconfigskeletonitem.md)
- **Inherited By:** [KCoreConfigSkeleton::ItemBool](kcoreconfigskeleton-itembool.md), [KCoreConfigSkeleton::ItemDateTime](kcoreconfigskeleton-itemdatetime.md), [KCoreConfigSkeleton::ItemDouble](kcoreconfigskeleton-itemdouble.md), [KCoreConfigSkeleton::ItemInt](kcoreconfigskeleton-itemint.md), [KCoreConfigSkeleton::ItemIntList](kcoreconfigskeleton-itemintlist.md), [KCoreConfigSkeleton::ItemLongLong](kcoreconfigskeleton-itemlonglong.md), [KCoreConfigSkeleton::ItemPoint](kcoreconfigskeleton-itempoint.md), [KCoreConfigSkeleton::ItemPointF](kcoreconfigskeleton-itempointf.md), [KCoreConfigSkeleton::ItemProperty](kcoreconfigskeleton-itemproperty.md), [KCoreConfigSkeleton::ItemRect](kcoreconfigskeleton-itemrect.md), [KCoreConfigSkeleton::ItemRectF](kcoreconfigskeleton-itemrectf.md), [KCoreConfigSkeleton::ItemSize](kcoreconfigskeleton-itemsize.md), [KCoreConfigSkeleton::ItemSizeF](kcoreconfigskeleton-itemsizef.md), [KCoreConfigSkeleton::ItemString](kcoreconfigskeleton-itemstring.md), [KCoreConfigSkeleton::ItemStringList](kcoreconfigskeleton-itemstringlist.md), [KCoreConfigSkeleton::ItemTime](kcoreconfigskeleton-itemtime.md), [KCoreConfigSkeleton::ItemUInt](kcoreconfigskeleton-itemuint.md), [KCoreConfigSkeleton::ItemULongLong](kcoreconfigskeleton-itemulonglong.md), [KCoreConfigSkeleton::ItemUrl](kcoreconfigskeleton-itemurl.md), and [KCoreConfigSkeleton::ItemUrlList](kcoreconfigskeleton-itemurllist.md)

## Public Functions

- [KConfigSkeletonGenericItem(const QString &\_group, const QString &\_key, T &reference, T defaultValue)](#KConfigSkeletonGenericItem)
- [void setDefault()](#setDefault)
- [void setDefaultValue(const T &v)](#setDefaultValue)
- [void setValue(const T &v)](#setValue)
- [T &value()](#value)
- [const T &value() const](#value-1)

## Detailed Description {#details}

## Member Function Documentation {#member-function-documentation}

### KConfigSkeletonGenericItem::KConfigSkeletonGenericItem(const QString &*\_group*, const QString &*\_key*, T &*reference*, T *defaultValue*) {#KConfigSkeletonGenericItem}

Constructs a generic skeleton item with the given `_group`, `_key`, the initial value `reference` to hold in the item, and the `defaultValue` for the item.

### \[override virtual\] void KConfigSkeletonGenericItem::setDefault() {#setDefault}

Reimplements: [KConfigSkeletonItem::setDefault()](kconfigskeletonitem.md#setDefault).

Sets the value for this item to the default value.

### \[virtual\] void KConfigSkeletonGenericItem::setDefaultValue(const T &*v*) {#setDefaultValue}

Sets the default value `v` for this item.

### void KConfigSkeletonGenericItem::setValue(const T &*v*) {#setValue}

Sets the value `v` of this [KConfigSkeletonItem](kconfigskeletonitem.md).

*See also* [value](kconfigskeletongenericitem.md#value)()

### T &KConfigSkeletonGenericItem::value() {#value}

Returns the value of this [KConfigSkeletonItem](kconfigskeletonitem.md).

*See also* [setValue](kconfigskeletongenericitem.md#setValue)()

### const T &KConfigSkeletonGenericItem::value() const {#value-1}

Returns the const value of this [KConfigSkeletonItem](kconfigskeletonitem.md).
