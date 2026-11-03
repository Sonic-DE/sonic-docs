---
title: "KSycoca Class"
description: "Read-only SYstem COnfiguration CAche."
---

# KSycoca Class

Read-only SYstem COnfiguration CAche. [More...](#details)

- **Header:** `#include <KSycoca>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS Service)`  
  `target_link_libraries(mytarget PRIVATE KF6::Service)`
- **Inherits:** [QObject](https://doc.qt.io/qt-6/qobject.html)

[List of all members, including inherited members](ksycoca-members.md)  
[Deprecated members](ksycoca-obsolete.md)

## Public Functions

- [void ensureCacheValid()](#ensureCacheValid)

## Signals

- [void databaseChanged()](#databaseChanged)

## Static Public Members

- [void disableAutoRebuild()](#disableAutoRebuild)
- [bool isAvailable()](#isAvailable)
- [KSycoca \*self()](#self)
- [int version()](#version)

## Detailed Description {#details}

## Member Function Documentation {#member-function-documentation}

### \[signal\] void KSycoca::databaseChanged() {#databaseChanged}

Connect to this to get notified when the database changes.

Example: after creating a .desktop file in [KOpenWithDialog](../kiowidgets/kopenwithdialog.md), it must wait until kbuildsycoca6 finishes until the [KService::Ptr](kservice.md#Ptr-typedef) is available. Other examples: anything that displays a list of apps or plugins to the user and which is always visible (otherwise querying sycoca before showing could be enough).

### \[static\] void KSycoca::disableAutoRebuild() {#disableAutoRebuild}

Disables automatic rebuilding of the cache on service file changes.

Be extremely careful when using this. Only threads that definitely have no use for automatic reloading should use this. Specifically shared runner threads (as seen in the threadweaver framework) can avoid claiming persistent resources this way (e.g. inotify instances on Linux).

### void KSycoca::ensureCacheValid() {#ensureCacheValid}

Ensures the ksycoca database is up to date.

If the database was modified by another process, close it, so the next use reopens it. If the desktop files have been modified more recently than the database, update it.

Update the sycoca file from the files on disk (e.g. desktop files or mimeapps.list). You don't normally have to call this because the next use of [KSycoca](ksycoca.md) (e.g. via KMimeTypeTrader, [KService](kservice-module.md) etc.) will notice that the sycoca database is out of date, by looking a directory modification times. In addition, in a full KDE session, kded monitors directories to detect changes.

This is however useful for GUIs that allow to create a new desktop file and then want to ensure it is available immediately in [KSycoca](ksycoca.md). This is also useful after modifying a mimeapps.list file.

[KBuildSycocaProgressDialog](../kiowidgets/kbuildsycocaprogressdialog.md) can also be used instead of this method, in GUI apps.

### \[static\] bool KSycoca::isAvailable() {#isAvailable}

Returns `true` if the ksycoca database is available

This is usually the case, except if KDE isn't installed yet, or before kded is started.

### \[static\] KSycoca \*KSycoca::self() {#self}

Get or create the only instance of [KSycoca](ksycoca.md) (read-only)

### \[static\] int KSycoca::version() {#version}

Returns the compiled-in version, i.e. the one used when writing a new ksycoca

## Macro Documentation {#macro-documentation}

### KBUILDSYCOCA\_EXENAME {#KBUILDSYCOCA_EXENAME}

Executable name of the kbuildsycoca program
