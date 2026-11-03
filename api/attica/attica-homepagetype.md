---
title: "Attica::HomePageType Class"
description: "The HomePageType class contains information about one home page type."
---

# Attica::HomePageType Class

The [HomePageType](attica-homepagetype.md) class contains information about one home page type. [More...](#details)

- **Header:** `#include <Attica/HomePageType>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS Attica)`  
  `target_link_libraries(mytarget PRIVATE KF6::Attica)`

[List of all members, including inherited members](attica-homepagetype-members.md)

## Public Types

- [HomePageType::List](#List-typedef)

## Public Functions

- [HomePageType()](#HomePageType)
- [uint id() const](#id)
- [QString name() const](#name)
- [void setId(uint id)](#setId)
- [void setName(const QString &name)](#setName)

## Detailed Description {#details}

It consists of an integer id and a home page type name.

## Member Type Documentation {#member-type-documentation}

### HomePageType::List {#List-typedef}

## Member Function Documentation {#member-function-documentation}

### HomePageType::HomePageType() {#HomePageType}

Creates an empty [HomePageType](attica-homepagetype.md)

### uint HomePageType::id() const {#id}

*See also* [setId](attica-homepagetype.md#setId)()

### QString HomePageType::name() const {#name}

*See also* [setName](attica-homepagetype.md#setName)()

### void HomePageType::setId(uint *id*) {#setId}

*See also* [id](attica-homepagetype.md#id)()

### void HomePageType::setName(const QString &*name*) {#setName}

*See also* [name](attica-homepagetype.md#name)()
