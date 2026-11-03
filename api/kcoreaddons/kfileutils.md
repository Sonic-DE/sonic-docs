---
title: "KFileUtils Namespace"
description: "A namespace for KFileUtils globals."
---

# KFileUtils Namespace

A namespace for [KFileUtils](kfileutils.md) globals. [More...](#details)

- Header: KFileUtils
- CMake: find\_package(KF6 REQUIRED COMPONENTS CoreAddons) target\_link\_libraries(mytarget PRIVATE KF6::CoreAddons)

## Detailed Description {#details}

## Function Documentation {#function-documentation}

### QStringList KFileUtils::findAllUniqueFiles(const QStringList &*dirs*, const QStringList &*nameFilters* = {}) {#findAllUniqueFiles}

Locates all files matching the `nameFilters` in the given `dirs` The returned list does not contain duplicate file names. In case there are multiple files the one which comes first in the dirs list is returned. For example:

```cpp
QStringList dirs = QStandardPaths::locateAll(QStandardPaths::GenericDataLocation, QStringLiteral("krunner/dbusplugins"), QStandardPaths::LocateDirectory);
KFileUtils::findAllUniqueFiles(dirs, QStringList{QStringLiteral("*.desktop")});
```

`location` standard location for the dir

`dir` directory in which the files are located

`nameFilters` filters that get passed to the [QDirIterator](https://doc.qt.io/qt-6/qdiriterator.html) that is used internally to iterate over the files in each dir in the list

Returns list of absolute file paths

### QString KFileUtils::makeSuggestedName(const QString &*oldName*) {#makeSuggestedName}

Given a string, "foo", representing a file/directory (which usually exists already), this function returns a suggested name for a file/directory in the form "foo (1)", "foo (2)" etc.

Unlike the [suggestName](kfileutils.md#suggestName)() method, this function doesn't check if there is a file/directory with the newly suggested name; the idea being that this responsibility falls on the caller, e.g. one can use KIO::stat() to check asynchronously whether the new name already exists (in its parent directory) or not.

### QString KFileUtils::suggestName(const QUrl &*baseURL*, const QString &*oldName*) {#suggestName}

Given a directory path and a string representing a file or directory (which usually exist already), this function returns a suggested name for a file/directory that doesn't exist in `baseURL`.

The suggested file name is of the form "foo (1)", "foo (2)" etc.

For local URLs, this function will check if there is already a file/directory with the new suggested name and will keep incrementing the number in the above format until it finds one that doesn't exist. Note that this function uses a blocking I/O call (using [QFileInfo](https://doc.qt.io/qt-6/qfileinfo.html)) to check the existence of the file/directory, this could be problematic for network mounts (e.g. SMB, NFS) as these are treated as local files by the upstream [QFile](https://doc.qt.io/qt-6/qfile.html) code. An alternative is to use [makeSuggestedName](kfileutils.md#makeSuggestedName)() and use KIO to stat the new file/directory in an asynchronous way.
