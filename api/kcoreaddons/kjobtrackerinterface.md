---
title: "KJobTrackerInterface Class"
description: "The interface to implement to track the progresses of a job."
---

# KJobTrackerInterface Class

The interface to implement to track the progresses of a job. [More...](#details)

- **Header:** `#include <KJobTrackerInterface>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS CoreAddons)`  
  `target_link_libraries(mytarget PRIVATE KF6::CoreAddons)`
- **Inherits:** [QObject](https://doc.qt.io/qt-6/qobject.html)

[List of all members, including inherited members](kjobtrackerinterface-members.md)

## Public Functions

- [KJobTrackerInterface(QObject \*parent = nullptr)](#KJobTrackerInterface)

## Public Slots

- [void description(KJob \*job, const QString &title, const QPair\<QString, QString\> &field1, const QPair\<QString, QString\> &field2)](#description)
- [void finished(KJob \*job)](#finished)
- [void infoMessage(KJob \*job, const QString &message)](#infoMessage)
- [void percent(KJob \*job, unsigned long percent)](#percent)
- [void processedAmount(KJob \*job, KJob::Unit unit, qulonglong amount)](#processedAmount)
- [void registerJob(KJob \*job)](#registerJob)
- [void resumed(KJob \*job)](#resumed)
- [void speed(KJob \*job, unsigned long value)](#speed)
- [void suspended(KJob \*job)](#suspended)
- [void totalAmount(KJob \*job, KJob::Unit unit, qulonglong amount)](#totalAmount)
- [void unregisterJob(KJob \*job)](#unregisterJob)
- [void warning(KJob \*job, const QString &message)](#warning)

## Detailed Description {#details}

## Member Function Documentation {#member-function-documentation}

### \[explicit\] KJobTrackerInterface::KJobTrackerInterface(QObject \**parent* = nullptr) {#KJobTrackerInterface}

Creates a new [KJobTrackerInterface](kjobtrackerinterface.md)

`parent` the parent object

### \[virtual protected slot\] void KJobTrackerInterface::description(KJob \**job*, const QString &*title*, const QPair\<QString, QString\> &*field1*, const QPair\<QString, QString\> &*field2*) {#description}

Called to display general description of a job. A description has a title and two optional fields which can be used to complete the description.

Examples of titles are "Copying", "Creating resource", etc. The fields of the description can be "Source" with an URL, and, "Destination" with an URL for a "Copying" description.

`job` the job that emitted this signal

`title` the general description of the job

`field1` first field (localized name and value)

`field2` second field (localized name and value)

### \[virtual protected slot\] void KJobTrackerInterface::finished(KJob \**job*) {#finished}

Called when a job is finished, in any case. It is used to notify that the job is terminated and that progress UI (if any) can be hidden.

`job` the job that emitted this signal

### \[virtual protected slot\] void KJobTrackerInterface::infoMessage(KJob \**job*, const QString &*message*) {#infoMessage}

Called to display state information about a job. Examples of message are "Resolving host", "Connecting to host...", etc.

`job` the job that emitted this signal

`message` the info message

### \[virtual protected slot\] void KJobTrackerInterface::percent(KJob \**job*, unsigned long *percent*) {#percent}

Called to show the overall progress of the job. Note that this is not called for finished jobs.

`job` the job that emitted this signal

`percent` the percentage

### \[virtual protected slot\] void KJobTrackerInterface::processedAmount(KJob \**job*, KJob::Unit *unit*, qulonglong *amount*) {#processedAmount}

Regularly called to show the progress of a job by giving the current amount. The unit of this amount is provided too. It can be called several times for a given job if the job manages several different units.

`job` the job that emitted this signal

`unit` the unit of the processed amount

`amount` the processed amount

### \[virtual slot\] void KJobTrackerInterface::registerJob(KJob \**job*) {#registerJob}

Register a new job in this tracker. The default implementation connects the following [KJob](kjob.md) signals to the respective protected slots of this class:

- [finished](kjobtrackerinterface.md#finished)() (also connected to the [unregisterJob](kjobtrackerinterface.md#unregisterJob)() slot)
- [suspended](kjobtrackerinterface.md#suspended)()
- [resumed](kjobtrackerinterface.md#resumed)()
- [description](kjobtrackerinterface.md#description)()
- [infoMessage](kjobtrackerinterface.md#infoMessage)()
- [totalAmount](kjobtrackerinterface.md#totalAmount)()
- [processedAmount](kjobtrackerinterface.md#processedAmount)()
- [percent](kjobtrackerinterface.md#percent)()
- [speed](kjobtrackerinterface.md#speed)()

If you re-implement this method, you may want to call the default implementation or add at least:

```cpp
connect(job, &KJob::finished, this, &MyJobTracker::unregisterJob);
```

so that you won't have to manually call [unregisterJob](kjobtrackerinterface.md#unregisterJob)().

`job` the job to register

*See also* [unregisterJob](kjobtrackerinterface.md#unregisterJob)()

### \[virtual protected slot\] void KJobTrackerInterface::resumed(KJob \**job*) {#resumed}

Called when a job is resumed.

`job` the job that emitted this signal

### \[virtual protected slot\] void KJobTrackerInterface::speed(KJob \**job*, unsigned long *value*) {#speed}

Called to show the speed of the job.

`job` the job that emitted this signal

`value` the current speed of the job

### \[virtual protected slot\] void KJobTrackerInterface::suspended(KJob \**job*) {#suspended}

Called when a job is suspended.

`job` the job that emitted this signal

### \[virtual protected slot\] void KJobTrackerInterface::totalAmount(KJob \**job*, KJob::Unit *unit*, qulonglong *amount*) {#totalAmount}

Called when we know the amount a job will have to process. The unit of this amount is provided too. It can be called several times for a given job if the job manages several different units.

`job` the job that emitted this signal

`unit` the unit of the total amount

`amount` the total amount

### \[virtual slot\] void KJobTrackerInterface::unregisterJob(KJob \**job*) {#unregisterJob}

Unregister a job from this tracker.

> **Note:** You need to manually call this method only if you re-implemented [registerJob](kjobtrackerinterface.md#registerJob)() without connecting [KJob::finished](kjob.md#finished) to this slot.

`job` the job to unregister

*See also* [registerJob](kjobtrackerinterface.md#registerJob)()

### \[virtual protected slot\] void KJobTrackerInterface::warning(KJob \**job*, const QString &*message*) {#warning}

Emitted to display a warning about a job.

`job` the job that emitted this signal

`message` the warning message
