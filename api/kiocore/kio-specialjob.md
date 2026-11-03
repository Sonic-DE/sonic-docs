---
title: "KIO::SpecialJob Class"
description: "A class that sends a special command to a KIO worker."
---

# KIO::SpecialJob Class

A class that sends a special command to a KIO worker. [More...](#details)

- **Header:** `#include <KIO/SpecialJob>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS KIO)`  
  `target_link_libraries(mytarget PRIVATE KF6::KIOCore)`
- **Inherits:** [KIO::TransferJob](kio-transferjob.md)

[List of all members, including inherited members](kio-specialjob-members.md)

## Public Functions

- [SpecialJob(const QUrl &url, const QByteArray &data = QByteArray())](#SpecialJob)
- [QByteArray arguments() const](#arguments)
- [void setArguments(const QByteArray &data)](#setArguments)

## Detailed Description {#details}

This allows you to send a binary blob to a worker and handle its responses. The worker will receive the binary data as an argument to the "special" function (inherited from [WorkerBase::special](kio-workerbase.md#special)()).

Use this only on KIO workers that belong to your application. Sending special commands to other workers may cause unexpected behaviour.

*See also* [KIO::special](kio-index.md)

## Member Function Documentation {#member-function-documentation}

### \[explicit\] SpecialJob::SpecialJob(const QUrl &*url*, const QByteArray &*data* = QByteArray()) {#SpecialJob}

Creates a [KIO::SpecialJob](kio-specialjob.md).

`url` the URL to be passed to the worker

`data` the data to be sent to the [WorkerBase::special](kio-workerbase.md#special)() function.

### QByteArray SpecialJob::arguments() const {#arguments}

Returns the [QByteArray](https://doc.qt.io/qt-6/qbytearray.html) data that will be sent (or has been sent) to the worker.

*See also* [setArguments](kio-specialjob.md#setArguments)()

### void SpecialJob::setArguments(const QByteArray &*data*) {#setArguments}

Sets the [QByteArray](https://doc.qt.io/qt-6/qbytearray.html) that is passed to [WorkerBase::special](kio-workerbase.md#special)() on the worker.

*See also* [arguments](kio-specialjob.md#arguments)()
