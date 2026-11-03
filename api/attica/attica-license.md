---
title: "Attica::License Class"
description: "The License class contains information about one license that the server offers."
---

# Attica::License Class

The License class contains information about one license that the server offers. [More...](#details)

- **Header:** `#include <Attica/License>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS Attica)`  
  `target_link_libraries(mytarget PRIVATE KF6::Attica)`

[List of all members, including inherited members](attica-license-members.md)

## Public Types

- [License::List](#List-typedef)

## Public Functions

- [License()](#License)
- [uint id() const](#id)
- [QString name() const](#name)
- [void setId(uint id)](#setId)
- [void setName(const QString &name)](#setName)
- [void setUrl(const QUrl &url)](#setUrl)
- [QUrl url() const](#url)

## Detailed Description {#details}

It consists of an integer id, a name and a link to a webpage describing the license.

## Member Type Documentation {#member-type-documentation}

### License::List {#List-typedef}

## Member Function Documentation {#member-function-documentation}

### License::License() {#License}

Creates an empty License

### uint License::id() const {#id}

*See also* [setId](attica-license.md#setId)()

### QString License::name() const {#name}

*See also* [setName](attica-license.md#setName)()

### void License::setId(uint *id*) {#setId}

*See also* [id](attica-license.md#id)()

### void License::setName(const QString &*name*) {#setName}

*See also* [name](attica-license.md#name)()

### void License::setUrl(const QUrl &*url*) {#setUrl}

*See also* [url](attica-license.md#url)()

### QUrl License::url() const {#url}

*See also* [setUrl](attica-license.md#setUrl)()
