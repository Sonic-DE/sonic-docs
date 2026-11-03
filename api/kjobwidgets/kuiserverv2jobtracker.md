---
title: "KUiServerV2JobTracker Class"
description: "The interface to implement to track the progresses of a job."
---

# KUiServerV2JobTracker Class

The interface to implement to track the progresses of a job. [More...](#details)

- **Header:** `#include <KUiServerV2JobTracker>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS JobWidgets)`  
  `target_link_libraries(mytarget PRIVATE KF6::JobWidgets)`
- **Inherits:** [KJobTrackerInterface](../kcoreaddons/kjobtrackerinterface.md)

[List of all members, including inherited members](kuiserverv2jobtracker-members.md)

## Public Functions

- [KUiServerV2JobTracker(QObject \*parent = nullptr)](#KUiServerV2JobTracker)
- [void registerJob(KJob \*job)](#registerJob)
- [void unregisterJob(KJob \*job)](#unregisterJob)

## Detailed Description {#details}

## Member Function Documentation {#member-function-documentation}

### \[explicit\] KUiServerV2JobTracker::KUiServerV2JobTracker(QObject \**parent* = nullptr) {#KUiServerV2JobTracker}

Creates a new [KJobTrackerInterface](../kcoreaddons/kjobtrackerinterface.md)

`parent` the parent object

### \[override virtual\] void KUiServerV2JobTracker::registerJob(KJob \**job*) {#registerJob}

Reimplements: [KJobTrackerInterface::registerJob(KJob \*job)](../kcoreaddons/kjobtrackerinterface.md#registerJob).

Register a new job in this tracker.

`job` the job to register

### \[override virtual\] void KUiServerV2JobTracker::unregisterJob(KJob \**job*) {#unregisterJob}

Reimplements: [KJobTrackerInterface::unregisterJob(KJob \*job)](../kcoreaddons/kjobtrackerinterface.md#unregisterJob).

Unregister a job from this tracker.

`job` the job to unregister
