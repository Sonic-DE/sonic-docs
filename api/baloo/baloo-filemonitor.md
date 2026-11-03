---
title: "Baloo::FileMonitor Class"
description: "File indexing."
---

# Baloo::FileMonitor Class

File indexing. [More...](#details)

- **Header:** `#include <Baloo/FileMonitor>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS Baloo)`  
  `target_link_libraries(mytarget PRIVATE KF6::Baloo)`
- **Inherits:** [QObject](https://doc.qt.io/qt-6/qobject.html)

[List of all members, including inherited members](baloo-filemonitor-members.md)

## Public Functions

- [FileMonitor(QObject \*parent = nullptr)](#FileMonitor)
- [void addFile(const QString &fileUrl)](#addFile)
- [void addFile(const QUrl &url)](#addFile-1)
- [void clear()](#clear)
- [QStringList files() const](#files)
- [void setFiles(const QStringList &fileList)](#setFiles)

## Signals

- [void fileMetaDataChanged(const QString &fileUrl)](#fileMetaDataChanged)

## Detailed Description {#details}

## Member Function Documentation {#member-function-documentation}

### \[explicit\] FileMonitor::FileMonitor(QObject \**parent* = nullptr) {#FileMonitor}

### void FileMonitor::addFile(const QString &*fileUrl*) {#addFile}

### void FileMonitor::addFile(const QUrl &*url*) {#addFile-1}

### void FileMonitor::clear() {#clear}

### \[signal\] void FileMonitor::fileMetaDataChanged(const QString &*fileUrl*) {#fileMetaDataChanged}

### QStringList FileMonitor::files() const {#files}

*See also* [setFiles](baloo-filemonitor.md#setFiles)()

### void FileMonitor::setFiles(const QStringList &*fileList*) {#setFiles}

*See also* [files](baloo-filemonitor.md#files)()
