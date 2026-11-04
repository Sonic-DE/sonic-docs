---
title: "KCrash Namespace"
description: "This namespace contains functions to handle crashes."
---

# KCrash Namespace

This namespace contains functions to handle crashes. [More...](#details)

- **Header:** `#include <KCrash>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS Crash)`  
  `target_link_libraries(mytarget PRIVATE KF6::Crash)`

## Detailed Description {#details}

It allows you to set a crash handler function that will be called when your application crashes and also provides a default crash handler that implements the following functionality:

- Launches the KDE crash display application (DrKonqi) to let the user report the bug and/or debug it.
- Calls an emergency save function that you can set with [setEmergencySaveFunction](kcrash.md#setEmergencySaveFunction)() to attempt to save the application's data.
- Autorestarts your application.

> **Note:** All the above features are optional and you need to enable them explicitly. By default, the [defaultCrashHandler](kcrash.md#defaultCrashHandler)() will not do anything. However, if you are using KApplication, it will by default enable launching DrKonqi on crashes, unless the –nocrashhandler argument was passed on the command line or the environment variable KDE\_DEBUG is set to any value.

Since 6.27 [KCrash](kcrash-module.md) also supports crash report submissions on Android (API 30+). For this to work the following Android-specific changes are necessary.

In `build.gradle`, add `sentry-android-core` as a dependency:

```cpp
dependencies {
  ...
  implementation 'io.sentry:sentry-android-core:8.43.0'
}
```

In `AndroidManifest.xml`, add a meta-data entry configuring the Sentry DSN for your application:

```cpp
<application ...>
    <meta-data android:name="io.sentry.dsn" android:value="https://<token>@crash-reports.kde.org/<app-id>"/>
</application>
```

## Type Documentation {#type-documentation}

### enum KCrash::CrashFlag {#CrashFlag-enum}

**flags KCrash::CrashFlags**

Options to determine how the default crash handler should behave.

| Constant | Value | Description |
| --- | --- | --- |
| `KCrash::KeepFDs` | `1` | Don't close all file descriptors immediately |
| `KCrash::SaferDialog` | `2` | Start DrKonqi without arbitrary disk access |
| `KCrash::AlwaysDirectly` | `4` | Never try to to start DrKonqi via kdeinit. Use fork() and exec() instead. This enum has been deprecated. This is now the default, and does not need to be set. |
| `KCrash::AutoRestart (since Qt 4.1)` | `8` | autorestart this application. Only sensible for KUniqueApplications |

The `CrashFlags` type is a typedef for `QFlags<CrashFlag>. `It stores an OR combination of `CrashFlag` values.

### KCrash::HandlerType {#HandlerType-typedef}

Typedef for a pointer to a crash handler function. The function's argument is the number of the signal.

## Function Documentation {#function-documentation}

### KCrash::HandlerType KCrash::crashHandler() {#crashHandler}

Returns the installed crash handler.

*See also* [setCrashHandler](kcrash.md#setCrashHandler)()

### void KCrash::defaultCrashHandler(int *signal*) {#defaultCrashHandler}

The default crash handler. Do not call this function directly. Instead, use [setCrashHandler](kcrash.md#setCrashHandler)() to set it as your application's crash handler.

`signal` the signal number

> **Note:** If you implement your own crash handler, you will have to call this function from your implementation if you want to use the features of this namespace.

### KCrash::HandlerType KCrash::emergencySaveFunction() {#emergencySaveFunction}

Returns the currently set emergency save function.

*See also* [setEmergencySaveFunction](kcrash.md#setEmergencySaveFunction)()

### void KCrash::initialize() {#initialize}

Initialize [KCrash](kcrash-module.md).

This does nothing if $KDE\_DEBUG is set.

Call this in your main() after setting up KAboutData to ensure that the crash handler is launched.

### bool KCrash::isDrKonqiEnabled() {#isDrKonqiEnabled}

Returns true if DrKonqi is set to be launched from the crash handler or false otherwise.

### void KCrash::setCrashHandler(KCrash::HandlerType *handler* = defaultCrashHandler) {#setCrashHandler}

Install a function to be called when a crash occurs. A crash occurs when one of the following signals is caught: SIGSEGV, SIGBUS, SIGFPE, SIGILL, SIGABRT.

`handler` this can be one of:

- null, in which case signal catching is disabled (by setting the signal handler for the crash signals to SIG\_DFL)
- a user defined function in the form: static (if in a class) void myCrashHandler(int);
- if handler is omitted, the default crash handler is installed

> **Note:** If you use [setDrKonqiEnabled](kcrash.md#setDrKonqiEnabled)(true), [setEmergencySaveFunction](kcrash.md#setEmergencySaveFunction)(myfunc) or [setFlags](kcrash.md#setFlags)([AutoRestart](kcrash.md#CrashFlag-enum)), you do not need to call this function explicitly. The default crash handler is automatically installed by those functions if needed. However, if you set a custom crash handler, those functions will not change it.

*See also* [crashHandler](kcrash.md#crashHandler)()

### void KCrash::setDrKonqiEnabled(bool *enabled*) {#setDrKonqiEnabled}

Enables or disables launching DrKonqi from the crash handler. By default, launching DrKonqi is enabled when [QCoreApplication](https://doc.qt.io/qt-6/qcoreapplication.html) is created. To disable it:

```cpp
void disableDrKonqi()
{
  KCrash::setDrKonqiEnabled(false);
}
Q_CONSTRUCTOR_FUNCTION(disableDrKonqi)
```

> **Note:** It is the crash handler's responsibility to launch DrKonqi. Therefore, if no crash handler is set, this method also installs the default crash handler to ensure that DrKonqi will be launched.

*See also* [isDrKonqiEnabled](kcrash.md#isDrKonqiEnabled)()

### void KCrash::setEmergencySaveFunction(KCrash::HandlerType *saveFunction* = nullptr) {#setEmergencySaveFunction}

Installs a function which should try to save the application's data.

> **Note:** It is the crash handler's responsibility to call this function. Therefore, if no crash handler is set, the default crash handler is installed to ensure the save function will be called.

`saveFunction` the handler to install

*See also* [emergencySaveFunction](kcrash.md#emergencySaveFunction)()

### \[since 6.11\] void KCrash::setErrorExtraData(const QHash\<QString, QString\> &*details*) {#setErrorExtraData}

Sets the error details to be included in the crash report. These are rendered as extra blobs of data and can any form.

Note that these are subject to event ingestion limits and should be kept at reasonable sizes to prevent event rejection.

This function was introduced in Qt 6.11.

### void KCrash::setErrorMessage(const QString &*message*) {#setErrorMessage}

Allows providing information to be included in the bug report. Prefer setErrorExtraInformation as it is more flexible.

### \[since 6.11\] void KCrash::setErrorTags(const QHash\<QString, QString\> &*details*) {#setErrorTags}

Sets the error tags to be included in the crash report. These are rendered as tags in the crash reporting system.

Note that server-side limits apply to the length of these so you should only put short, sortable data in here.

This function was introduced in Qt 6.11.

### void KCrash::setFlags(KCrash::CrashFlags *flags*) {#setFlags}

Set options to determine how the default crash handler should behave.

`flags` ORed together [CrashFlags](kcrash.md#CrashFlag-enum)

### \[since 6.11\] void KCrash::setGPUData(const QVariantHash &*data*) {#setGPUData}

Sets better GPU data.

By default [KCrash](kcrash-module.md) will try to determine the GPU name, this may however not be accurate data. In particular on multi-gpu systems it may not be possible to determine whether the integrated or dedicated GPU is in use.

You should call this function once you know which GPU will be in use for application. This is a free form string.

Server-side limits may apply; keep it as short as possible.

At least 'name' should be set. Additional supported fields follow Sentry unless documented otherwise.

Supported fields are listed at https://develop.sentry.dev/sdk/data-model/event-payloads/contexts/#gpu-context

This function was introduced in Qt 6.11.
