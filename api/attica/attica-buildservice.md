---
title: "Attica::BuildService Class"
description: "Represents a build service."
---

# Attica::BuildService Class

Represents a build service. [More...](#details)

- **Header:** `#include <Attica/BuildService>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS Attica)`  
  `target_link_libraries(mytarget PRIVATE KF6::Attica)`

[List of all members, including inherited members](attica-buildservice-members.md)

## Public Types

- [BuildService::List](#List-typedef)

## Public Functions

- [BuildService()](#BuildService)
- [void addTarget(const Attica::Target &)](#addTarget)
- [QString id() const](#id)
- [bool isValid() const](#isValid)
- [QString name() const](#name)
- [void setId(const QString &)](#setId)
- [void setName(const QString &)](#setName)
- [void setUrl(const QString &)](#setUrl)
- [QList\<Attica::Target\> targets() const](#targets)
- [QString url() const](#url)

## Detailed Description {#details}

## Member Type Documentation {#member-type-documentation}

### BuildService::List {#List-typedef}

## Member Function Documentation {#member-function-documentation}

### BuildService::BuildService() {#BuildService}

### void BuildService::addTarget(*const Attica::Target &*) {#addTarget}

### QString BuildService::id() const {#id}

*See also* [setId](attica-buildservice.md#setId)()

### bool BuildService::isValid() const {#isValid}

### QString BuildService::name() const {#name}

*See also* [setName](attica-buildservice.md#setName)()

### void BuildService::setId(*const QString &*) {#setId}

*See also* [id](attica-buildservice.md#id)()

### void BuildService::setName(*const QString &*) {#setName}

*See also* [name](attica-buildservice.md#name)()

### void BuildService::setUrl(*const QString &*) {#setUrl}

*See also* [url](attica-buildservice.md#url)()

### QList\<Attica::Target\> BuildService::targets() const {#targets}

### QString BuildService::url() const {#url}

*See also* [setUrl](attica-buildservice.md#setUrl)()
