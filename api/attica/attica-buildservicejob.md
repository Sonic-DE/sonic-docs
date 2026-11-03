---
title: "Attica::BuildServiceJob Class"
description: "Represents a build service job."
---

# Attica::BuildServiceJob Class

Represents a build service job. [More...](#details)

- **Header:** `#include <Attica/BuildServiceJob>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS Attica)`  
  `target_link_libraries(mytarget PRIVATE KF6::Attica)`

[List of all members, including inherited members](attica-buildservicejob-members.md)

## Public Types

- [BuildServiceJob::List](#List-typedef)

## Public Functions

- [BuildServiceJob()](#BuildServiceJob)
- [QString buildServiceId() const](#buildServiceId)
- [QString id() const](#id)
- [bool isCompleted() const](#isCompleted)
- [bool isFailed() const](#isFailed)
- [bool isRunning() const](#isRunning)
- [bool isValid() const](#isValid)
- [QString message() const](#message)
- [QString name() const](#name)
- [qreal progress() const](#progress)
- [QString projectId() const](#projectId)
- [void setBuildServiceId(const QString &)](#setBuildServiceId)
- [void setId(const QString &)](#setId)
- [void setMessage(const QString &)](#setMessage)
- [void setName(const QString &)](#setName)
- [void setProgress(const qreal)](#setProgress)
- [void setProjectId(const QString &)](#setProjectId)
- [void setStatus(const int)](#setStatus)
- [void setTarget(const QString &)](#setTarget)
- [void setUrl(const QString &)](#setUrl)
- [QString target() const](#target)
- [QString url() const](#url)

## Detailed Description {#details}

## Member Type Documentation {#member-type-documentation}

### BuildServiceJob::List {#List-typedef}

## Member Function Documentation {#member-function-documentation}

### BuildServiceJob::BuildServiceJob() {#BuildServiceJob}

### QString BuildServiceJob::buildServiceId() const {#buildServiceId}

*See also* [setBuildServiceId](attica-buildservicejob.md#setBuildServiceId)()

### QString BuildServiceJob::id() const {#id}

*See also* [setId](attica-buildservicejob.md#setId)()

### bool BuildServiceJob::isCompleted() const {#isCompleted}

### bool BuildServiceJob::isFailed() const {#isFailed}

### bool BuildServiceJob::isRunning() const {#isRunning}

### bool BuildServiceJob::isValid() const {#isValid}

### QString BuildServiceJob::message() const {#message}

*See also* [setMessage](attica-buildservicejob.md#setMessage)()

### QString BuildServiceJob::name() const {#name}

*See also* [setName](attica-buildservicejob.md#setName)()

### qreal BuildServiceJob::progress() const {#progress}

*See also* [setProgress](attica-buildservicejob.md#setProgress)()

### QString BuildServiceJob::projectId() const {#projectId}

*See also* [setProjectId](attica-buildservicejob.md#setProjectId)()

### void BuildServiceJob::setBuildServiceId(*const QString &*) {#setBuildServiceId}

*See also* [buildServiceId](attica-buildservicejob.md#buildServiceId)()

### void BuildServiceJob::setId(*const QString &*) {#setId}

*See also* [id](attica-buildservicejob.md#id)()

### void BuildServiceJob::setMessage(*const QString &*) {#setMessage}

*See also* [message](attica-buildservicejob.md#message)()

### void BuildServiceJob::setName(*const QString &*) {#setName}

*See also* [name](attica-buildservicejob.md#name)()

### void BuildServiceJob::setProgress(*const qreal*) {#setProgress}

*See also* [progress](attica-buildservicejob.md#progress)()

### void BuildServiceJob::setProjectId(*const QString &*) {#setProjectId}

*See also* [projectId](attica-buildservicejob.md#projectId)()

### void BuildServiceJob::setStatus(*const int*) {#setStatus}

### void BuildServiceJob::setTarget(*const QString &*) {#setTarget}

*See also* [target](attica-buildservicejob.md#target)()

### void BuildServiceJob::setUrl(*const QString &*) {#setUrl}

*See also* [url](attica-buildservicejob.md#url)()

### QString BuildServiceJob::target() const {#target}

*See also* [setTarget](attica-buildservicejob.md#setTarget)()

### QString BuildServiceJob::url() const {#url}

*See also* [setUrl](attica-buildservicejob.md#setUrl)()
