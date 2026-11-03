---
title: "BluezQt::InitManagerJob Class"
description: "Init manager job."
---

# BluezQt::InitManagerJob Class

Init manager job. [More...](#details)

- **Header:** `#include <BluezQt/InitManagerJob>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS BluezQt)`  
  `target_link_libraries(mytarget PRIVATE KF6::BluezQt)`
- **Inherits:** [BluezQt::Job](bluezqt-job.md)

[List of all members, including inherited members](bluezqt-initmanagerjob-members.md)

## Properties

- [\[read-only\] manager : Manager\*](#manager-prop)

## Public Functions

- [BluezQt::Manager \*manager() const](#manager)

## Signals

- [void result(BluezQt::InitManagerJob \*job)](#result)

## Detailed Description {#details}

This class represents a job that initializes Manager.

## Property Documentation {#property-documentation}

### \[read-only\] manager : Manager\* {#manager-prop}

**Access functions:**

- `BluezQt::Manager` \***[manager](bluezqt-initmanagerjob.md#manager)**() const

## Member Function Documentation {#member-function-documentation}

### BluezQt::Manager \*InitManagerJob::manager() const {#manager}

Returns a manager that is being initialized.

> **Note:** Getter function for property [manager](bluezqt-initmanagerjob.md#manager-prop).

### \[signal\] void InitManagerJob::result(BluezQt::InitManagerJob \**job*) {#result}

Indicates that the `job` has finished.
