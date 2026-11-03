---
title: "KIO::OpenOrExecuteFileInterface Class"
description: "The OpenOrExecuteFileInterface class allows OpenUrlJob to ask the user about how to handle various types of executable files, basically whether to run/execute the file, or in the case of text-based ones (shell scripts and .desktop files) open them as text."
---

# KIO::OpenOrExecuteFileInterface Class

The [OpenOrExecuteFileInterface](kio-openorexecutefileinterface.md) class allows [OpenUrlJob](kio-openurljob.md) to ask the user about how to handle various types of executable files, basically whether to run/execute the file, or in the case of text-based ones (shell scripts and .desktop files) open them as text. [More...](#details)

- **Header:** `#include <KIO/OpenOrExecuteFileInterface>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS KIO)`  
  `target_link_libraries(mytarget PRIVATE KIOGui)`
- **Inherits:** [QObject](https://doc.qt.io/qt-6/qobject.html)

[List of all members, including inherited members](kio-openorexecutefileinterface-members.md)

## Public Functions

- [void promptUserOpenOrExecute(KJob \*job, const QString &mimetype)](#promptUserOpenOrExecute)

## Signals

- [void canceled()](#canceled)
- [void executeFile(bool enable)](#executeFile)

## Protected Functions

- [OpenOrExecuteFileInterface(QObject \*parent = nullptr)](#OpenOrExecuteFileInterface)

## Detailed Description {#details}

This extension mechanism for jobs is similar to [KIO::JobUiDelegateExtension](../kiocore/kio-jobuidelegateextension.md), [OpenWithHandlerInterface](kio-openwithhandlerinterface.md) and UntrustedProgramHandlerInterface.

## Member Function Documentation {#member-function-documentation}

### \[explicit protected\] OpenOrExecuteFileInterface::OpenOrExecuteFileInterface(QObject \**parent* = nullptr) {#OpenOrExecuteFileInterface}

Constructor

### \[signal\] void OpenOrExecuteFileInterface::canceled() {#canceled}

Emitted by [promptUserOpenOrExecute](kio-openorexecutefileinterface.md#promptUserOpenOrExecute)() if user selects cancel.

### \[signal\] void OpenOrExecuteFileInterface::executeFile(bool *enable*) {#executeFile}

Emitted by [promptUserOpenOrExecute](kio-openorexecutefileinterface.md#promptUserOpenOrExecute)() once the user chooses an action.

`enable` `true` if the user selected to execute/run the file or `false` if the user selected to open the file as text (the latter is only valid for shell scripts and .desktop files)

### \[virtual\] void OpenOrExecuteFileInterface::promptUserOpenOrExecute(KJob \**job*, const QString &*mimetype*) {#promptUserOpenOrExecute}

Show a dialog to ask the user how to handle various types of executable files, basically whether to run/execute the file, or in the case of text-based ones (shell scripts and .desktop files) open them as text.

`job` the job calling this. This is useful if you need to get any of its properties

`mimetype` the MIME type of the file being handled

Implementations of this method must emit either [executeFile](kio-openorexecutefileinterface.md#executeFile) or canceled.

The default implementation in this base class simply emits [canceled](kio-openorexecutefileinterface.md#canceled)(). Any application using KIO::JobUiDelegate (from KIOWidgets) will benefit from an automatically registered subclass which implements this method, which in turn uses ExecutableFileOpenDialog (from KIOWidgets).
