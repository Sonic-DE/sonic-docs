---
title: "KTerminalLauncherJob Class"
description: "KTerminalLauncherJob starts a terminal application, either for the user to use interactively, or to execute a command."
---

# KTerminalLauncherJob Class

[KTerminalLauncherJob](kterminallauncherjob.md) starts a terminal application, either for the user to use interactively, or to execute a command. [More...](#details)

- **Header:** `#include <KTerminalLauncherJob>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS KIO)`  
  `target_link_libraries(mytarget PRIVATE KIOGui)`
- **Inherits:** [KJob](../kcoreaddons/kjob.md)

[List of all members, including inherited members](kterminallauncherjob-members.md)

## Public Functions

- [KTerminalLauncherJob(const QString &command, QObject \*parent = nullptr)](#KTerminalLauncherJob)
- [~KTerminalLauncherJob()](#dtor.KTerminalLauncherJob)
- [bool prepare()](#prepare) (since 6.17)
- [void setProcessEnvironment(const QProcessEnvironment &environment)](#setProcessEnvironment)
- [void setStartupId(const QByteArray &startupId)](#setStartupId)
- [void setWorkingDirectory(const QString &workingDirectory)](#setWorkingDirectory)
- [void start()](#start)

## Detailed Description {#details}

It creates a startup notification and finishes it on success or on error (for the taskbar). It also emits an error message if necessary (e.g. "program not found").

The job finishes when the application is successfully started. For error handling, either connect to the [result](../kcoreaddons/kjob.md#result)() signal, or for a simple messagebox on error, you can do

```cpp
job->setUiDelegate(new KDialogJobUiDelegate(KJobUiDelegate::AutoHandlingEnabled, this));
```

## Member Function Documentation {#member-function-documentation}

### \[explicit\] KTerminalLauncherJob::KTerminalLauncherJob(const QString &*command*, QObject \**parent* = nullptr) {#KTerminalLauncherJob}

Creates a [KTerminalLauncherJob](kterminallauncherjob.md).

`command` the command to execute in a terminal, can be empty.

`parent` the parent [QObject](https://doc.qt.io/qt-6/qobject.html)

### \[override virtual noexcept\] KTerminalLauncherJob::~KTerminalLauncherJob() {#dtor.KTerminalLauncherJob}

Destructor

Note that jobs auto-delete themselves after emitting result

### \[since 6.17\] bool KTerminalLauncherJob::prepare() {#prepare}

Checks whether the command to launch a terminal can be constructed and sets it.

The [start](kterminallauncherjob.md#start)() function calls this internally, so you only need to call prepare() directly if you want to validate the command separately from actually starting the terminal.

This is useful if you want to avoid calling [start](kterminallauncherjob.md#start)() just to catch an error, for example to conditionally show or hide a GUI element depending on whether launching a terminal is likely to succeed.

Returns true if a launch command could be constructed, false otherwise.

This function was introduced in Qt 6.17.

*See also* [start](kterminallauncherjob.md#start)()

### void KTerminalLauncherJob::setProcessEnvironment(const QProcessEnvironment &*environment*) {#setProcessEnvironment}

Can be used to pass environment variables to the child process.

`environment` set of environment variables to pass to the child process

*See also* [QProcessEnvironment](https://doc.qt.io/qt-6/qprocessenvironment.html)

### void KTerminalLauncherJob::setStartupId(const QByteArray &*startupId*) {#setStartupId}

Sets the platform-specific startup id of the command launch.

`startupId` startup id, if any (otherwise "").

For X11, this would be the id for the Startup Notification protocol.

### void KTerminalLauncherJob::setWorkingDirectory(const QString &*workingDirectory*) {#setWorkingDirectory}

Sets the working directory from which to run the command.

`workingDirectory` path of a local directory

### \[override virtual\] void KTerminalLauncherJob::start() {#start}

Reimplements: [KJob::start()](../kcoreaddons/kjob.md#start).

Starts the job. You must call this, after having called all the necessary setters.
