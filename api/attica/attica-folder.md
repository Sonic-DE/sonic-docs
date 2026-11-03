---
title: "Attica::Folder Class"
description: "Represents a single mail folder."
---

# Attica::Folder Class

Represents a single mail folder. [More...](#details)

- **Header:** `#include <Attica/Folder>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS Attica)`  
  `target_link_libraries(mytarget PRIVATE KF6::Attica)`

[List of all members, including inherited members](attica-folder-members.md)

## Public Types

- [Folder::List](#List-typedef)

## Public Functions

- [Folder()](#Folder)
- [QString id() const](#id)
- [bool isValid() const](#isValid)
- [int messageCount() const](#messageCount)
- [QString name() const](#name)
- [void setId(const QString &id)](#setId)
- [void setMessageCount(int messageCount)](#setMessageCount)
- [void setName(const QString &name)](#setName)
- [void setType(const QString &type)](#setType)
- [QString type() const](#type)

## Detailed Description {#details}

## Member Type Documentation {#member-type-documentation}

### Folder::List {#List-typedef}

## Member Function Documentation {#member-function-documentation}

### Folder::Folder() {#Folder}

Creates an empty Folder

### QString Folder::id() const {#id}

Returns the id of the Folder.

The id uniquely identifies a Folder with the OCS API.

*See also* [setId](attica-folder.md#setId)()

### bool Folder::isValid() const {#isValid}

Checks whether this Folder has an id

### int Folder::messageCount() const {#messageCount}

Returns the number of messages in the Folder.

*See also* [setMessageCount](attica-folder.md#setMessageCount)()

### QString Folder::name() const {#name}

Returns the name of the Folder.

*See also* [setName](attica-folder.md#setName)()

### void Folder::setId(const QString &*id*) {#setId}

Sets the id of the Folder.

The id uniquely identifies a Folder with the OCS API.

`id` the new id

*See also* [id](attica-folder.md#id)()

### void Folder::setMessageCount(int *messageCount*) {#setMessageCount}

Sets the number of messages in the Folder.

`messageCount` the new number of messages

*See also* [messageCount](attica-folder.md#messageCount)()

### void Folder::setName(const QString &*name*) {#setName}

Sets the name of the Folder.

`name` the new name

*See also* [name](attica-folder.md#name)()

### void Folder::setType(const QString &*type*) {#setType}

Sets the type of the folder

`type` the new type

*See also* [type](attica-folder.md#type)()

### QString Folder::type() const {#type}

Returns the type of the Folder.

*See also* [setType](attica-folder.md#setType)()
