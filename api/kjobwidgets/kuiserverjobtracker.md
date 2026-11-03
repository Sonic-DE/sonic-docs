---
title: "KUiServerJobTracker Class"
description: "The interface to implement to track the progresses of a job. Use KUiServerV2JobTracker. This class is deprecated since 6.17. We strongly advise against using it in new code."
---

# KUiServerJobTracker Class

The interface to implement to track the progresses of a job. Use [KUiServerV2JobTracker](kuiserverv2jobtracker.md). **This class is deprecated since 6.17. We strongly advise against using it in new code.** [More...](#details)

- **Header:** `#include <KUiServerJobTracker>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS JobWidgets)`  
  `target_link_libraries(mytarget PRIVATE KF6::JobWidgets)`
- **Inherits:** [KJobTrackerInterface](../kcoreaddons/kjobtrackerinterface.md)
- **Status:** Deprecated since 6.17

[List of all members, including inherited members](kuiserverjobtracker-members.md)

## Public Functions

- [KUiServerJobTracker(QObject \*parent = nullptr)](#KUiServerJobTracker)
- [void registerJob(KJob \*job)](#registerJob)
- [void unregisterJob(KJob \*job)](#unregisterJob)

**This class is deprecated since 6.17. We strongly advise against using it in new code.**

## Detailed Description {#details}

## Member Function Documentation {#member-function-documentation}

### \[explicit\] KUiServerJobTracker::KUiServerJobTracker(QObject \**parent* = nullptr) {#KUiServerJobTracker}

Creates a new [KJobTrackerInterface](../kcoreaddons/kjobtrackerinterface.md)

`parent` the parent object

### \[override virtual\] void KUiServerJobTracker::registerJob(KJob \**job*) {#registerJob}

Reimplements: [KJobTrackerInterface::registerJob(KJob \*job)](../kcoreaddons/kjobtrackerinterface.md#registerJob).

Register a new job in this tracker.

`job` the job to register

### \[override virtual\] void KUiServerJobTracker::unregisterJob(KJob \**job*) {#unregisterJob}

Reimplements: [KJobTrackerInterface::unregisterJob(KJob \*job)](../kcoreaddons/kjobtrackerinterface.md#unregisterJob).

Unregister a job from this tracker.

`job` the job to unregister
