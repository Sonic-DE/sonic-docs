---
title: "KUpdateLaunchEnvironmentJob Class"
description: "Job for updating the launch environment. This class was introduced in Qt 6.0."
---

# KUpdateLaunchEnvironmentJob Class

Job for updating the launch environment. This class was introduced in Qt 6.0. [More...](#details)

- **Header:** `#include <KUpdateLaunchEnvironmentJob>`
- **Since:** Qt 6.0
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS DBusAddons)`  
  `target_link_libraries(mytarget PRIVATE KF6::DBusAddons)`
- **Inherits:** [QObject](https://doc.qt.io/qt-6/qobject.html)

[List of all members, including inherited members](kupdatelaunchenvironmentjob-members.md)

## Public Functions

- [KUpdateLaunchEnvironmentJob(const QProcessEnvironment &environment)](#KUpdateLaunchEnvironmentJob)

## Signals

- [void finished()](#finished)

## Detailed Description {#details}

This job adds or updates an environment variable in process environment that will be used when a process is launched. This includes:

- DBus activation
- Systemd units
- Plasma-session

Environment variables are sanitized before uploading.

This object deletes itself after completion, similar to KJobs.

Example usage:

```cpp
QProcessEnvironment newEnv;
newEnv.insert("VARIABLE"_s, "value"_s);
auto job = new KUpdateLaunchEnvironmentJob(newEnv);
QObject::connect(job, &KUpdateLaunchEnvironmentJob::finished, &SomeClass, &SomeClass::someSlot);
```

Porting from KF5 to KF6:

The class UpdateLaunchEnvironmentJob was renamed to [KUpdateLaunchEnvironmentJob](kupdatelaunchenvironmentjob.md).

## Member Function Documentation {#member-function-documentation}

### \[explicit\] KUpdateLaunchEnvironmentJob::KUpdateLaunchEnvironmentJob(const QProcessEnvironment &*environment*) {#KUpdateLaunchEnvironmentJob}

Creates a new job for the given launch `environment`.

### \[signal\] void KUpdateLaunchEnvironmentJob::finished() {#finished}

Emitted when the job is finished, before the object is automatically deleted.
