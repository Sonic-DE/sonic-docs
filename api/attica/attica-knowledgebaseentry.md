---
title: "Attica::KnowledgeBaseEntry Class"
description: "Represents a knowledge base entry."
---

# Attica::KnowledgeBaseEntry Class

Represents a knowledge base entry. [More...](#details)

- **Header:** `#include <Attica/KnowledgeBaseEntry>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS Attica)`  
  `target_link_libraries(mytarget PRIVATE KF6::Attica)`

[List of all members, including inherited members](attica-knowledgebaseentry-members.md)

## Public Types

- [KnowledgeBaseEntry::List](#List-typedef)

## Public Functions

- [KnowledgeBaseEntry()](#KnowledgeBaseEntry)
- [void addExtendedAttribute(const QString &key, const QString &value)](#addExtendedAttribute)
- [QString answer() const](#answer)
- [QDateTime changed() const](#changed)
- [int comments() const](#comments)
- [int contentId() const](#contentId)
- [QString description() const](#description)
- [QUrl detailPage() const](#detailPage)
- [QString extendedAttribute(const QString &key) const](#extendedAttribute)
- [QMap\<QString, QString\> extendedAttributes() const](#extendedAttributes)
- [QString id() const](#id)
- [bool isValid() const](#isValid)
- [QString name() const](#name)
- [void setAnswer(const QString &answer)](#setAnswer)
- [void setChanged(const QDateTime &changed)](#setChanged)
- [void setComments(int comments)](#setComments)
- [void setContentId(int id)](#setContentId)
- [void setDescription(const QString &description)](#setDescription)
- [void setDetailPage(const QUrl &detailPage)](#setDetailPage)
- [void setId(QString id)](#setId)
- [void setName(const QString &name)](#setName)
- [void setStatus(const QString &status)](#setStatus)
- [void setUser(const QString &user)](#setUser)
- [QString status() const](#status)
- [QString user() const](#user)

## Detailed Description {#details}

## Member Type Documentation {#member-type-documentation}

### KnowledgeBaseEntry::List {#List-typedef}

## Member Function Documentation {#member-function-documentation}

### KnowledgeBaseEntry::KnowledgeBaseEntry() {#KnowledgeBaseEntry}

### void KnowledgeBaseEntry::addExtendedAttribute(const QString &*key*, const QString &*value*) {#addExtendedAttribute}

### QString KnowledgeBaseEntry::answer() const {#answer}

*See also* [setAnswer](attica-knowledgebaseentry.md#setAnswer)()

### QDateTime KnowledgeBaseEntry::changed() const {#changed}

*See also* [setChanged](attica-knowledgebaseentry.md#setChanged)()

### int KnowledgeBaseEntry::comments() const {#comments}

*See also* [setComments](attica-knowledgebaseentry.md#setComments)()

### int KnowledgeBaseEntry::contentId() const {#contentId}

*See also* [setContentId](attica-knowledgebaseentry.md#setContentId)()

### QString KnowledgeBaseEntry::description() const {#description}

*See also* [setDescription](attica-knowledgebaseentry.md#setDescription)()

### QUrl KnowledgeBaseEntry::detailPage() const {#detailPage}

*See also* [setDetailPage](attica-knowledgebaseentry.md#setDetailPage)()

### QString KnowledgeBaseEntry::extendedAttribute(const QString &*key*) const {#extendedAttribute}

### QMap\<QString, QString\> KnowledgeBaseEntry::extendedAttributes() const {#extendedAttributes}

### QString KnowledgeBaseEntry::id() const {#id}

*See also* [setId](attica-knowledgebaseentry.md#setId)()

### bool KnowledgeBaseEntry::isValid() const {#isValid}

### QString KnowledgeBaseEntry::name() const {#name}

*See also* [setName](attica-knowledgebaseentry.md#setName)()

### void KnowledgeBaseEntry::setAnswer(const QString &*answer*) {#setAnswer}

*See also* [answer](attica-knowledgebaseentry.md#answer)()

### void KnowledgeBaseEntry::setChanged(const QDateTime &*changed*) {#setChanged}

*See also* [changed](attica-knowledgebaseentry.md#changed)()

### void KnowledgeBaseEntry::setComments(int *comments*) {#setComments}

*See also* [comments](attica-knowledgebaseentry.md#comments)()

### void KnowledgeBaseEntry::setContentId(int *id*) {#setContentId}

*See also* [contentId](attica-knowledgebaseentry.md#contentId)()

### void KnowledgeBaseEntry::setDescription(const QString &*description*) {#setDescription}

*See also* [description](attica-knowledgebaseentry.md#description)()

### void KnowledgeBaseEntry::setDetailPage(const QUrl &*detailPage*) {#setDetailPage}

*See also* [detailPage](attica-knowledgebaseentry.md#detailPage)()

### void KnowledgeBaseEntry::setId(QString *id*) {#setId}

*See also* [id](attica-knowledgebaseentry.md#id)()

### void KnowledgeBaseEntry::setName(const QString &*name*) {#setName}

*See also* [name](attica-knowledgebaseentry.md#name)()

### void KnowledgeBaseEntry::setStatus(const QString &*status*) {#setStatus}

*See also* [status](attica-knowledgebaseentry.md#status)()

### void KnowledgeBaseEntry::setUser(const QString &*user*) {#setUser}

*See also* [user](attica-knowledgebaseentry.md#user)()

### QString KnowledgeBaseEntry::status() const {#status}

*See also* [setStatus](attica-knowledgebaseentry.md#setStatus)()

### QString KnowledgeBaseEntry::user() const {#user}

*See also* [setUser](attica-knowledgebaseentry.md#setUser)()
