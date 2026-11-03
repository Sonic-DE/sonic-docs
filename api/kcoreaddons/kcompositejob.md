---
title: "KCompositeJob Class"
description: "The base class for all jobs able to be composed of one or more subjobs."
---

# KCompositeJob Class

The base class for all jobs able to be composed of one or more subjobs. [More...](#details)

- **Header:** `#include <KCompositeJob>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS CoreAddons)`  
  `target_link_libraries(mytarget PRIVATE KF6::CoreAddons)`
- **Inherits:** [KJob](kjob.md)

[List of all members, including inherited members](kcompositejob-members.md)

## Public Functions

- [KCompositeJob(QObject \*parent = nullptr)](#KCompositeJob)

## Public Slots

- [void slotInfoMessage(KJob \*job, const QString &message)](#slotInfoMessage)
- [void slotResult(KJob \*job)](#slotResult)

## Protected Functions

- [bool addSubjob(KJob \*job)](#addSubjob)
- [void clearSubjobs()](#clearSubjobs)
- [bool hasSubjobs() const](#hasSubjobs)
- [bool removeSubjob(KJob \*job)](#removeSubjob)
- [const QList\<KJob \*\> &subjobs() const](#subjobs)

## Detailed Description {#details}

## Member Function Documentation {#member-function-documentation}

### \[explicit\] KCompositeJob::KCompositeJob(QObject \**parent* = nullptr) {#KCompositeJob}

Creates a new [KCompositeJob](kcompositejob.md) object.

`parent` the parent [QObject](https://doc.qt.io/qt-6/qobject.html)

### \[virtual protected\] bool KCompositeJob::addSubjob(KJob \**job*) {#addSubjob}

Add a job that has to be finished before a result is emitted. This has obviously to be called before the result has been emitted by the job.

Note that the composite job takes ownership of `job`

`job` the subjob to add

Returns `true` if the job has been added correctly, false otherwise

### \[protected\] void KCompositeJob::clearSubjobs() {#clearSubjobs}

Clears the list of subjobs.

Note that this will \*not\* delete the subjobs. Ownership of the subjobs is passed on to the caller.

### \[protected\] bool KCompositeJob::hasSubjobs() const {#hasSubjobs}

Checks if this job has subjobs running.

Returns `true` if we still have subjobs running, false otherwise

### \[virtual protected\] bool KCompositeJob::removeSubjob(KJob \**job*) {#removeSubjob}

Mark a sub job as being done.

The ownership of `job` is passed on to the caller.

`job` the subjob to remove

Returns `true` if the job has been removed correctly, false otherwise

### \[virtual protected slot\] void KCompositeJob::slotInfoMessage(KJob \**job*, const QString &*message*) {#slotInfoMessage}

Forward signal from subjob.

`job` the subjob

`message` the info message

*See also* [infoMessage](kjob.md#infoMessage)()

### \[virtual protected slot\] void KCompositeJob::slotResult(KJob \**job*) {#slotResult}

Called whenever a subjob finishes.

Default implementation checks for errors and propagates to parent job, and in all cases it calls [removeSubjob](kcompositejob.md#removeSubjob).

`job` the subjob

### \[protected\] const QList\<KJob \*\> &KCompositeJob::subjobs() const {#subjobs}

Returns the full list of sub jobs
