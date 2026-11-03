---
title: "Baloo::QueryRunnable Class"
description: "File indexing."
---

# Baloo::QueryRunnable Class

File indexing. [More...](#details)

- **Header:** `#include <Baloo/QueryRunnable>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS Baloo)`  
  `target_link_libraries(mytarget PRIVATE KF6::Baloo)`
- **Inherits:** [QObject](https://doc.qt.io/qt-6/qobject.html) and [QRunnable](https://doc.qt.io/qt-6/qrunnable.html)

[List of all members, including inherited members](baloo-queryrunnable-members.md)

## Public Functions

- [QueryRunnable(const Baloo::Query &query, QObject \*parent = nullptr)](#QueryRunnable)
- [void stop()](#stop)

## Signals

- [void finished(Baloo::QueryRunnable \*queryRunnable)](#finished)
- [void queryResult(Baloo::QueryRunnable \*queryRunnable, const QString &filePath)](#queryResult)

## Detailed Description {#details}

## Member Function Documentation {#member-function-documentation}

### QueryRunnable::QueryRunnable(const Baloo::Query &*query*, QObject \**parent* = nullptr) {#QueryRunnable}

### \[signal\] void QueryRunnable::finished(Baloo::QueryRunnable \**queryRunnable*) {#finished}

### \[signal\] void QueryRunnable::queryResult(Baloo::QueryRunnable \**queryRunnable*, const QString &*filePath*) {#queryResult}

### void QueryRunnable::stop() {#stop}
