---
title: "KMountPoint::List Class"
description: "Network transparent access to files and data."
---

# KMountPoint::List Class

Network transparent access to files and data. [More...](#details)

- **Header:** `#include <List>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS KIO)`  
  `target_link_libraries(mytarget PRIVATE KF6::KIOCore)`
- **Inherits:** [QList](https://doc.qt.io/qt-6/qlist.html)

[List of all members, including inherited members](kmountpoint-list-members.md)

## Public Functions

- [KMountPoint::Ptr findByDevice(const QString &device) const](#findByDevice)
- [KMountPoint::Ptr findByMountId(quint64 mountId) const](#findByMountId) (since 6.24)
- [KMountPoint::Ptr findByPath(const QString &path) const](#findByPath)

## Detailed Description {#details}

List of mount points.

## Member Function Documentation {#member-function-documentation}

### KMountPoint::Ptr List::findByDevice(const QString &*device*) const {#findByDevice}

Returns the mount point associated with `device`, i.e. the one where [mountedFrom](kmountpoint.md#mountedFrom)() == `device` (after symlink resolution).

Returns the mountpoint, or `nullptr` if this device doesn't exist or isn't mounted

### \[since 6.24\] KMountPoint::Ptr List::findByMountId(quint64 *mountId*) const {#findByMountId}

Returns the mount point associated with `mountId`

Returns the mountpoint, or `nullptr` if there is no mount point associated with this ID.

This is prefered over looking up a path because it does not have to deal with symlinks.

> **Note:** This is only supported on Linux and returns `nullptr` for all other platforms

> **Warning:** [mountId](kmountpoint.md#mountId) must not be zero

This function was introduced in Qt 6.24.

### KMountPoint::Ptr List::findByPath(const QString &*path*) const {#findByPath}

Find the mountpoint on which resides `path` For instance if /home is a separate partition, findByPath("/home/user/blah") will return /home

`path` the path to check

Returns the mount point of the given file
