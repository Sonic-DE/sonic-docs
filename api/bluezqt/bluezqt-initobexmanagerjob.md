---
title: "BluezQt::InitObexManagerJob Class"
description: "Init obex manager job."
---

# BluezQt::InitObexManagerJob Class

Init obex manager job. [More...](#details)

- **Header:** `#include <BluezQt/InitObexManagerJob>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS BluezQt)`  
  `target_link_libraries(mytarget PRIVATE KF6::BluezQt)`
- **Inherits:** [BluezQt::Job](bluezqt-job.md)

[List of all members, including inherited members](bluezqt-initobexmanagerjob-members.md)

## Properties

- [\[read-only\] manager : ObexManager\*](#manager-prop)

## Public Functions

- [BluezQt::ObexManager \*manager() const](#manager)

## Signals

- [void result(BluezQt::InitObexManagerJob \*job)](#result)

## Detailed Description {#details}

This class represents a job that initializes [ObexManager](bluezqt-obexmanager.md).

## Property Documentation {#property-documentation}

### \[read-only\] manager : ObexManager\* {#manager-prop}

**Access functions:**

- `BluezQt::ObexManager` \***[manager](bluezqt-initobexmanagerjob.md#manager)**() const

## Member Function Documentation {#member-function-documentation}

### BluezQt::ObexManager \*InitObexManagerJob::manager() const {#manager}

Returns a manager that is being initialized.

> **Note:** Getter function for property [manager](bluezqt-initobexmanagerjob.md#manager-prop).

### \[signal\] void InitObexManagerJob::result(BluezQt::InitObexManagerJob \**job*) {#result}

Indicates that the job have finished.
