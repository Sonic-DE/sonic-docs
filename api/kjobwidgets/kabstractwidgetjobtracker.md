---
title: "KAbstractWidgetJobTracker Class"
description: "The base class for widget based job trackers."
---

# KAbstractWidgetJobTracker Class

The base class for widget based job trackers. [More...](#details)

- **Header:** `#include <KAbstractWidgetJobTracker>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS JobWidgets)`  
  `target_link_libraries(mytarget PRIVATE KF6::JobWidgets)`
- **Inherits:** [KJobTrackerInterface](../kcoreaddons/kjobtrackerinterface.md)
- **Inherited By:** [KStatusBarJobTracker](kstatusbarjobtracker.md) and [KWidgetJobTracker](kwidgetjobtracker.md)

[List of all members, including inherited members](kabstractwidgetjobtracker-members.md)

## Public Functions

- [KAbstractWidgetJobTracker(QWidget \*parent = nullptr)](#KAbstractWidgetJobTracker)
- [bool autoDelete(KJob \*job) const](#autoDelete)
- [void setAutoDelete(KJob \*job, bool autoDelete)](#setAutoDelete)
- [void setStopOnClose(KJob \*job, bool stopOnClose)](#setStopOnClose)
- [bool stopOnClose(KJob \*job) const](#stopOnClose)
- [QWidget \*widget(KJob \*job)](#widget)

## Public Slots

- [void registerJob(KJob \*job)](#registerJob)
- [void slotClean(KJob \*job)](#slotClean)
- [void slotResume(KJob \*job)](#slotResume)
- [void slotStop(KJob \*job)](#slotStop)
- [void slotSuspend(KJob \*job)](#slotSuspend)
- [void unregisterJob(KJob \*job)](#unregisterJob)

## Signals

- [void resume(KJob \*job)](#resume)
- [void stopped(KJob \*job)](#stopped)
- [void suspend(KJob \*job)](#suspend)

## Detailed Description {#details}

## Member Function Documentation {#member-function-documentation}

### \[explicit\] KAbstractWidgetJobTracker::KAbstractWidgetJobTracker(QWidget \**parent* = nullptr) {#KAbstractWidgetJobTracker}

Creates a new [KAbstractWidgetJobTracker](kabstractwidgetjobtracker.md)

`parent` the parent of this object and of the widget displaying the job progresses

### bool KAbstractWidgetJobTracker::autoDelete(KJob \**job*) const {#autoDelete}

Checks whether the dialog should be deleted or cleaned.

`job` the job's widget that will be auto-deleted

Returns `false` if the dialog only calls [slotClean](kabstractwidgetjobtracker.md#slotClean), true if it will be deleted

*See also* [setAutoDelete](kabstractwidgetjobtracker.md#setAutoDelete)()

### \[override virtual slot\] void KAbstractWidgetJobTracker::registerJob(KJob \**job*) {#registerJob}

Reimplements: [KJobTrackerInterface::registerJob(KJob \*job)](../kcoreaddons/kjobtrackerinterface.md#registerJob).

Register a new job in this tracker. Note that job trackers inheriting from this class can have only one job registered at a time.

`job` the job to register

### \[signal\] void KAbstractWidgetJobTracker::resume(KJob \**job*) {#resume}

Emitted when the user resumed the operation

`job` The job that has been resumed

### void KAbstractWidgetJobTracker::setAutoDelete(KJob \**job*, bool *autoDelete*) {#setAutoDelete}

This controls whether the dialog should be deleted or only cleaned when the [KJob](../kcoreaddons/kjob.md) is finished (or canceled).

If your dialog is an embedded widget and not a separate window, you should setAutoDelete(false) in the constructor of your custom dialog.

`job` the job's widget that is going to be auto-deleted

`autoDelete` If false the dialog will only call method [slotClean](kabstractwidgetjobtracker.md#slotClean).

If true the dialog will be deleted.

*See also* [autoDelete](kabstractwidgetjobtracker.md#autoDelete)()

### void KAbstractWidgetJobTracker::setStopOnClose(KJob \**job*, bool *stopOnClose*) {#setStopOnClose}

This controls whether the job should be canceled if the dialog is closed.

`job` the job's widget that will be stopped when closing

`stopOnClose` If true the job will be stopped if the dialog is closed, otherwise the job will continue even on close.

*See also* [stopOnClose](kabstractwidgetjobtracker.md#stopOnClose)()

### \[virtual protected slot\] void KAbstractWidgetJobTracker::slotClean(KJob \**job*) {#slotClean}

This method is called when the widget should be cleaned (after job is finished). redefine this for custom behavior.

`job` The job that is being cleaned

### \[virtual protected slot\] void KAbstractWidgetJobTracker::slotResume(KJob \**job*) {#slotResume}

This method should be called for pause/resume Connect this to the progress widgets buttons etc.

`job` The job that is being resumed

### \[virtual protected slot\] void KAbstractWidgetJobTracker::slotStop(KJob \**job*) {#slotStop}

This method should be called for correct cancellation of IO operation Connect this to the progress widgets buttons etc.

`job` The job that is being stopped

### \[virtual protected slot\] void KAbstractWidgetJobTracker::slotSuspend(KJob \**job*) {#slotSuspend}

This method should be called for pause/resume Connect this to the progress widgets buttons etc.

`job` The job that is being suspended

### bool KAbstractWidgetJobTracker::stopOnClose(KJob \**job*) const {#stopOnClose}

Checks whether the job will be killed when the dialog is closed.

`job` the job's widget that will be stopped when closing

Returns `true` if the job is killed on close event, false otherwise.

*See also* [setStopOnClose](kabstractwidgetjobtracker.md#setStopOnClose)()

### \[signal\] void KAbstractWidgetJobTracker::stopped(KJob \**job*) {#stopped}

Emitted when the user aborted the operation

`job` The job that has been stopped

### \[signal\] void KAbstractWidgetJobTracker::suspend(KJob \**job*) {#suspend}

Emitted when the user suspended the operation

`job` The job that has been suspended

### \[override virtual slot\] void KAbstractWidgetJobTracker::unregisterJob(KJob \**job*) {#unregisterJob}

Reimplements: [KJobTrackerInterface::unregisterJob(KJob \*job)](../kcoreaddons/kjobtrackerinterface.md#unregisterJob).

Unregister a job from this tracker.

`job` the job to unregister

### \[pure virtual\] QWidget \*KAbstractWidgetJobTracker::widget(KJob \**job*) {#widget}

The widget associated to this tracker.

`job` the job that is assigned the widget we want to return Returns the widget displaying the job progresses
