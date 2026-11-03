---
title: "KIO::CommandLauncherJob Class"
description: "CommandLauncherJob runs a command and watches it while running."
---

# KIO::CommandLauncherJob Class

[CommandLauncherJob](kio-commandlauncherjob.md) runs a command and watches it while running. [More...](#details)

- **Header:** `#include <KIO/CommandLauncherJob>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS KIO)`  
  `target_link_libraries(mytarget PRIVATE KIOGui)`
- **Inherits:** [KJob](../kcoreaddons/kjob.md)

[List of all members, including inherited members](kio-commandlauncherjob-members.md)

## Public Functions

- [CommandLauncherJob(const QString &command, QObject \*parent = nullptr)](#CommandLauncherJob)
- [CommandLauncherJob(const QString &executable, const QStringList &args, QObject \*parent = nullptr)](#CommandLauncherJob-1)
- [~CommandLauncherJob()](#dtor.CommandLauncherJob)
- [QString command() const](#command)
- [qint64 pid() const](#pid)
- [void setCommand(const QString &command)](#setCommand)
- [void setDesktopName(const QString &desktopName)](#setDesktopName)
- [void setExecutable(const QString &executable)](#setExecutable)
- [void setProcessEnvironment(const QProcessEnvironment &environment)](#setProcessEnvironment)
- [void setStartupId(const QByteArray &startupId)](#setStartupId)
- [void setWorkingDirectory(const QString &workingDirectory)](#setWorkingDirectory)
- [void start()](#start)
- [QString workingDirectory() const](#workingDirectory)

## Detailed Description {#details}

It creates a startup notification and finishes it on success or on error (for the taskbar). It also emits a "program not found" error message if the requested command did not exist.

The job finishes when the command is successfully started; at that point you can query the PID with [pid](kio-commandlauncherjob.md#pid)(). Note that no other errors are handled automatically after the command starts running. As far as [CommandLauncherJob](kio-commandlauncherjob.md) is concerned, if the command was launched, the result is a success. If you need to query the command for its exit status or error text later, it is recommended to use [QProcess](https://doc.qt.io/qt-6/qprocess.html) instead.

For error handling, either connect to the [result](../kcoreaddons/kjob.md#result)() signal, or for a simple messagebox on error, you can do

```cpp
job->setUiDelegate(new KDialogJobUiDelegate(KJobUiDelegate::AutoHandlingEnabled, this));
```

## Member Function Documentation {#member-function-documentation}

### \[explicit\] CommandLauncherJob::CommandLauncherJob(const QString &*command*, QObject \**parent* = nullptr) {#CommandLauncherJob}

Creates a [CommandLauncherJob](kio-commandlauncherjob.md).

`command` the shell command to run

The command is given "as is" to the shell, it must already be quoted if necessary. If `command` is instead a filename, consider using the other constructor, even if no args are present.

`parent` the parent [QObject](https://doc.qt.io/qt-6/qobject.html)

Please consider also calling [setDesktopName](kio-commandlauncherjob.md#setDesktopName)() for better startup notification.

### \[explicit\] CommandLauncherJob::CommandLauncherJob(const QString &*executable*, const QStringList &*args*, QObject \**parent* = nullptr) {#CommandLauncherJob-1}

Creates a [CommandLauncherJob](kio-commandlauncherjob.md).

`executable` the name of the executable

`args` the commandline arguments to pass to the executable

`parent` the parent [QObject](https://doc.qt.io/qt-6/qobject.html)

Please consider also calling [setDesktopName](kio-commandlauncherjob.md#setDesktopName)() for better startup notification.

### \[override virtual noexcept\] CommandLauncherJob::~CommandLauncherJob() {#dtor.CommandLauncherJob}

Destructor

Note that jobs auto-delete themselves after emitting result

### QString CommandLauncherJob::command() const {#command}

Returns the command executed by this job.

*See also* [setCommand](kio-commandlauncherjob.md#setCommand)()

### qint64 CommandLauncherJob::pid() const {#pid}

Returns the PID of the command that was started

Available after the job emits [result](../kcoreaddons/kjob.md#result)().

### void CommandLauncherJob::setCommand(const QString &*command*) {#setCommand}

Sets the command to execute, this will change the command that was set by any of the constructors.

*See also* [command](kio-commandlauncherjob.md#command)()

### void CommandLauncherJob::setDesktopName(const QString &*desktopName*) {#setDesktopName}

Set the name of the desktop file (e.g. "org.kde.dolphin", without the ".desktop" filename extension).

This is necessary for startup notification to work.

### void CommandLauncherJob::setExecutable(const QString &*executable*) {#setExecutable}

Sets the name of the executable, used in the startup notification (see KStartupInfoData::setBin()).

`executable` executable name, with or without a path

Alternatively, use [setDesktopName](kio-commandlauncherjob.md#setDesktopName)().

### void CommandLauncherJob::setProcessEnvironment(const QProcessEnvironment &*environment*) {#setProcessEnvironment}

Can be used to pass environment variables to the child process.

`environment` set of environment variables to pass to the child process

*See also* [QProcessEnvironment](https://doc.qt.io/qt-6/qprocessenvironment.html)

### void CommandLauncherJob::setStartupId(const QByteArray &*startupId*) {#setStartupId}

Sets the platform-specific startup id of the command launch.

`startupId` startup id, if any (otherwise "").

For X11, this would be the id for the Startup Notification protocol.

### void CommandLauncherJob::setWorkingDirectory(const QString &*workingDirectory*) {#setWorkingDirectory}

Sets the working directory from which to run the command.

`workingDirectory` path of a local directory

*See also* [workingDirectory](kio-commandlauncherjob.md#workingDirectory)()

### \[override virtual\] void CommandLauncherJob::start() {#start}

Reimplements: [KJob::start()](../kcoreaddons/kjob.md#start).

Starts the job. You must call this, after having called all the necessary setters.

### QString CommandLauncherJob::workingDirectory() const {#workingDirectory}

Returns the working directory, which was previously set with @c [setWorkingDirectory](kio-commandlauncherjob.md#setWorkingDirectory)().

*See also* [setWorkingDirectory](kio-commandlauncherjob.md#setWorkingDirectory)()
