---
title: "KMountPoint Class"
description: "The KMountPoint class provides information about mounted and unmounted disks."
---

# KMountPoint Class

The [KMountPoint](kmountpoint.md) class provides information about mounted and unmounted disks. [More...](#details)

- **Header:** `#include <KMountPoint>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS KIO)`  
  `target_link_libraries(mytarget PRIVATE KF6::KIOCore)`
- **Inherits:** [QSharedData](https://doc.qt.io/qt-6/qshareddata.html)

[List of all members, including inherited members](kmountpoint-members.md)

## Public Types

- [enum KMountPoint::DetailsNeededFlag](#DetailsNeededFlag-enum)
- [enum KMountPoint::FileSystemFlag](#FileSystemFlag-enum)

## Public Functions

- [dev\_t deviceId() const](#deviceId)
- [bool isEncryptedFs() const](#isEncryptedFs) (since 6.24)
- [bool isOnNetwork() const](#isOnNetwork)
- [bool isPseudoFs() const](#isPseudoFs) (since 6.24)
- [quint64 mountId() const](#mountId) (since 6.24)
- [QStringList mountOptions() const](#mountOptions)
- [QString mountPoint() const](#mountPoint)
- [QString mountType() const](#mountType)
- [QString mountedFrom() const](#mountedFrom)
- [bool probablySlow() const](#probablySlow)
- [QString realDeviceName() const](#realDeviceName)
- [bool testFileSystemFlag(KMountPoint::FileSystemFlag flag) const](#testFileSystemFlag)

## Static Public Members

- [KMountPoint::Ptr currentMountPointForPath(const QString &path)](#currentMountPointForPath) (since 6.30)
- [KMountPoint::Ptr currentMountPointForUniqueId(quint64 uniqueMountId)](#currentMountPointForUniqueId) (since 6.30)
- [KMountPoint::List currentMountPoints(KMountPoint::DetailsNeededFlags infoNeeded = BasicInfoNeeded)](#currentMountPoints)
- [KMountPoint::List possibleMountPoints(KMountPoint::DetailsNeededFlags infoNeeded = BasicInfoNeeded)](#possibleMountPoints)

## Detailed Description {#details}

It provides a system independent interface to fstab or libmount.

## Member Type Documentation {#member-type-documentation}

### enum KMountPoint::DetailsNeededFlag {#DetailsNeededFlag-enum}

**flags KMountPoint::DetailsNeededFlags**

Flags that specify which additional details should be fetched for each mountpoint.

| Constant | Value | Description |
| --- | --- | --- |
| `KMountPoint::BasicInfoNeeded` | `0` | Only the basic details: [mountedFrom](kmountpoint.md#mountedFrom), [mountPoint](kmountpoint.md#mountPoint), [mountType](kmountpoint.md#mountType). |
| `KMountPoint::NeedMountOptions` | `1` | Also fetch the options used when mounting, see [KMountPoint::mountOptions](kmountpoint.md#mountOptions)(). |
| `KMountPoint::NeedRealDeviceName` | `2` | Also fetch the device name (with symlinks resolved), see [KMountPoint::realDeviceName](kmountpoint.md#realDeviceName)(). |

The `DetailsNeededFlags` type is a typedef for `QFlags<DetailsNeededFlag>. `It stores an OR combination of `DetailsNeededFlag` values.

### enum KMountPoint::FileSystemFlag {#FileSystemFlag-enum}

| Constant | Value |   |
| --- | --- | --- |
| `KMountPoint::SupportsChmod` | `0` |   |
| `KMountPoint::SupportsChown` | `1` |   |
| `KMountPoint::SupportsUTime` | `2` |   |
| `KMountPoint::SupportsSymlinks` | `3` |   |
| `KMountPoint::CaseInsensitive` | `4` |   |
| `KMountPoint::SupportsFileCloning (since Qt 6.30)` | `5` | Copy-on-write filesystem, where a file can be copied with the FICLONE ioctl. |

## Member Function Documentation {#member-function-documentation}

### \[static, since 6.30\] KMountPoint::Ptr KMountPoint::currentMountPointForPath(const QString &*path*) {#currentMountPointForPath}

Returns the current mount point that `path` resides on, using the same cache as [currentMountPointForUniqueId](kmountpoint.md#currentMountPointForUniqueId)(). Falls back to [currentMountPoints](kmountpoint.md#currentMountPoints)().findByPath() when unique mount ids are not available.

Returns the mount point, or nullptr if none matches.

This function was introduced in Qt 6.30.

### \[static, since 6.30\] KMountPoint::Ptr KMountPoint::currentMountPointForUniqueId(quint64 *uniqueMountId*) {#currentMountPointForUniqueId}

Returns the current mount point that has the given unique mount id, as reported by statx() with STATX\_MNT\_ID\_UNIQUE, or nullptr if no current mount has this id.

It is guaranteed to return for any mounted mountpoint on Linux 6.8+.

> **Note:** This is only useful on Linux; elsewhere it re-reads the mount table on every call, like [currentMountPoints](kmountpoint.md#currentMountPoints)().

> **Warning:** uniqueMountId must not be zero.

This function was introduced in Qt 6.30.

*See also* [KIO::UDSEntry::UDS\_MOUNT\_ID](kio-index.md)

### \[static\] KMountPoint::List KMountPoint::currentMountPoints(KMountPoint::DetailsNeededFlags *infoNeeded* = BasicInfoNeeded) {#currentMountPoints}

Returns a list of all current mountpoints.

`infoNeeded` Flags that specify which additional information should be fetched.

> **Note:** This method will return an empty list on Android

### dev\_t KMountPoint::deviceId() const {#deviceId}

Returns the device ID (dev\_t, major, minor) of this mount point. This ID is unique per device (including network mounts).

### \[since 6.24\] bool KMountPoint::isEncryptedFs() const {#isEncryptedFs}

Returns `true` if this mount points to a filesystem that is encrypting its content (e.g. gocryptfs), otherwise returns `false`.

This function was introduced in Qt 6.24.

### bool KMountPoint::isOnNetwork() const {#isOnNetwork}

Returns `true` if this mount point represents a network filesystem (e.g. NFS, CIFS, etc.), otherwise returns `false`.

### \[since 6.24\] bool KMountPoint::isPseudoFs() const {#isPseudoFs}

Returns `true` if this mount points to a pseudo filesystem (e.g. devfs, proc, tmpfs, fuse, etc.), otherwise returns `false`.

This function was introduced in Qt 6.24.

### \[since 6.24\] quint64 KMountPoint::mountId() const {#mountId}

Returns the mount ID of this mount point.

If the system supports MNT\_ID\_UNIQUE, it will be returned. It is guaranteed to be unique until the next boot. If the system doesn't support that, the MNT\_ID property will be returned. It is unique for a point in time, but is not guaranteed to be unique until next boot.

On systems without statmount() (exists since Linux 6.8) this will return 0.

This function was introduced in Qt 6.24.

### QStringList KMountPoint::mountOptions() const {#mountOptions}

Options used to mount the filesystem. Only available if the [NeedMountOptions](kmountpoint.md#DetailsNeededFlag-enum) flag was set.

### QString KMountPoint::mountPoint() const {#mountPoint}

Path where the filesystem is mounted (if you used [currentMountPoints](kmountpoint.md#currentMountPoints)()), or can be mounted (if you used [possibleMountPoints](kmountpoint.md#possibleMountPoints)()).

### QString KMountPoint::mountType() const {#mountType}

Type of filesystem

### QString KMountPoint::mountedFrom() const {#mountedFrom}

Where this filesystem gets mounted from. This can refer to a device, a remote server or something else.

### \[static\] KMountPoint::List KMountPoint::possibleMountPoints(KMountPoint::DetailsNeededFlags *infoNeeded* = BasicInfoNeeded) {#possibleMountPoints}

This function gives a list of all possible mountpoints. (fstab)

`infoNeeded` Flags that specify which additional information should be fetched.

### bool KMountPoint::probablySlow() const {#probablySlow}

Returns `true` if the filesystem is "probably" slow, e.g. a network mount, `false` otherwise.

### QString KMountPoint::realDeviceName() const {#realDeviceName}

Canonical name of the device where the filesystem got mounted from. (Or empty, if not a device) Only available when the [NeedRealDeviceName](kmountpoint.md#DetailsNeededFlag-enum) flag was set.

### bool KMountPoint::testFileSystemFlag(KMountPoint::FileSystemFlag *flag*) const {#testFileSystemFlag}

Checks the capabilities of the filesystem.

`flag` the flag to check

Returns `true` if the filesystem has that flag, false if not

The available flags are:

- [SupportsChmod](kmountpoint.md#FileSystemFlag-enum): returns true if the filesystem supports chmod (e.g. msdos filesystems return false)
- [SupportsChown](kmountpoint.md#FileSystemFlag-enum): returns true if the filesystem supports chown (e.g. msdos filesystems return false)
- SupportsUtime: returns true if the filesystems supports utime (e.g. msdos filesystems return false)
- [SupportsSymlinks](kmountpoint.md#FileSystemFlag-enum): returns true if the filesystems supports symlinks (e.g. msdos filesystems return false)
- [CaseInsensitive](kmountpoint.md#FileSystemFlag-enum): returns true if the filesystem treats "foo" and "FOO" as being the same file (true for msdos filesystems)
- [SupportsFileCloning](kmountpoint.md#FileSystemFlag-enum): returns true on a copy-on-write filesystem, where a file can be copied with the FICLONE ioctl, which only ever works within one filesystem. Such a filesystem may still turn a single request down, XFS for one only clones when it was made with reflink support, so a caller has to be ready for the request to fail and copy the contents instead.
