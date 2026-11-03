---
title: "KIO::UntrustedProgramHandlerInterface Class"
description: "The UntrustedProgramHandlerInterface class allows ApplicationLauncherJob to prompt the user about an untrusted executable or desktop file."
---

# KIO::UntrustedProgramHandlerInterface Class

The [UntrustedProgramHandlerInterface](kio-untrustedprogramhandlerinterface.md) class allows ApplicationLauncherJob to prompt the user about an untrusted executable or desktop file. [More...](#details)

- **Header:** `#include <KIO/UntrustedProgramHandlerInterface>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS KIO)`  
  `target_link_libraries(mytarget PRIVATE KF6::KIOCore)`
- **Inherits:** [QObject](https://doc.qt.io/qt-6/qobject.html)

[List of all members, including inherited members](kio-untrustedprogramhandlerinterface-members.md)

## Public Functions

- [bool makeServiceFileExecutable(const QString &fileName, QString &errorString)](#makeServiceFileExecutable)
- [bool setExecuteBit(const QString &fileName, QString &errorString)](#setExecuteBit)
- [void showUntrustedProgramWarning(KJob \*job, const QString &programName)](#showUntrustedProgramWarning)

## Signals

- [void result(bool confirmed)](#result)

## Protected Functions

- [UntrustedProgramHandlerInterface(QObject \*parent = nullptr)](#UntrustedProgramHandlerInterface)

## Detailed Description {#details}

This extension mechanism for jobs is similar to [KIO::JobUiDelegateExtension](kio-jobuidelegateextension.md).

The class also provides helper methods to set the execute bit so that the program can be started.

## Member Function Documentation {#member-function-documentation}

### \[explicit protected\] UntrustedProgramHandlerInterface::UntrustedProgramHandlerInterface(QObject \**parent* = nullptr) {#UntrustedProgramHandlerInterface}

Constructor

### bool UntrustedProgramHandlerInterface::makeServiceFileExecutable(const QString &*fileName*, QString &*errorString*) {#makeServiceFileExecutable}

Helper function that attempts to make a desktop file executable. In addition to the execute bit, this includes fixing its first line to ensure that it says \#!/usr/bin/env xdg-open.

`fileName` the full path to the file

`errorString` output parameter so the method can return an error message

Returns `true` on success, `false` on error

### \[signal\] void UntrustedProgramHandlerInterface::result(bool *confirmed*) {#result}

Implementations of this interface must emit result in [showUntrustedProgramWarning](kio-untrustedprogramhandlerinterface.md#showUntrustedProgramWarning).

`confirmed` `true` if the user confirms running this program, `false` on cancel

### bool UntrustedProgramHandlerInterface::setExecuteBit(const QString &*fileName*, QString &*errorString*) {#setExecuteBit}

Helper function that attempts to set execute bit for given file.

`fileName` the full path to the file

`errorString` output parameter so the method can return an error message

Returns `true` on success, `false` on error

### \[virtual\] void UntrustedProgramHandlerInterface::showUntrustedProgramWarning(KJob \**job*, const QString &*programName*) {#showUntrustedProgramWarning}

Show a warning to the user about the program not being trusted for execution. This could be an executable which is not a script and without the execute bit. Or it could be a desktop file outside the standard locations, without the execute bit.

`job` the job calling this. Useful to get the associated window.

`programName` the full path to the executable or desktop file

If this function emits result(true), the caller should then call either [setExecuteBit](kio-untrustedprogramhandlerinterface.md#setExecuteBit) or [makeServiceFileExecutable](kio-untrustedprogramhandlerinterface.md#makeServiceFileExecutable); those helper methods are provided by this class.

The default implementation in this base class simply emits result(false). Any application using [KIO::JobUiDelegate](../kiowidgets/kio-jobuidelegate.md) ([KIOWidgets](../kiowidgets/kiowidgets-module.md)) will benefit from an automatically registered subclass which implements this method using QtWidgets.
