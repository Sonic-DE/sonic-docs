---
title: "Attica::HomePageEntry Class"
description: "The HomePageEntry class contains information about one home page entry."
---

# Attica::HomePageEntry Class

The [HomePageEntry](attica-homepageentry.md) class contains information about one home page entry. [More...](#details)

- **Header:** `#include <Attica/HomePageEntry>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS Attica)`  
  `target_link_libraries(mytarget PRIVATE KF6::Attica)`

[List of all members, including inherited members](attica-homepageentry-members.md)

## Public Types

- [HomePageEntry::List](#List-typedef)

## Public Functions

- [HomePageEntry()](#HomePageEntry)
- [void setType(const QString &type)](#setType)
- [void setUrl(const QUrl &url)](#setUrl)
- [QString type() const](#type)
- [QUrl url() const](#url)

## Detailed Description {#details}

It consists of a type and a home page url.

## Member Type Documentation {#member-type-documentation}

### HomePageEntry::List {#List-typedef}

## Member Function Documentation {#member-function-documentation}

### HomePageEntry::HomePageEntry() {#HomePageEntry}

Creates an empty [HomePageEntry](attica-homepageentry.md)

### void HomePageEntry::setType(const QString &*type*) {#setType}

*See also* [type](attica-homepageentry.md#type)()

### void HomePageEntry::setUrl(const QUrl &*url*) {#setUrl}

*See also* [url](attica-homepageentry.md#url)()

### QString HomePageEntry::type() const {#type}

*See also* [setType](attica-homepageentry.md#setType)()

### QUrl HomePageEntry::url() const {#url}

*See also* [setUrl](attica-homepageentry.md#setUrl)()
