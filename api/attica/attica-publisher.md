---
title: "Attica::Publisher Class"
description: "Represents a publisher."
---

# Attica::Publisher Class

Represents a publisher. [More...](#details)

- **Header:** `#include <Attica/Publisher>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS Attica)`  
  `target_link_libraries(mytarget PRIVATE KF6::Attica)`

[List of all members, including inherited members](attica-publisher-members.md)

## Public Types

- [Publisher::List](#List-typedef)

## Public Functions

- [Publisher()](#Publisher)
- [void addField(const Attica::Field &)](#addField)
- [void addTarget(const Attica::Target &)](#addTarget)
- [QList\<Attica::Field\> fields() const](#fields)
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

### Publisher::List {#List-typedef}

## Member Function Documentation {#member-function-documentation}

### Publisher::Publisher() {#Publisher}

### void Publisher::addField(*const Attica::Field &*) {#addField}

### void Publisher::addTarget(*const Attica::Target &*) {#addTarget}

### QList\<Attica::Field\> Publisher::fields() const {#fields}

### QString Publisher::id() const {#id}

*See also* [setId](attica-publisher.md#setId)()

### bool Publisher::isValid() const {#isValid}

### QString Publisher::name() const {#name}

*See also* [setName](attica-publisher.md#setName)()

### void Publisher::setId(*const QString &*) {#setId}

*See also* [id](attica-publisher.md#id)()

### void Publisher::setName(*const QString &*) {#setName}

*See also* [name](attica-publisher.md#name)()

### void Publisher::setUrl(*const QString &*) {#setUrl}

*See also* [url](attica-publisher.md#url)()

### QList\<Attica::Target\> Publisher::targets() const {#targets}

### QString Publisher::url() const {#url}

*See also* [setUrl](attica-publisher.md#setUrl)()
