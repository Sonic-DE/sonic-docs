---
title: "KStatusBarJobTracker Class"
description: "This class implements a job tracker with a widget suited for embedding in a status bar."
---

# KStatusBarJobTracker Class

This class implements a job tracker with a widget suited for embedding in a status bar. [More...](#details)

- **Header:** `#include <KStatusBarJobTracker>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS JobWidgets)`  
  `target_link_libraries(mytarget PRIVATE KF6::JobWidgets)`
- **Inherits:** [KAbstractWidgetJobTracker](kabstractwidgetjobtracker.md)

[List of all members, including inherited members](kstatusbarjobtracker-members.md)

## Public Types

- [enum KStatusBarJobTracker::StatusBarMode](#StatusBarMode-enum)

## Public Functions

- [KStatusBarJobTracker(QWidget \*parent = nullptr, bool button = true)](#KStatusBarJobTracker)
- [void setStatusBarMode(KStatusBarJobTracker::StatusBarModes statusBarMode)](#setStatusBarMode)

## Detailed Description {#details}

## Member Type Documentation {#member-type-documentation}

### enum KStatusBarJobTracker::StatusBarMode {#StatusBarMode-enum}

**flags KStatusBarJobTracker::StatusBarModes**

| Constant | Value | Description |
| --- | --- | --- |
| `KStatusBarJobTracker::NoInformation` | `0x0000` | Does not show any information |
| `KStatusBarJobTracker::LabelOnly` | `0x0001` | Shows an informative label for job progress |
| `KStatusBarJobTracker::ProgressOnly` | `0x0002` | Shows a progress bar with the job completion |

The `StatusBarModes` type is a typedef for `QFlags<StatusBarMode>. `It stores an OR combination of `StatusBarMode` values.

## Member Function Documentation {#member-function-documentation}

### \[explicit\] KStatusBarJobTracker::KStatusBarJobTracker(QWidget \**parent* = nullptr, bool *button* = true) {#KStatusBarJobTracker}

Creates a new [KStatusBarJobTracker](kstatusbarjobtracker.md)

`parent` the parent of this object and of the widget displaying the job progresses

`button` true to display a stop button allowing to kill the job, false otherwise

### void KStatusBarJobTracker::setStatusBarMode(KStatusBarJobTracker::StatusBarModes *statusBarMode*) {#setStatusBarMode}

Sets the mode of the status bar.

`statusBarMode` what information the status bar will show (see [StatusBarMode](kstatusbarjobtracker.md#StatusBarMode-enum)). [LabelOnly](kstatusbarjobtracker.md#StatusBarMode-enum) by default
