---
title: "KWidgetJobTracker Class"
description: "This class implements a job tracker with a widget suited for use as a progress dialog."
---

# KWidgetJobTracker Class

This class implements a job tracker with a widget suited for use as a progress dialog. [More...](#details)

- **Header:** `#include <KWidgetJobTracker>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS JobWidgets)`  
  `target_link_libraries(mytarget PRIVATE KF6::JobWidgets)`
- **Inherits:** [KAbstractWidgetJobTracker](kabstractwidgetjobtracker.md)

[List of all members, including inherited members](kwidgetjobtracker-members.md)

## Public Functions

- [KWidgetJobTracker(QWidget \*parent = nullptr)](#KWidgetJobTracker)
- [bool keepOpen(KJob \*job) const](#keepOpen)

## Detailed Description {#details}

## Member Function Documentation {#member-function-documentation}

### \[explicit\] KWidgetJobTracker::KWidgetJobTracker(QWidget \**parent* = nullptr) {#KWidgetJobTracker}

Creates a new [KWidgetJobTracker](kwidgetjobtracker.md)

`parent` the parent of this object and of the widget displaying the job progresses

### bool KWidgetJobTracker::keepOpen(KJob \**job*) const {#keepOpen}
