---
title: "KIO::MkpathJob Class"
description: "A KIO job that creates a directory, after creating all parent directories necessary for this."
---

# KIO::MkpathJob Class

A KIO job that creates a directory, after creating all parent directories necessary for this. [More...](#details)

- **Header:** `#include <KIO/MkpathJob>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS KIO)`  
  `target_link_libraries(mytarget PRIVATE KF6::KIOCore)`
- **Inherits:** [KIO::Job](kio-job.md)

[List of all members, including inherited members](kio-mkpathjob-members.md)

## Signals

- [void directoryCreated(const QUrl &url)](#directoryCreated)

## Detailed Description {#details}

*See also* [KIO::mkpath()](kio-index.md), [KIO::mkdir()](kio-index.md)

## Member Function Documentation {#member-function-documentation}

### \[signal\] void MkpathJob::directoryCreated(const QUrl &*url*) {#directoryCreated}

Signals that a directory was created.

## Related Non-Members {#related-non-members}

### KIO::MkpathJob \*mkpath(const QUrl &*url*, const QUrl &*baseUrl* = QUrl(), KIO::JobFlags *flags* = DefaultFlags) {#mkpath}

Creates a directory, creating parent directories as needed. Unlike [KIO::mkdir](kio-mkdirjob.md#mkdir)(), the job will succeed if the directory exists already.

`url` The URL of the directory to create.

`baseUrl` Optionally, the URL to start from, which is known to exist (e.g. the directory currently listed).

`flags` mkpath() supports [HideProgressInfo](kio.md#JobFlag-enum).

If `baseUrl` is not an ancestor of `url`, `baseUrl` will be ignored.

Returns a pointer to the job handling the operation.
