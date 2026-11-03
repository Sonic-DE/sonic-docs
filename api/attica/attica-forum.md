---
title: "Attica::Forum Class"
description: "Represents a forum."
---

# Attica::Forum Class

Represents a forum. [More...](#details)

- **Header:** `#include <Attica/Forum>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS Attica)`  
  `target_link_libraries(mytarget PRIVATE KF6::Attica)`

[List of all members, including inherited members](attica-forum-members.md)

## Public Types

- [Forum::List](#List-typedef)

## Public Functions

- [Forum()](#Forum)
- [int childCount() const](#childCount)
- [QList\<Attica::Forum\> children() const](#children)
- [QDateTime date() const](#date)
- [QString description() const](#description)
- [QUrl icon() const](#icon)
- [QString id() const](#id)
- [bool isValid() const](#isValid)
- [QString name() const](#name)
- [void setChildCount(const int childCount)](#setChildCount)
- [void setChildren(QList\<Attica::Forum\> comments)](#setChildren)
- [void setDate(const QDateTime &date)](#setDate)
- [void setDescription(const QString &description)](#setDescription)
- [void setIcon(const QUrl &icon)](#setIcon)
- [void setId(const QString &id)](#setId)
- [void setName(const QString &name)](#setName)
- [void setTopics(const int topics)](#setTopics)
- [int topics() const](#topics)

## Detailed Description {#details}

## Member Type Documentation {#member-type-documentation}

### Forum::List {#List-typedef}

## Member Function Documentation {#member-function-documentation}

### Forum::Forum() {#Forum}

### int Forum::childCount() const {#childCount}

*See also* [setChildCount](attica-forum.md#setChildCount)()

### QList\<Attica::Forum\> Forum::children() const {#children}

*See also* [setChildren](attica-forum.md#setChildren)()

### QDateTime Forum::date() const {#date}

*See also* [setDate](attica-forum.md#setDate)()

### QString Forum::description() const {#description}

*See also* [setDescription](attica-forum.md#setDescription)()

### QUrl Forum::icon() const {#icon}

*See also* [setIcon](attica-forum.md#setIcon)()

### QString Forum::id() const {#id}

*See also* [setId](attica-forum.md#setId)()

### bool Forum::isValid() const {#isValid}

### QString Forum::name() const {#name}

*See also* [setName](attica-forum.md#setName)()

### void Forum::setChildCount(const int *childCount*) {#setChildCount}

*See also* [childCount](attica-forum.md#childCount)()

### void Forum::setChildren(QList\<Attica::Forum\> *comments*) {#setChildren}

*See also* [children](attica-forum.md#children)()

### void Forum::setDate(const QDateTime &*date*) {#setDate}

*See also* [date](attica-forum.md#date)()

### void Forum::setDescription(const QString &*description*) {#setDescription}

*See also* [description](attica-forum.md#description)()

### void Forum::setIcon(const QUrl &*icon*) {#setIcon}

*See also* [icon](attica-forum.md#icon)()

### void Forum::setId(const QString &*id*) {#setId}

*See also* [id](attica-forum.md#id)()

### void Forum::setName(const QString &*name*) {#setName}

*See also* [name](attica-forum.md#name)()

### void Forum::setTopics(const int *topics*) {#setTopics}

*See also* [topics](attica-forum.md#topics)()

### int Forum::topics() const {#topics}

*See also* [setTopics](attica-forum.md#setTopics)()
