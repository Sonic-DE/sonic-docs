---
title: "KSycocaEntry Class"
description: "Base class for all Sycoca entries."
---

# KSycocaEntry Class

Base class for all Sycoca entries. [More...](#details)

- **Header:** `#include <KSycocaEntry>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS Service)`  
  `target_link_libraries(mytarget PRIVATE KF6::Service)`
- **Inherits:** [QSharedData](https://doc.qt.io/qt-6/qshareddata.html)
- **Inherited By:** [KService](kservice.md) and [KServiceGroup](kservicegroup.md)

[List of all members, including inherited members](ksycocaentry-members.md)

## Public Types

- [KSycocaEntry::List](#List-typedef)
- [KSycocaEntry::Ptr](#Ptr-typedef)

## Public Functions

- [QString entryPath() const](#entryPath)
- [bool isDeleted() const](#isDeleted)
- [bool isSeparator() const](#isSeparator)
- [bool isType(KSycocaType t) const](#isType)
- [bool isValid() const](#isValid)
- [QString name() const](#name)
- [void setDeleted(bool deleted)](#setDeleted)
- [QString storageId() const](#storageId)

## Detailed Description {#details}

You can't create an instance of [KSycocaEntry](ksycocaentry.md), but it provides the common functionality for servicetypes and services.

*See also* [http://techbase.kde.org/Development/Architecture/KDE3/System_Configuration_Cache](http://techbase.kde.org/Development/Architecture/KDE3/System_Configuration_Cache)

## Member Type Documentation {#member-type-documentation}

### KSycocaEntry::List {#List-typedef}

A list of shared data pointers for [KSycocaEntry](ksycocaentry.md).

### KSycocaEntry::Ptr {#Ptr-typedef}

A shared data pointer for [KSycocaEntry](ksycocaentry.md).

## Member Function Documentation {#member-function-documentation}

### QString KSycocaEntry::entryPath() const {#entryPath}

Returns the path of this entry The path can be absolute or relative. The corresponding factory should know relative to what.

### bool KSycocaEntry::isDeleted() const {#isDeleted}

Returns `true` if deleted

### bool KSycocaEntry::isSeparator() const {#isSeparator}

Returns `true`, if this is a separator

### bool KSycocaEntry::isType(KSycocaType *t*) const {#isType}

Returns true if this sycoca entry is of the given type `t`.

### bool KSycocaEntry::isValid() const {#isValid}

Returns `true` if valid

### QString KSycocaEntry::name() const {#name}

Returns the name of this entry

### void KSycocaEntry::setDeleted(bool *deleted*) {#setDeleted}

Sets whether or not this service is deleted

*See also* [isDeleted](ksycocaentry.md#isDeleted)()

### QString KSycocaEntry::storageId() const {#storageId}

Returns the unique ID for this entry

In practice, this is storageId() for [KService](kservice-module.md) and [name](ksycocaentry.md#name)() for everything else.
