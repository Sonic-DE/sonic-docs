---
title: "KIO::MkdirJob Class"
description: "Network transparent access to files and data."
---

# KIO::MkdirJob Class

Network transparent access to files and data. [More...](#details)

- **Header:** `#include <KIO/MkdirJob>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS KIO)`  
  `target_link_libraries(mytarget PRIVATE KF6::KIOCore)`
- **Inherits:** [KIO::SimpleJob](kio-simplejob.md)

[List of all members, including inherited members](kio-mkdirjob-members.md)

## Public Functions

- [void setOwnership(int uid, int gid)](#setOwnership) (since 6.28)

## Signals

- [void permanentRedirection(KIO::Job \*job, const QUrl &fromUrl, const QUrl &toUrl)](#permanentRedirection)
- [void redirection(KIO::Job \*job, const QUrl &url)](#redirection)

## Detailed Description {#details}

A KIO job that creates a directory

*See also* [KIO::mkdir()](kio-index.md)

## Member Function Documentation {#member-function-documentation}

### \[signal\] void MkdirJob::permanentRedirection(KIO::Job \**job*, const QUrl &*fromUrl*, const QUrl &*toUrl*) {#permanentRedirection}

Signals a permanent redirection. The redirection itself is handled internally.

`job` the job that is redirected

`fromUrl` the original URL

`toUrl` the new URL

### \[signal\] void MkdirJob::redirection(KIO::Job \**job*, const QUrl &*url*) {#redirection}

Signals a redirection. Use to update the URL shown to the user. The redirection itself is handled internally.

`job` the job that is redirected

`url` the new url

### \[since 6.28\] void MkdirJob::setOwnership(int *uid*, int *gid*) {#setOwnership}

uid and gid to use for the new directory

Only supported on unix filesystem.

This function was introduced in Qt 6.28.

## Related Non-Members {#related-non-members}

### KIO::MkdirJob \*mkdir(const QUrl &*url*, int *permissions* = -1) {#mkdir}

Creates a single directory.

`url` The URL of the directory to create.

`permissions` The permissions to set after creating the directory (unix-style), -1 for default permissions. Returns a pointer to the job handling the operation.
