---
title: "KFileMetaData::WriterPlugin Class"
description: "The WriterPlugin is the base class for all file metadata writers."
---

# KFileMetaData::WriterPlugin Class

The [WriterPlugin](kfilemetadata-writerplugin.md) is the base class for all file metadata writers. [More...](#details)

- **Header:** `#include <KFileMetaData/WriterPlugin>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS FileMetaData)`  
  `target_link_libraries(mytarget PRIVATE KF6::FileMetaData)`
- **Inherits:** [QObject](https://doc.qt.io/qt-6/qobject.html)

[List of all members, including inherited members](kfilemetadata-writerplugin-members.md)

## Public Functions

- [WriterPlugin(QObject \*parent)](#WriterPlugin)
- [void write(const KFileMetaData::WriteData &data)](#write)
- [QStringList writeMimetypes() const](#writeMimetypes)

## Detailed Description {#details}

It is responsible for writing the metadata to a file.

## Member Function Documentation {#member-function-documentation}

### \[explicit\] WriterPlugin::WriterPlugin(QObject \**parent*) {#WriterPlugin}

### \[pure virtual\] void WriterPlugin::write(const KFileMetaData::WriteData &*data*) {#write}

### \[pure virtual\] QStringList WriterPlugin::writeMimetypes() const {#writeMimetypes}
