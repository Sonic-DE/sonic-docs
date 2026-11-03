---
title: "KPropertySkeletonItem Class"
description: "Class for proxying a QObject property as a preferences setting."
---

# KPropertySkeletonItem Class

Class for proxying a [QObject](https://doc.qt.io/qt-6/qobject.html) property as a preferences setting. [More...](#details)

- **Header:** `#include <KCoreConfigSkeleton>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS Config)`  
  `target_link_libraries(mytarget PRIVATE KF6::ConfigCore)`
- **Inherits:** [KConfigSkeletonItem](kconfigskeletonitem.md)

[List of all members, including inherited members](kpropertyskeletonitem-members.md)

## Public Functions

- [KPropertySkeletonItem(QObject \*object, const QByteArray &propertyName, const QVariant &defaultValue)](#KPropertySkeletonItem)
- [void setNotifyFunction(const std::function\<void ()\> &impl)](#setNotifyFunction)

## Detailed Description {#details}

This class represents one preferences setting as used by [KCoreConfigSkeleton](kcoreconfigskeleton.md). Unlike other [KConfigSkeletonItem](kconfigskeletonitem.md) subclasses, this one won't store the preference in [KConfig](kconfig.md) but will use a [QObject](https://doc.qt.io/qt-6/qobject.html) property as storage, allowing to implement callbacks to run when a configuration property changes. You will have to register instances of this class with the function [KCoreConfigSkeleton::addItem](kcoreconfigskeleton.md#addItem)().

*See also* [KConfigSkeletonItem](kconfigskeletonitem.md)

## Member Function Documentation {#member-function-documentation}

### KPropertySkeletonItem::KPropertySkeletonItem(QObject \**object*, const QByteArray &*propertyName*, const QVariant &*defaultValue*) {#KPropertySkeletonItem}

Constructs a property skeleton item instance that allows to manage the `propertyName` and the property's `defaultValue` present in a [QObject](https://doc.qt.io/qt-6/qobject.html) `object`.

### void KPropertySkeletonItem::setNotifyFunction(const std::function\<void ()\> &*impl*) {#setNotifyFunction}

Sets a notify function `impl` that will be invoked when the value of the property changes.
