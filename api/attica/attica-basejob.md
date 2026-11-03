---
title: "Attica::BaseJob Class"
description: "The baseclass for all job classes."
---

# Attica::BaseJob Class

The baseclass for all job classes. [More...](#details)

- **Header:** `#include <attica/atticabasejob.h>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS Attica)`  
  `target_link_libraries(mytarget PRIVATE KF6::Attica)`
- **Inherits:** [QObject](https://doc.qt.io/qt-6/qobject.html)
- **Inherited By:** [Attica::DeleteJob](attica-deletejob.md), [Attica::GetJob](attica-getjob.md), [Attica::PostJob](attica-postjob.md), and [Attica::PutJob](attica-putjob.md)

[List of all members, including inherited members](attica-basejob-members.md)

## Public Types

- [enum BaseJob::NetworkRequestCustomAttributes](#NetworkRequestCustomAttributes-enum)

## Public Functions

- [bool isAborted() const](#isAborted)
- [Attica::Metadata metadata() const](#metadata)

## Public Slots

- [void abort()](#abort)
- [void dataFinished()](#dataFinished)
- [void start()](#start)

## Protected Functions

- [QNetworkReply \*executeRequest()](#executeRequest)
- [Attica::PlatformDependent \*internals()](#internals)
- [void parse(const QString &xml)](#parse)
- [void setError(int errorCode)](#setError)
- [void setMetadata(const Attica::Metadata &data) const](#setMetadata)

## Detailed Description {#details}

## Member Type Documentation {#member-type-documentation}

### enum BaseJob::NetworkRequestCustomAttributes {#NetworkRequestCustomAttributes-enum}

UserAttribute

PasswordAttribute

## Member Function Documentation {#member-function-documentation}

### \[slot\] void BaseJob::abort() {#abort}

### \[protected slot\] void BaseJob::dataFinished() {#dataFinished}

### \[pure virtual protected\] QNetworkReply \*BaseJob::executeRequest() {#executeRequest}

### \[protected\] Attica::PlatformDependent \*BaseJob::internals() {#internals}

### bool BaseJob::isAborted() const {#isAborted}

Returns whether [abort](attica-basejob.md#abort)() has been called on the job

### Attica::Metadata BaseJob::metadata() const {#metadata}

*See also* [setMetadata](attica-basejob.md#setMetadata)()

### \[pure virtual protected\] void BaseJob::parse(const QString &*xml*) {#parse}

### \[protected\] void BaseJob::setError(int *errorCode*) {#setError}

### \[protected\] void BaseJob::setMetadata(const Attica::Metadata &*data*) const {#setMetadata}

*See also* [metadata](attica-basejob.md#metadata)()

### \[slot\] void BaseJob::start() {#start}
