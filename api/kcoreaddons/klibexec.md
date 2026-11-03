---
title: "KLibexec Namespace"
description: "Utility functions around libexec."
---

# KLibexec Namespace

Utility functions around libexec. [More...](#details)

- Header: KLibexec
- CMake: find\_package(KF6 REQUIRED COMPONENTS CoreAddons) target\_link\_libraries(mytarget PRIVATE KF6::CoreAddons)

## Detailed Description {#details}

## Function Documentation {#function-documentation}

### QStringList KLibexec::kdeFrameworksPaths(const QString &*relativePath*) {#kdeFrameworksPaths}

default paths list for KDE Frameworks

This function returns a fairly opinionated list of paths you can feed into [QStandardPaths](https://doc.qt.io/qt-6/qstandardpaths.html). The list includes various standard locations for Qt and KDE Frameworks and should generally be sensible for most use cases. You may wish to append the absolute installation path as final fallback.

> **Warning:** The precise content and order of the list is an implementation detail and not expected to remain stable!

`relativePath` see [path](klibexec.md#path)() - not all paths get this appended!

Returns [QStringList](https://doc.qt.io/qt-6/qstringlist.html) list of search paths

### QString KLibexec::path(const QString &*relativePath*) {#path}

Absolute libexec path resolved in relative relation to the current shared object.

This function helps locate the absolute libexec path relative to the caller's binary artifact.

For example:

- Your source gets built with prefix /usr
- Your binary artifact's presumed absolute path will be /usr/lib/libfoobar.so
- You call KLibexec::path("libexec/foobar")

Scenario 1: The binaries are actually installed in /usr:

- The function's output is /usr/lib/libexec/foobar/ (resolved relatively from /usr/lib/libfoobar.so)

Scenario 2: The same binaries are installed in /opt (or moved there):

- The function's output is /opt/lib/libexec/foobar/ (resolved relatively from /opt/lib/libfoobar.so)

`relativePath` relative element to append (e.g. "libexec/foobar" resulting in /usr/lib/libexec/foobar/ as output) when called with an empty string you effectively get the directory of your binary artifact.

Returns the absolute libexec path or empty string if it cannot be resolved
