---
title: "Attica::Activity Class"
description: "Represents a single news item (also known as activity)."
---

# Attica::Activity Class

Represents a single news item (also known as activity). [More...](#details)

- **Header:** `#include <Attica/Activity>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS Attica)`  
  `target_link_libraries(mytarget PRIVATE KF6::Attica)`

[List of all members, including inherited members](attica-activity-members.md)

## Public Types

- [Activity::List](#List-typedef)

## Public Functions

- [Activity()](#Activity)
- [Attica::Person associatedPerson() const](#associatedPerson)
- [QString id() const](#id)
- [bool isValid() const](#isValid)
- [QUrl link() const](#link)
- [QString message() const](#message)
- [void setAssociatedPerson(const Attica::Person &associatedPerson)](#setAssociatedPerson)
- [void setId(const QString &id)](#setId)
- [void setLink(const QUrl &link)](#setLink)
- [void setMessage(const QString &message)](#setMessage)
- [void setTimestamp(const QDateTime &timestamp)](#setTimestamp)
- [QDateTime timestamp() const](#timestamp)

## Detailed Description {#details}

## Member Type Documentation {#member-type-documentation}

### Activity::List {#List-typedef}

## Member Function Documentation {#member-function-documentation}

### Activity::Activity() {#Activity}

Creates an empty Activity

### Attica::Person Activity::associatedPerson() const {#associatedPerson}

Returns the user bound to the Activity.

*See also* [setAssociatedPerson](attica-activity.md#setAssociatedPerson)()

### QString Activity::id() const {#id}

Gets the id of the Activity.

The id uniquely identifies an Activity with the OCS API.

Returns the id

*See also* [setId](attica-activity.md#setId)()

### bool Activity::isValid() const {#isValid}

Checks whether this Activity has an id Returns `true` if an id has been set, `false` otherwise

### QUrl Activity::link() const {#link}

Returns the link to further information about this Activity.

*See also* [setLink](attica-activity.md#setLink)()

### QString Activity::message() const {#message}

Returns the message of the Activity.

*See also* [setMessage](attica-activity.md#setMessage)()

### void Activity::setAssociatedPerson(const Attica::Person &*associatedPerson*) {#setAssociatedPerson}

Sets the user bound to the Activity.

`id` the new user

*See also* [associatedPerson](attica-activity.md#associatedPerson)()

### void Activity::setId(const QString &*id*) {#setId}

Sets the id of the Activity.

The id uniquely identifies an Activity with the OCS API.

`id` the new id

*See also* [id](attica-activity.md#id)()

### void Activity::setLink(const QUrl &*link*) {#setLink}

Sets the link to further information about this Activity.

`link` the new link

*See also* [link](attica-activity.md#link)()

### void Activity::setMessage(const QString &*message*) {#setMessage}

Sets the message of the Activity.

`message` the new message

*See also* [message](attica-activity.md#message)()

### void Activity::setTimestamp(const QDateTime &*timestamp*) {#setTimestamp}

Sets the timestamp the Activity has been published.

`timestamp` the new timestamp

*See also* [timestamp](attica-activity.md#timestamp)()

### QDateTime Activity::timestamp() const {#timestamp}

Returns the timestamp the Activity has been published.

*See also* [setTimestamp](attica-activity.md#setTimestamp)()
