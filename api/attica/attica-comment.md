---
title: "Attica::Comment Class"
description: "Represents a comment."
---

# Attica::Comment Class

Represents a comment. [More...](#details)

- **Header:** `#include <Attica/Comment>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS Attica)`  
  `target_link_libraries(mytarget PRIVATE KF6::Attica)`

[List of all members, including inherited members](attica-comment-members.md)

## Public Types

- [Comment::List](#List-typedef)
- [enum Comment::Type](#Type-enum)

## Public Functions

- [Comment()](#Comment)
- [int childCount() const](#childCount)
- [QList\<Attica::Comment\> children() const](#children)
- [QDateTime date() const](#date)
- [QString id() const](#id)
- [bool isValid() const](#isValid)
- [int score() const](#score)
- [void setChildCount(const int childCount)](#setChildCount)
- [void setChildren(QList\<Attica::Comment\> comments)](#setChildren)
- [void setDate(const QDateTime &date)](#setDate)
- [void setId(const QString &id)](#setId)
- [void setScore(const int score)](#setScore)
- [void setSubject(const QString &subject)](#setSubject)
- [void setText(const QString &text)](#setText)
- [void setUser(const QString &user)](#setUser)
- [QString subject() const](#subject)
- [QString text() const](#text)
- [QString user() const](#user)

## Static Public Members

- [QString commentTypeToString(const Attica::Comment::Type type)](#commentTypeToString)

## Detailed Description {#details}

## Member Type Documentation {#member-type-documentation}

### Comment::List {#List-typedef}

### enum Comment::Type {#Type-enum}

| Constant |   |
| --- | --- |
| `Attica::Comment::ContentComment` | `0` |
| `Attica::Comment::ForumComment` | `1` |
| `Attica::Comment::KnowledgeBaseComment` | `2` |
| `Attica::Comment::EventComment` | `3` |

## Member Function Documentation {#member-function-documentation}

### Comment::Comment() {#Comment}

### int Comment::childCount() const {#childCount}

*See also* [setChildCount](attica-comment.md#setChildCount)()

### QList\<Attica::Comment\> Comment::children() const {#children}

*See also* [setChildren](attica-comment.md#setChildren)()

### \[static\] QString Comment::commentTypeToString(const Attica::Comment::Type *type*) {#commentTypeToString}

### QDateTime Comment::date() const {#date}

*See also* [setDate](attica-comment.md#setDate)()

### QString Comment::id() const {#id}

*See also* [setId](attica-comment.md#setId)()

### bool Comment::isValid() const {#isValid}

### int Comment::score() const {#score}

Returns score of this comment.

`score` average comment score in scale from 0 to 100

*See also* [setScore](attica-comment.md#setScore)()

### void Comment::setChildCount(const int *childCount*) {#setChildCount}

*See also* [childCount](attica-comment.md#childCount)()

### void Comment::setChildren(QList\<Attica::Comment\> *comments*) {#setChildren}

*See also* [children](attica-comment.md#children)()

### void Comment::setDate(const QDateTime &*date*) {#setDate}

*See also* [date](attica-comment.md#date)()

### void Comment::setId(const QString &*id*) {#setId}

*See also* [id](attica-comment.md#id)()

### void Comment::setScore(const int *score*) {#setScore}

This is for internal usage, see Provider::setCommentScore to set scores in comments.

`score` average comment score in scale from 0 to 100

*See also* [score](attica-comment.md#score)()

### void Comment::setSubject(const QString &*subject*) {#setSubject}

*See also* [subject](attica-comment.md#subject)()

### void Comment::setText(const QString &*text*) {#setText}

*See also* [text](attica-comment.md#text)()

### void Comment::setUser(const QString &*user*) {#setUser}

*See also* [user](attica-comment.md#user)()

### QString Comment::subject() const {#subject}

*See also* [setSubject](attica-comment.md#setSubject)()

### QString Comment::text() const {#text}

*See also* [setText](attica-comment.md#setText)()

### QString Comment::user() const {#user}

*See also* [setUser](attica-comment.md#setUser)()
