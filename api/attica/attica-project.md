---
title: "Attica::Project Class"
description: "Represents a project."
---

# Attica::Project Class

Represents a project. [More...](#details)

- **Header:** `#include <Attica/Project>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS Attica)`  
  `target_link_libraries(mytarget PRIVATE KF6::Attica)`

[List of all members, including inherited members](attica-project-members.md)

## Public Types

- [Project::List](#List-typedef)

## Public Functions

- [Project()](#Project)
- [void addExtendedAttribute(const QString &key, const QString &value)](#addExtendedAttribute)
- [QString description() const](#description)
- [QStringList developers() const](#developers)
- [QString extendedAttribute(const QString &key) const](#extendedAttribute)
- [QMap\<QString, QString\> extendedAttributes() const](#extendedAttributes)
- [QString id() const](#id)
- [bool isValid() const](#isValid)
- [QString license() const](#license)
- [QString name() const](#name)
- [QString requirements() const](#requirements)
- [void setDescription(const QString &)](#setDescription)
- [void setDevelopers(const QStringList &)](#setDevelopers)
- [void setId(const QString &)](#setId)
- [void setLicense(const QString &)](#setLicense)
- [void setName(const QString &)](#setName)
- [void setRequirements(const QString &)](#setRequirements)
- [void setSpecFile(const QString &)](#setSpecFile)
- [void setSummary(const QString &)](#setSummary)
- [void setUrl(const QString &)](#setUrl)
- [void setVersion(const QString &)](#setVersion)
- [QString specFile() const](#specFile)
- [QString summary() const](#summary)
- [QString url() const](#url)
- [QString version() const](#version)

## Detailed Description {#details}

## Member Type Documentation {#member-type-documentation}

### Project::List {#List-typedef}

## Member Function Documentation {#member-function-documentation}

### Project::Project() {#Project}

### void Project::addExtendedAttribute(const QString &*key*, const QString &*value*) {#addExtendedAttribute}

### QString Project::description() const {#description}

*See also* [setDescription](attica-project.md#setDescription)()

### QStringList Project::developers() const {#developers}

*See also* [setDevelopers](attica-project.md#setDevelopers)()

### QString Project::extendedAttribute(const QString &*key*) const {#extendedAttribute}

### QMap\<QString, QString\> Project::extendedAttributes() const {#extendedAttributes}

### QString Project::id() const {#id}

*See also* [setId](attica-project.md#setId)()

### bool Project::isValid() const {#isValid}

### QString Project::license() const {#license}

*See also* [setLicense](attica-project.md#setLicense)()

### QString Project::name() const {#name}

*See also* [setName](attica-project.md#setName)()

### QString Project::requirements() const {#requirements}

*See also* [setRequirements](attica-project.md#setRequirements)()

### void Project::setDescription(*const QString &*) {#setDescription}

*See also* [description](attica-project.md#description)()

### void Project::setDevelopers(*const QStringList &*) {#setDevelopers}

*See also* [developers](attica-project.md#developers)()

### void Project::setId(*const QString &*) {#setId}

*See also* [id](attica-project.md#id)()

### void Project::setLicense(*const QString &*) {#setLicense}

*See also* [license](attica-project.md#license)()

### void Project::setName(*const QString &*) {#setName}

*See also* [name](attica-project.md#name)()

### void Project::setRequirements(*const QString &*) {#setRequirements}

*See also* [requirements](attica-project.md#requirements)()

### void Project::setSpecFile(*const QString &*) {#setSpecFile}

*See also* [specFile](attica-project.md#specFile)()

### void Project::setSummary(*const QString &*) {#setSummary}

*See also* [summary](attica-project.md#summary)()

### void Project::setUrl(*const QString &*) {#setUrl}

*See also* [url](attica-project.md#url)()

### void Project::setVersion(*const QString &*) {#setVersion}

*See also* [version](attica-project.md#version)()

### QString Project::specFile() const {#specFile}

*See also* [setSpecFile](attica-project.md#setSpecFile)()

### QString Project::summary() const {#summary}

*See also* [setSummary](attica-project.md#setSummary)()

### QString Project::url() const {#url}

*See also* [setUrl](attica-project.md#setUrl)()

### QString Project::version() const {#version}

*See also* [setVersion](attica-project.md#setVersion)()
