---
title: "KIO::WorkerConfig Class"
description: "This class manages the configuration for KIO workers based on protocol and host."
---

# KIO::WorkerConfig Class

This class manages the configuration for KIO workers based on protocol and host. [More...](#details)

- **Header:** `#include <KIO/WorkerConfig>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS KIO)`  
  `target_link_libraries(mytarget PRIVATE KF6::KIOCore)`
- **Inherits:** [QObject](https://doc.qt.io/qt-6/qobject.html)

[List of all members, including inherited members](kio-workerconfig-members.md)

## Public Functions

- [KIO::MetaData configData(const QString &protocol, const QString &host)](#configData)
- [QString configData(const QString &protocol, const QString &host, const QString &key)](#configData-1)
- [void reset()](#reset)

## Signals

- [void configNeeded(const QString &protocol, const QString &host)](#configNeeded)

## Detailed Description {#details}

The Scheduler makes use of this class to configure the worker whenever it has to connect to a new host.

You only need to use this class if you want to override specific configuration items of an KIO worker when the worker is used by your application.

Normally KIO workers are being configured by "kio\_\<protocol\>rc" configuration files. Groups defined in such files are treated as host or domain specification. Configuration items defined in a group are only applied when the worker is connecting with a host that matches with the host and/or domain specified by the group.

## Member Function Documentation {#member-function-documentation}

### KIO::MetaData WorkerConfig::configData(const QString &*protocol*, const QString &*host*) {#configData}

Query worker configuration for workers of type `protocol` when dealing with `host`.

### QString WorkerConfig::configData(const QString &*protocol*, const QString &*host*, const QString &*key*) {#configData-1}

Query a specific configuration key for workers of type `protocol` when dealing with `host`.

### \[signal\] void WorkerConfig::configNeeded(const QString &*protocol*, const QString &*host*) {#configNeeded}

This signal is raised when a worker of type `protocol` deals with `host` for the first time.

Your application can use this signal to make some last minute configuration changes with setConfigData based on the host.

### void WorkerConfig::reset() {#reset}

Undo any changes made by calls to setConfigData.
