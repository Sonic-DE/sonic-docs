---
title: "KAuth::ExecuteJob Class"
description: "Job for executing an Action."
---

# KAuth::ExecuteJob Class

Job for executing an Action. [More...](#details)

- **Header:** `#include <KAuth/ExecuteJob>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS Auth)`  
  `target_link_libraries(mytarget PRIVATE KF6::AuthCore)`
- **Inherits:** [KJob](../kcoreaddons/kjob.md)

[List of all members, including inherited members](kauth-executejob-members.md)

## Public Functions

- [KAuth::Action action() const](#action)
- [QVariantMap data() const](#data)
- [void start()](#start)

## Public Slots

- [bool kill(KJob::KillVerbosity verbosity = Quietly)](#kill)

## Signals

- [void newData(const QVariantMap &data)](#newData)
- [void statusChanged(KAuth::Action::AuthStatus status)](#statusChanged)

## Detailed Description {#details}

To run the action synchonously use [KJob::exec](../kcoreaddons/kjob.md#exec)() and check the return code for success.

For longer tasks connect [KJob::result](../kcoreaddons/kjob.md#result)([KJob](../kcoreaddons/kjob.md)\*) and any other signals such as percent([KJob](../kcoreaddons/kjob.md)\*, unsigned long) and [newData](kauth-executejob.md#newData)(const [QVariantMap](https://doc.qt.io/qt-6/qvariant.html#QVariantMap-typedef) &) then run [start](kauth-executejob.md#start)().

To check for authentiation success or problems connect to [statusChanged](kauth-executejob.md#statusChanged)([KAuth::Action::AuthStatus](kauth-action.md#AuthStatus-enum) status) signal.

Use [data](kauth-executejob.md#data)() to get the return result of the action.

## Member Function Documentation {#member-function-documentation}

### KAuth::Action ExecuteJob::action() const {#action}

Returns the action associated with this job

### QVariantMap ExecuteJob::data() const {#data}

Use this to get the data set in the action by [HelperSupport::progressStep](kauth-helpersupport.md#progressStep)([QVariant](https://doc.qt.io/qt-6/qvariant.html)) or returned at the end of the action.

This function is particularly useful once the job has completed. During execution, simply read the data in the [newData](kauth-executejob.md#newData)() signal.

Returns the data set by the helper

*See also* [ExecuteJob::newData](kauth-executejob.md#newData)

### \[slot\] bool ExecuteJob::kill(KJob::KillVerbosity *verbosity* = Quietly) {#kill}

Attempts to halt the execution of the action associated with this job. You should listen to the finished and result signals to work out whether halting was successful (as long running operations can also take time to shut down cleanly). Always returns `true`

*See also* [HelperSupport::isStopped](kauth-helpersupport.md#isStopped)(), [KJob::result](../kcoreaddons/kjob.md#result), [KJob::finished](../kcoreaddons/kjob.md#finished)

### \[signal\] void ExecuteJob::newData(const QVariantMap &*data*) {#newData}

Signal emitted by the helper to notify the action's progress

This signal is emitted every time the helper's code calls the [HelperSupport::progressStep](kauth-helpersupport.md#progressStep)([QVariantMap](https://doc.qt.io/qt-6/qvariant.html#QVariantMap-typedef)) method. This is useful to let the helper notify the execution status of a long action, also providing some data, for example if you want to achieve some sort of progressive loading. The meaning of the data passed here is totally application-dependent. If you only need to pass some percentage, you can use the other signal that pass an int.

`data` The progress data from the helper

### \[override virtual\] void ExecuteJob::start() {#start}

Reimplements: [KJob::start()](../kcoreaddons/kjob.md#start).

Starts the job asynchronously.

*See also* [KJob::result](../kcoreaddons/kjob.md#result), [newData](kauth-executejob.md#newData), [statusChanged](kauth-executejob.md#statusChanged)

### \[signal\] void ExecuteJob::statusChanged(KAuth::Action::AuthStatus *status*) {#statusChanged}

Signal emitted when the authentication status changes `status` the new authentication status
