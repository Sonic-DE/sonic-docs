---
title: "KRecentDirs Namespace"
description: "Network transparent access to files and data."
---

# KRecentDirs Namespace

Network transparent access to files and data. [More...](#details)

- Header: KRecentDirs
- CMake: find\_package(KF6 REQUIRED COMPONENTS KIO) target\_link\_libraries(mytarget PRIVATE KF6::KIOCore)

## Detailed Description {#details}

The goal of this namespace is to make sure that, when the user needs to specify a file via the file selection dialog, this dialog will start in the directory most likely to contain the desired files.

This works as follows: Each time the file selection dialog is shown, the programmer can specify a "file-class". The file-dialog will then start with the directory associated with this file-class. When the dialog closes, the directory currently shown in the file-dialog will be associated with the file-class.

A file-class can either start with ':' or with '::'. If it starts with a single ':' the file-class is specific to the current application. If the file-class starts with '::' it is global to all applications.

## Function Documentation {#function-documentation}

### void KRecentDirs::add(const QString &*fileClass*, const QString &*directory*) {#add}

Associates `directory` with `fileClass`

### QString KRecentDirs::dir(const QString &*fileClass*) {#dir}

Returns the most recently used directory associated with this file-class.

### QStringList KRecentDirs::list(const QString &*fileClass*) {#list}

Returns a list of directories associated with this file-class. The most recently used directory is at the front of the list.
