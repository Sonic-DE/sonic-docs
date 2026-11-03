---
title: "KInhibitionJobTracker Class"
description: "Block standby mode while a job is running. This class was introduced in Qt 6.18."
---

# KInhibitionJobTracker Class

Block standby mode while a job is running. This class was introduced in Qt 6.18. [More...](#details)

- **Header:** `#include <KInhibitionJobTracker>`
- **Since:** Qt 6.18
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS JobWidgets)`  
  `target_link_libraries(mytarget PRIVATE KF6::JobWidgets)`
- **Inherits:** [KJobTrackerInterface](../kcoreaddons/kjobtrackerinterface.md)

[List of all members, including inherited members](kinhibitionjobtracker-members.md)

## Public Functions

- [KInhibitionJobTracker(QObject \*parent = nullptr)](#KInhibitionJobTracker)
- [~KInhibitionJobTracker()](#dtor.KInhibitionJobTracker)
- [void registerJob(KJob \*job)](#registerJob)
- [void unregisterJob(KJob \*job)](#unregisterJob)

## Detailed Description {#details}

This job tracker will prevent the system from going into standby mode while a given job is running. This can be used to guard potentially lengthy operations, such as copying files, encoding videos, extracting archives, etc.

When the job is started, a power management inhibition is posted after a short delay. When the job is paused, the inhibition is lifted until the job is resumed again.

## Member Function Documentation {#member-function-documentation}

### \[explicit\] KInhibitionJobTracker::KInhibitionJobTracker(QObject \**parent* = nullptr) {#KInhibitionJobTracker}

Creates a new [KInhibitionJobTracker](kinhibitionjobtracker.md)

`parent` the parent object

### \[override virtual noexcept\] KInhibitionJobTracker::~KInhibitionJobTracker() {#dtor.KInhibitionJobTracker}

Creates a new [KJobTrackerInterface](../kcoreaddons/kjobtrackerinterface.md)

`parent` the parent object

### \[override virtual\] void KInhibitionJobTracker::registerJob(KJob \**job*) {#registerJob}

Reimplements: [KJobTrackerInterface::registerJob(KJob \*job)](../kcoreaddons/kjobtrackerinterface.md#registerJob).

Register a new job in this tracker.

`job` the job to register

### \[override virtual\] void KInhibitionJobTracker::unregisterJob(KJob \**job*) {#unregisterJob}

Reimplements: [KJobTrackerInterface::unregisterJob(KJob \*job)](../kcoreaddons/kjobtrackerinterface.md#unregisterJob).

Unregister a job from this tracker.

`job` the job to unregister
