---
title: "KIO::DirectorySizeJob Class"
description: "Computes a directory size."
---

# KIO::DirectorySizeJob Class

Computes a directory size. [More...](#details)

- **Header:** `#include <KIO/DirectorySizeJob>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS KIO)`  
  `target_link_libraries(mytarget PRIVATE KF6::KIOCore)`
- **Inherits:** [KIO::Job](kio-job.md)

[List of all members, including inherited members](kio-directorysizejob-members.md)

## Public Functions

- [KIO::filesize\_t totalFiles() const](#totalFiles)
- [KIO::filesize\_t totalSize() const](#totalSize)
- [std::optional\<KIO::filesize\_t\> totalSizeOnDisk() const](#totalSizeOnDisk) (since 6.30)
- [KIO::filesize\_t totalSubdirs() const](#totalSubdirs)

## Detailed Description {#details}

Similar to "du", but doesn't give the same results since we simply sum up the dir and file sizes, whereas du speaks disk blocks.

*See also* [KIO::directorySize](kio-index.md)

## Member Function Documentation {#member-function-documentation}

### KIO::filesize\_t DirectorySizeJob::totalFiles() const {#totalFiles}

Returns the total number of files (counting symlinks to files, sockets and character devices as files) in this directory and all sub-directories

### KIO::filesize\_t DirectorySizeJob::totalSize() const {#totalSize}

Returns how many bytes of data the files we found hold. Directories do not add to it: the room their list of entries needs is not data anybody put there, and it varies wildly between filesystems, which made the same folder report a different size once copied. See [totalSizeOnDisk](kio-directorysizejob.md#totalSizeOnDisk)() for the space everything takes up.

### \[since 6.30\] std::optional\<KIO::filesize\_t\> DirectorySizeJob::totalSizeOnDisk() const {#totalSizeOnDisk}

Returns the space the files and directories we found take up on the storage they live on, which is what the filesystem has allocated to them rather than how many bytes of data they hold. Empty when the protocol has no way to tell, which is anything but local files. Zero is an answer in its own right: a file that is entirely sparse holds data but occupies nothing.

This function was introduced in Qt 6.30.

### KIO::filesize\_t DirectorySizeJob::totalSubdirs() const {#totalSubdirs}

Returns the total number of sub-directories found (not including the directory the search started from and treating symlinks to directories as directories)

## Related Non-Members {#related-non-members}

### KIO::DirectorySizeJob \*directorySize(const KFileItemList &*lstItems*) {#directorySize}

Computes a directory size (by doing a recursive listing). Connect to the result signal (this is the preferred solution to avoid blocking the GUI), or use [exec](../kcoreaddons/kjob.md#exec)() for a synchronous (blocking) calculation.

This one lists the items from `lstItems`. The reason we asks for items instead of just urls, is so that we directly know if the item is a file or a directory, and in case of a file, we already have its size.

### KIO::DirectorySizeJob \*directorySize(const QUrl &*directory*) {#directorySize-1}

Computes a directory size (by doing a recursive listing). Connect to the result signal (this is the preferred solution to avoid blocking the GUI), or use [exec](../kcoreaddons/kjob.md#exec)() for a synchronous (blocking) calculation.

This one lists a single directory.
