---
title: "Attica::Distribution Class"
description: "The Distribution class contains information about one distribution that the server offers."
---

# Attica::Distribution Class

The Distribution class contains information about one distribution that the server offers. [More...](#details)

- **Header:** `#include <Attica/Distribution>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS Attica)`  
  `target_link_libraries(mytarget PRIVATE KF6::Attica)`

[List of all members, including inherited members](attica-distribution-members.md)

## Public Types

- [Distribution::List](#List-typedef)

## Public Functions

- [Distribution()](#Distribution)
- [uint id() const](#id)
- [QString name() const](#name)
- [void setId(uint id)](#setId)
- [void setName(const QString &name)](#setName)

## Detailed Description {#details}

It consists of an integer id and a distribution name.

## Member Type Documentation {#member-type-documentation}

### Distribution::List {#List-typedef}

## Member Function Documentation {#member-function-documentation}

### Distribution::Distribution() {#Distribution}

Creates an empty Distribution

### uint Distribution::id() const {#id}

*See also* [setId](attica-distribution.md#setId)()

### QString Distribution::name() const {#name}

*See also* [setName](attica-distribution.md#setName)()

### void Distribution::setId(uint *id*) {#setId}

*See also* [id](attica-distribution.md#id)()

### void Distribution::setName(const QString &*name*) {#setName}

*See also* [name](attica-distribution.md#name)()
