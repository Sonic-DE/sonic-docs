---
title: "KIO::OpenWithHandlerInterface Class"
description: "The OpenWithHandlerInterface class allows OpenUrlJob to prompt the user about which application to use to open URLs that do not have an associated application (via the \"Open With\" dialog)."
---

# KIO::OpenWithHandlerInterface Class

The [OpenWithHandlerInterface](kio-openwithhandlerinterface.md) class allows [OpenUrlJob](kio-openurljob.md) to prompt the user about which application to use to open URLs that do not have an associated application (via the "Open With" dialog). [More...](#details)

- **Header:** `#include <KIO/OpenWithHandlerInterface>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS KIO)`  
  `target_link_libraries(mytarget PRIVATE KIOGui)`
- **Inherits:** [QObject](https://doc.qt.io/qt-6/qobject.html)

[List of all members, including inherited members](kio-openwithhandlerinterface-members.md)

## Public Functions

- [void promptUserForApplication(KJob \*job, const QList\<QUrl\> &urls, const QString &mimeType)](#promptUserForApplication)

## Signals

- [void canceled()](#canceled)
- [void handled()](#handled)
- [void serviceSelected(const KService::Ptr &service)](#serviceSelected)

## Protected Functions

- [OpenWithHandlerInterface(QObject \*parent = nullptr)](#OpenWithHandlerInterface)

## Detailed Description {#details}

This extension mechanism for jobs is similar to [KIO::JobUiDelegateExtension](../kiocore/kio-jobuidelegateextension.md) and UntrustedProgramHandlerInterface.

## Member Function Documentation {#member-function-documentation}

### \[explicit protected\] OpenWithHandlerInterface::OpenWithHandlerInterface(QObject \**parent* = nullptr) {#OpenWithHandlerInterface}

Constructor

### \[signal\] void OpenWithHandlerInterface::canceled() {#canceled}

Emitted by [promptUserForApplication](kio-openwithhandlerinterface.md#promptUserForApplication)() if the user canceled the application selection dialog.

### \[signal\] void OpenWithHandlerInterface::handled() {#handled}

Emitted by [promptUserForApplication](kio-openwithhandlerinterface.md#promptUserForApplication)() if it fully handled it including launching the app. This is a special case for the native Windows open-with dialog.

### \[virtual\] void OpenWithHandlerInterface::promptUserForApplication(KJob \**job*, const QList\<QUrl\> &*urls*, const QString &*mimeType*) {#promptUserForApplication}

Show the "Open With" dialog.

`job` the job calling this. Useful to get all its properties

`urls` the URLs to open

`mimeType` the MIME type of the URLs, if known. Can be empty otherwise.

Implementations of this method must emit either [serviceSelected](kio-openwithhandlerinterface.md#serviceSelected) or canceled.

The default implementation in this base class simply emits [canceled](kio-openwithhandlerinterface.md#canceled)(). Any application using KIO::JobUiDelegate (from KIOWidgets) will benefit from an automatically registered subclass which implements this method using KOpenWithDialog.

### \[signal\] void OpenWithHandlerInterface::serviceSelected(const KService::Ptr &*service*) {#serviceSelected}

Emitted by [promptUserForApplication](kio-openwithhandlerinterface.md#promptUserForApplication)() once the user chooses an application.

`service` the application chosen by the user
