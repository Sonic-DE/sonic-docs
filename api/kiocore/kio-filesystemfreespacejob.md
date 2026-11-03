---
title: "KIO::FileSystemFreeSpaceJob Class"
description: "A KIO job that retrieves the total and available size of a filesystem."
---

# KIO::FileSystemFreeSpaceJob Class

A KIO job that retrieves the total and available size of a filesystem. [More...](#details)

- **Header:** `#include <KIO/FileSystemFreeSpaceJob>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS KIO)`  
  `target_link_libraries(mytarget PRIVATE KF6::KIOCore)`
- **Inherits:** [KIO::SimpleJob](kio-simplejob.md)

[List of all members, including inherited members](kio-filesystemfreespacejob-members.md)

## Public Functions

- [KIO::filesize\_t availableSize() const](#availableSize) (since 6.0)
- [KIO::filesize\_t size() const](#size) (since 6.0)

## Detailed Description {#details}

## Member Function Documentation {#member-function-documentation}

### \[since 6.0\] KIO::filesize\_t FileSystemFreeSpaceJob::availableSize() const {#availableSize}

Get available amount of space

This function was introduced in Qt 6.0.

### \[since 6.0\] KIO::filesize\_t FileSystemFreeSpaceJob::size() const {#size}

Get total amount of space

This function was introduced in Qt 6.0.

## Related Non-Members {#related-non-members}

### KIO::FileSystemFreeSpaceJob \*fileSystemFreeSpace(const QUrl &*url*) {#fileSystemFreeSpace}

Get a filesystem's total and available space.

`url` Url to the filesystem.

Returns the job handling the operation.
