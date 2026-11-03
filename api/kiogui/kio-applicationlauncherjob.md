---
title: "KIO::ApplicationLauncherJob Class"
description: "ApplicationLauncherJob runs an application and watches it while running."
---

# KIO::ApplicationLauncherJob Class

[ApplicationLauncherJob](kio-applicationlauncherjob.md) runs an application and watches it while running. [More...](#details)

- **Header:** `#include <KIO/ApplicationLauncherJob>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS KIO)`  
  `target_link_libraries(mytarget PRIVATE KIOGui)`
- **Inherits:** [KJob](../kcoreaddons/kjob.md)

[List of all members, including inherited members](kio-applicationlauncherjob-members.md)

## Public Types

- [enum ApplicationLauncherJob::RunFlag](#RunFlag-enum)

## Public Functions

- [ApplicationLauncherJob(QObject \*parent = nullptr)](#ApplicationLauncherJob)
- [ApplicationLauncherJob(const KDesktopFileAction &desktopFileAction, QObject \*parent = nullptr)](#ApplicationLauncherJob-1) (since 6.0)
- [ApplicationLauncherJob(const KService::Ptr &service, QObject \*parent = nullptr)](#ApplicationLauncherJob-2)
- [ApplicationLauncherJob(const KServiceAction &serviceAction, QObject \*parent = nullptr)](#ApplicationLauncherJob-3)
- [~ApplicationLauncherJob()](#dtor.ApplicationLauncherJob)
- [qint64 pid() const](#pid)
- [QList\<qint64\> pids() const](#pids)
- [void setRunFlags(KIO::ApplicationLauncherJob::RunFlags runFlags)](#setRunFlags)
- [void setStartupId(const QByteArray &startupId)](#setStartupId)
- [void setSuggestedFileName(const QString &suggestedFileName)](#setSuggestedFileName)
- [void setUrls(const QList\<QUrl\> &urls)](#setUrls)
- [void start()](#start)

## Detailed Description {#details}

It creates a startup notification and finishes it on success or on error (for the taskbar). It also emits an error message if necessary (e.g. "program not found").

When passing multiple URLs to an application that doesn't support opening multiple files, the application will be launched once for each URL.

The job finishes when the application is successfully started. At that point you can query the PID(s).

For error handling, either connect to the [result](../kcoreaddons/kjob.md#result)() signal, or for a simple messagebox on error, you can use:

```cpp
// Since 5.98 use:
job->setUiDelegate(KIO::createDefaultJobUiDelegate(KJobUiDelegate::AutoHandlingEnabled, this));
// For older releases use:
job->setUiDelegate(new KIO::JobUiDelegate(KJobUiDelegate::AutoHandlingEnabled, this));
```

Using JobUiDelegate (which is widgets based) also enables the feature of asking the user in case the executable or desktop file isn't marked as executable. Otherwise the job will just refuse executing such files.

To invoke the open-with dialog (from KIOWidgets), construct an [ApplicationLauncherJob](kio-applicationlauncherjob.md) without any arguments or with a null [KService](../kservice/kservice.md).

## Member Type Documentation {#member-type-documentation}

### enum ApplicationLauncherJob::RunFlag {#RunFlag-enum}

**flags ApplicationLauncherJob::RunFlags**

| Constant | Value | Description |
| --- | --- | --- |
| `KIO::ApplicationLauncherJob::DeleteTemporaryFiles` | `0x1` | The URLs passed to the service will be deleted when it exits (if the URLs are local files) |

The `RunFlags` type is a typedef for `QFlags<RunFlag>. `It stores an OR combination of `RunFlag` values.

## Member Function Documentation {#member-function-documentation}

### \[explicit\] ApplicationLauncherJob::ApplicationLauncherJob(QObject \**parent* = nullptr) {#ApplicationLauncherJob}

Creates an [ApplicationLauncherJob](kio-applicationlauncherjob.md) which will prompt the user for which application to use (via the open-with dialog from KIOWidgets).

`parent` the parent [QObject](https://doc.qt.io/qt-6/qobject.html)

### \[explicit, since 6.0\] ApplicationLauncherJob::ApplicationLauncherJob(const KDesktopFileAction &*desktopFileAction*, QObject \**parent* = nullptr) {#ApplicationLauncherJob-1}

Creates an [ApplicationLauncherJob](kio-applicationlauncherjob.md).

This function was introduced in Qt 6.0.

### \[explicit\] ApplicationLauncherJob::ApplicationLauncherJob(const KService::Ptr &*service*, QObject \**parent* = nullptr) {#ApplicationLauncherJob-2}

Creates an [ApplicationLauncherJob](kio-applicationlauncherjob.md).

`service` the service (application desktop file) to run

`parent` the parent [QObject](https://doc.qt.io/qt-6/qobject.html)

### \[explicit\] ApplicationLauncherJob::ApplicationLauncherJob(const KServiceAction &*serviceAction*, QObject \**parent* = nullptr) {#ApplicationLauncherJob-3}

Creates an [ApplicationLauncherJob](kio-applicationlauncherjob.md).

`serviceAction` the service action to run

`parent` the parent [QObject](https://doc.qt.io/qt-6/qobject.html)

### \[override virtual noexcept\] ApplicationLauncherJob::~ApplicationLauncherJob() {#dtor.ApplicationLauncherJob}

Destructor

Note that jobs auto-delete themselves after emitting result. Deleting/killing the job will not stop the started application.

### qint64 ApplicationLauncherJob::pid() const {#pid}

Returns the PID of the application that was started

Convenience method for [pids](kio-applicationlauncherjob.md#pids)().at(0). You should only use this when specifying zero or one URL, or when you are sure that the application supports opening multiple files. Otherwise use [pids](kio-applicationlauncherjob.md#pids)(). Available after the job emits [result](../kcoreaddons/kjob.md#result)().

### QList\<qint64\> ApplicationLauncherJob::pids() const {#pids}

Returns the PIDs of the applications that were started

Available after the job emits [result](../kcoreaddons/kjob.md#result)().

### void ApplicationLauncherJob::setRunFlags(KIO::ApplicationLauncherJob::RunFlags *runFlags*) {#setRunFlags}

Specifies various flags.

`runFlags` the flags to be set. For instance, whether the URLs are temporary files that should be deleted after execution.

### void ApplicationLauncherJob::setStartupId(const QByteArray &*startupId*) {#setStartupId}

Sets the platform-specific startup id of the application launch.

`startupId` startup id, if any (otherwise "").

For X11, this would be the id for the Startup Notification protocol.

### void ApplicationLauncherJob::setSuggestedFileName(const QString &*suggestedFileName*) {#setSuggestedFileName}

Sets the file name to use in the case of downloading the file to a tempfile in order to give to a non-URL-aware application. Some apps rely on the extension to determine the MIME type of the file. Usually the file name comes from the URL, but in the case of the HTTP Content-Disposition header, we need to override the file name.

`suggestedFileName` the file name

### void ApplicationLauncherJob::setUrls(const QList\<QUrl\> &*urls*) {#setUrls}

Specifies the URLs to be passed to the application.

`urls` list of files (local or remote) to open

Note that when passing multiple URLs to an application that doesn't support opening multiple files, the application will be launched once for each URL.

### \[override virtual\] void ApplicationLauncherJob::start() {#start}

Reimplements: [KJob::start()](../kcoreaddons/kjob.md#start).

Starts the job.

You must call this, after having done all the setters. This is (potentially) a GUI job, never use [exec](../kcoreaddons/kjob.md#exec)(), it would block user interaction.
