---
title: "KIO::WorkerResult Class"
description: "The result of a worker call."
---

# KIO::WorkerResult Class

The result of a worker call. [More...](#details)

- **Header:** `#include <KIO/WorkerBase>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS KIO)`  
  `target_link_libraries(mytarget PRIVATE KF6::KIOCore)`

[List of all members, including inherited members](kio-workerresult-members.md)

## Public Functions

- [int error() const](#error)
- [QString errorString() const](#errorString)
- [bool success() const](#success)

## Static Public Members

- [KIO::WorkerResult fail(int \_error = KIO::ERR\_UNKNOWN, const QString &\_errorString = QString())](#fail)
- [KIO::WorkerResult pass()](#pass)

## Detailed Description {#details}

When using the Result type always mark the function Q\_REQUIRED\_RESULT to enforce handling of the Result.

## Member Function Documentation {#member-function-documentation}

### int WorkerResult::error() const {#error}

The error code (or ERR\_UNKNOWN) of the result.

### QString WorkerResult::errorString() const {#errorString}

The localized error description if applicable.

### \[static\] KIO::WorkerResult WorkerResult::fail(int *\_error* = KIO::ERR\_UNKNOWN, const QString &*\_errorString* = QString()) {#fail}

Constructs a failure results.

### \[static\] KIO::WorkerResult WorkerResult::pass() {#pass}

Constructs a success result.

### bool WorkerResult::success() const {#success}

Whether or not the result was a success.
