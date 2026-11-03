---
title: "Attica::PrivateData Class"
description: "Represents private data."
---

# Attica::PrivateData Class

Represents private data. [More...](#details)

- **Header:** `#include <Attica/PrivateData>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS Attica)`  
  `target_link_libraries(mytarget PRIVATE KF6::Attica)`

[List of all members, including inherited members](attica-privatedata-members.md)

## Public Types

- [PrivateData::List](#List-typedef)

## Public Functions

- [PrivateData()](#PrivateData)
- [QString attribute(const QString &key) const](#attribute)
- [QStringList keys() const](#keys)
- [void setAttribute(const QString &key, const QString &value)](#setAttribute)
- [void setTimestamp(const QString &key, const QDateTime &when)](#setTimestamp)
- [QDateTime timestamp(const QString &key) const](#timestamp)

## Detailed Description {#details}

## Member Type Documentation {#member-type-documentation}

### PrivateData::List {#List-typedef}

## Member Function Documentation {#member-function-documentation}

### PrivateData::PrivateData() {#PrivateData}

### QString PrivateData::attribute(const QString &*key*) const {#attribute}

Returns an attribute referenced by `key`.

*See also* [setAttribute](attica-privatedata.md#setAttribute)()

### QStringList PrivateData::keys() const {#keys}

Returns a list of fetched keys.

### void PrivateData::setAttribute(const QString &*key*, const QString &*value*) {#setAttribute}

Sets an attribute referenced by `key` to `value`.

*See also* [attribute](attica-privatedata.md#attribute)()

### void PrivateData::setTimestamp(const QString &*key*, const QDateTime &*when*) {#setTimestamp}

Sets when an attribute last was changed (mostly for internal use).

*See also* [timestamp](attica-privatedata.md#timestamp)()

### QDateTime PrivateData::timestamp(const QString &*key*) const {#timestamp}

Returns the date and time an attribute last was changed.

*See also* [setTimestamp](attica-privatedata.md#setTimestamp)()
