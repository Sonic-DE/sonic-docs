---
title: "Attica::Category Class"
description: "Represents a single content category."
---

# Attica::Category Class

Represents a single content category. [More...](#details)

- **Header:** `#include <Attica/Category>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS Attica)`  
  `target_link_libraries(mytarget PRIVATE KF6::Attica)`

[List of all members, including inherited members](attica-category-members.md)

## Public Types

- [Category::List](#List-typedef)

## Public Functions

- [Category()](#Category)
- [QString displayName() const](#displayName)
- [QString id() const](#id)
- [bool isValid() const](#isValid)
- [QString name() const](#name)
- [void setDisplayName(const QString &name)](#setDisplayName)
- [void setId(const QString &)](#setId)
- [void setName(const QString &name)](#setName)

## Detailed Description {#details}

## Member Type Documentation {#member-type-documentation}

### Category::List {#List-typedef}

## Member Function Documentation {#member-function-documentation}

### Category::Category() {#Category}

Creates an empty Category

### QString Category::displayName() const {#displayName}

Returns the display name of the Category.

This name is guaranteed to be user friendly, while name may be internal for the server

*See also* [setDisplayName](attica-category.md#setDisplayName)()

### QString Category::id() const {#id}

Returns the id of the Category.

The id uniquely identifies a Category with the OCS API.

*See also* [setId](attica-category.md#setId)()

### bool Category::isValid() const {#isValid}

Returns whether this Category has an id

### QString Category::name() const {#name}

Returns the name of the Category.

*See also* [setName](attica-category.md#setName)()

### void Category::setDisplayName(const QString &*name*) {#setDisplayName}

Sets the display name of the Category.

This name is guaranteed to be user friendly, while name may be internal for the server

`name` the new name

*See also* [displayName](attica-category.md#displayName)()

### void Category::setId(*const QString &*) {#setId}

Sets the id of the Category.

The id uniquely identifies a Category with the OCS API.

`id` the new id

*See also* [id](attica-category.md#id)()

### void Category::setName(const QString &*name*) {#setName}

Sets the name of the Category.

`name` the new name

*See also* [name](attica-category.md#name)()
