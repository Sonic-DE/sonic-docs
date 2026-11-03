---
title: "Attica::Message Class"
description: "Represents a message."
---

# Attica::Message Class

Represents a message. [More...](#details)

- **Header:** `#include <Attica/Message>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS Attica)`  
  `target_link_libraries(mytarget PRIVATE KF6::Attica)`

[List of all members, including inherited members](attica-message-members.md)

## Public Types

- [Message::List](#List-typedef)
- [enum Message::Status](#Status-enum)

## Public Functions

- [Message()](#Message)
- [QString body() const](#body)
- [QString from() const](#from)
- [QString id() const](#id)
- [bool isValid() const](#isValid)
- [QDateTime sent() const](#sent)
- [void setBody(const QString &)](#setBody)
- [void setFrom(const QString &)](#setFrom)
- [void setId(const QString &)](#setId)
- [void setSent(const QDateTime &)](#setSent)
- [void setStatus(Attica::Message::Status)](#setStatus)
- [void setSubject(const QString &)](#setSubject)
- [void setTo(const QString &)](#setTo)
- [Attica::Message::Status status() const](#status)
- [QString subject() const](#subject)
- [QString to() const](#to)

## Detailed Description {#details}

## Member Type Documentation {#member-type-documentation}

### Message::List {#List-typedef}

### enum Message::Status {#Status-enum}

| Constant |   |
| --- | --- |
| `Attica::Message::Unread` | `0` |
| `Attica::Message::Read` | `1` |
| `Attica::Message::Answered` | `2` |

## Member Function Documentation {#member-function-documentation}

### Message::Message() {#Message}

### QString Message::body() const {#body}

*See also* [setBody](attica-message.md#setBody)()

### QString Message::from() const {#from}

*See also* [setFrom](attica-message.md#setFrom)()

### QString Message::id() const {#id}

*See also* [setId](attica-message.md#setId)()

### bool Message::isValid() const {#isValid}

### QDateTime Message::sent() const {#sent}

*See also* [setSent](attica-message.md#setSent)()

### void Message::setBody(*const QString &*) {#setBody}

*See also* [body](attica-message.md#body)()

### void Message::setFrom(*const QString &*) {#setFrom}

*See also* [from](attica-message.md#from)()

### void Message::setId(*const QString &*) {#setId}

*See also* [id](attica-message.md#id)()

### void Message::setSent(*const QDateTime &*) {#setSent}

*See also* [sent](attica-message.md#sent)()

### void Message::setStatus(*Attica::Message::Status*) {#setStatus}

*See also* [status](attica-message.md#status)()

### void Message::setSubject(*const QString &*) {#setSubject}

*See also* [subject](attica-message.md#subject)()

### void Message::setTo(*const QString &*) {#setTo}

*See also* [to](attica-message.md#to)()

### Attica::Message::Status Message::status() const {#status}

*See also* [setStatus](attica-message.md#setStatus)()

### QString Message::subject() const {#subject}

*See also* [setSubject](attica-message.md#setSubject)()

### QString Message::to() const {#to}

*See also* [setTo](attica-message.md#setTo)()
