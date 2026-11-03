---
title: "KNetworkMounts Class"
description: "Additions to Qt Core."
---

# KNetworkMounts Class

Additions to Qt Core. [More...](#details)

- **Header:** `#include <KNetworkMounts>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS CoreAddons)`  
  `target_link_libraries(mytarget PRIVATE KF6::CoreAddons)`
- **Inherits:** [QObject](https://doc.qt.io/qt-6/qobject.html)

[List of all members, including inherited members](knetworkmounts-members.md)

## Public Types

- [enum KNetworkMounts::KNetworkMountOption](#KNetworkMountOption-enum)
- [enum KNetworkMounts::KNetworkMountsType](#KNetworkMountsType-enum)

## Public Functions

- [void addPath(const QString &path, KNetworkMounts::KNetworkMountsType type)](#addPath)
- [QString canonicalSymlinkPath(const QString &path)](#canonicalSymlinkPath)
- [void clearCache()](#clearCache)
- [bool isEnabled() const](#isEnabled)
- [bool isOptionEnabled(const KNetworkMounts::KNetworkMountOption option, const bool defaultValue = false) const](#isOptionEnabled)
- [bool isOptionEnabledForPath(const QString &path, KNetworkMounts::KNetworkMountOption option)](#isOptionEnabledForPath)
- [bool isSlowPath(const QString &path, KNetworkMounts::KNetworkMountsType type = Any)](#isSlowPath)
- [QStringList paths(KNetworkMounts::KNetworkMountsType type = Any) const](#paths)
- [void setEnabled(bool value)](#setEnabled)
- [void setOption(const KNetworkMounts::KNetworkMountOption option, const bool value)](#setOption)
- [void setPaths(const QStringList &paths, KNetworkMounts::KNetworkMountsType type)](#setPaths)
- [void sync()](#sync)

## Static Public Members

- [KNetworkMounts \*self()](#self)

## Detailed Description {#details}

Performance control on network mounts.

This class provides methods for deciding whether operations on slow network mounts should be performed or not.

Configuration is read from a configuration file network\_mounts in the user's [QStandardPaths::ConfigLocation](https://doc.qt.io/qt-6/qstandardpaths.html#StandardLocation-enum). This file can be filled by using the network mounts performance configuration module or directly via [setEnabled](knetworkmounts.md#setEnabled), [setPaths](knetworkmounts.md#setPaths), [addPath](knetworkmounts.md#addPath) and [setOption](knetworkmounts.md#setOption)

```cpp
KNetworkMounts::self()->setEnabled(true);
KNetworkMounts::self()->setOption(KNetworkMounts::LowSideEffectsOptimizations, true);
KNetworkMounts::self()->addPath(path1, KNetworkMounts::NfsPaths);
KNetworkMounts::self()->addPath(path2, KNetworkMounts::NfsPaths);
KNetworkMounts::self()->setPaths(listOfPaths, KNetworkMounts::SmbPaths);
```

Use [KNetworkMounts](knetworkmounts.md) like this to check if the given url is on a configured slow path and the [KNetworkMountOption](knetworkmounts.md#KNetworkMountOption-enum) [LowSideEffectsOptimizations](knetworkmounts.md#KNetworkMountOption-enum) is enabled:

```cpp
if (KNetworkMounts::self()->isOptionEnabledForPath(url.toLocalFile(),
    KNetworkMounts::LowSideEffectsOptimizations))
{
    // skip operations which are slow on the given url if
    // KNetworkMountOption LowSideEffectsOptimizations is enabled
} else {
    // given url is not configured being slow or the KNetworkMountOption
    // LowSideEffectsOptimizations is not enabled
}
```

If called for the first time, this creates a singleton instance and reads the config file. Subsequent calls just use this instance without reading the config file again.

## Member Type Documentation {#member-type-documentation}

### enum KNetworkMounts::KNetworkMountOption {#KNetworkMountOption-enum}

The KNetworkMountOption enum

| Constant | Value | Description |
| --- | --- | --- |
| `KNetworkMounts::LowSideEffectsOptimizations` | `0` | Don't run KDiskFreeSpaceInfo if slow path. Don't check for manually mounted drives. Don't check with [QFileInfo::isWritable](https://doc.qt.io/qt-6/qfileinfo.html#isWritable) if it is writable, if not yet known, return true. Don't check with [QFileInfo::isReadable](https://doc.qt.io/qt-6/qfileinfo.html#isReadable) if it is readable, return false. Don't check for desktop files just return false. Ignore .hidden files on slow paths. Don't read mime comment from .desktop or .directory files. Don't get the size with [QFileInfo::size](https://doc.qt.io/qt-6/qfileinfo.html#size), just return 0, if not yet known. Don't determine mime type from file content, use file extension. Don't check for desktop files just return false. Don't call [KFileSystemType::fileSystemType](kfilesystemtype.md#fileSystemType) to check if the filesystem is slow, just return true. Don't count files/directories in subdirectories. Don't calculate sizes of subdirectories. Avoid check for dir at Kate startup. |
| `KNetworkMounts::MediumSideEffectsOptimizations` | `1` | Don't return project for dir, avoid QFileInfo().absoluteDir(). Don't search for .kateconfig recursively Ignore recent files on slow paths |
| `KNetworkMounts::StrongSideEffectsOptimizations` | `2` | Turn off symbolic link resolution |
| `KNetworkMounts::KDirWatchDontAddWatches` | `3` | Disables dir watching completely for slow paths, avoids stat() calls on added dirs and subdirs |
| `KNetworkMounts::SymlinkPathsUseCache` | `4` | Cache resolved symlink paths |

### enum KNetworkMounts::KNetworkMountsType {#KNetworkMountsType-enum}

The KNetworkMountsType enum

| Constant | Value | Description |
| --- | --- | --- |
| `KNetworkMounts::NfsPaths` | `0` | NFS paths |
| `KNetworkMounts::SmbPaths` | `1` | SMB paths |
| `KNetworkMounts::SymlinkDirectory` | `2` | Paths to directories which contain symbolic links to network mounts |
| `KNetworkMounts::SymlinkToNetworkMount` | `3` | Paths which are symbolic links to network mounts |
| `KNetworkMounts::Any` | `4` | Any slow path type. Do not use with [setPaths](knetworkmounts.md#setPaths) or [addPath](knetworkmounts.md#addPath) |

## Member Function Documentation {#member-function-documentation}

### void KNetworkMounts::addPath(const QString &*path*, KNetworkMounts::KNetworkMountsType *type*) {#addPath}

Add a path for which optimizations are to take place

`path` the path to add

`type` the type of the path. Do not use Any

*See also* [KNetworkMountsType](knetworkmounts.md#KNetworkMountsType-enum)

### QString KNetworkMounts::canonicalSymlinkPath(const QString &*path*) {#canonicalSymlinkPath}

Resolves a `path` that may contain symbolic links to mounted network shares.

A symlink path is either a directory which contains symbolic links to slow network mounts ([SymlinkDirectory](knetworkmounts.md#KNetworkMountsType-enum)) or a direct symbolic link to a slow network mount ( \* SymlinkToNfsOrSmbPaths).

Example: There are some Samba shares mounted below /mnt. These are paths of type [SmbPaths](knetworkmounts.md#KNetworkMountsType-enum)

```cpp
/mnt/server1/share1
/mnt/server1/share2
/mnt/server2/share3
```

A (logged in) user may have symbolic links to them in his home directory below netshares. The directory /home/user/netshares is a [SymlinkDirectory](knetworkmounts.md#KNetworkMountsType-enum):

```cpp
/home/user/netshares/share1 -> /mnt/server1/share1
/home/user/netshares/share2 -> /mnt/server1/share2
/home/user/netshares/share3 -> /mnt/server2/share3
```

There is a direct symbolic link from /home/user/share1 to /mnt/server1/share1. This is of type SymlinkToNfsOrSmbPaths:

```cpp
/home/user/share1 -> /mnt/server1/share1
```

Both types of symbolic links from symlink paths to the real mounted shares are resolved even if [KNetworkMountOption](knetworkmounts.md#KNetworkMountOption-enum) [StrongSideEffectsOptimizations](knetworkmounts.md#KNetworkMountOption-enum) is enabled.

If the setup is like above a `path`

```cpp
/home/user/netshares/share1/Documents/file.txt
```

would be resolved to

```cpp
/mnt/server1/share1/Documents/file.txt
```

and a `path`

```cpp
/home/user/share1/Documents/file.txt
```

would also be resolved to

```cpp
/mnt/server1/share1/Documents/file.txt
```

Resolved paths are cached in a hash.

`path` the path to resolve

Returns the resolved path or `path` if `path` is not a symlink path or no symlink found

*See also* [KNetworkMountsType](knetworkmounts.md#KNetworkMountsType-enum), [clearCache](knetworkmounts.md#clearCache), [isSlowPath](knetworkmounts.md#isSlowPath)

### void KNetworkMounts::clearCache() {#clearCache}

Clears the canonical symlink path cache

Call this if directory structures on mounted network drives changed. Don't enable the cache ([SymlinkPathsUseCache](knetworkmounts.md#KNetworkMountOption-enum)) if this happens often and the drives are usually accessed via the symlinks. This method exists mainly for the KCM.

*See also* [canonicalSymlinkPath](knetworkmounts.md#canonicalSymlinkPath)

### bool KNetworkMounts::isEnabled() const {#isEnabled}

Query if the performance optimizations are switched on

Returns `true` if on, `false` otherwise

### bool KNetworkMounts::isOptionEnabled(const KNetworkMounts::KNetworkMountOption *option*, const bool *defaultValue* = false) const {#isOptionEnabled}

Query a performance option

`option` the option to query

`defaultValue` the value to return if the option is not configured

Returns `true` if option is on, `false` if not

*See also* [KNetworkMountOption](knetworkmounts.md#KNetworkMountOption-enum)

### bool KNetworkMounts::isOptionEnabledForPath(const QString &*path*, KNetworkMounts::KNetworkMountOption *option*) {#isOptionEnabledForPath}

Query if `path` is configured to be a slow path and `option` is enabled

`path` the path to query

`option` the option to query

Returns `true` if `path` is a configured slow path and option `option` is enabled

### bool KNetworkMounts::isSlowPath(const QString &*path*, KNetworkMounts::KNetworkMountsType *type* = Any) {#isSlowPath}

Query if `path` is configured to be a slow path of type `type`

`path` the path to query

`type` the type to query. If omitted, any type matches

Returns `true` if `path` is a configured slow path of type `type`

This function is also used to determine the filesystem type in [KFileSystemType::fileSystemType](kfilesystemtype.md#fileSystemType) ([KFileSystemType::Smb](kfilesystemtype.md#Type-enum) or [KFileSystemType::Nfs](kfilesystemtype.md#Type-enum)) without an expensive call to stafs(). For this to work the types of paths need to be correctly assigned in setPath or [addPath](knetworkmounts.md#addPath)

### QStringList KNetworkMounts::paths(KNetworkMounts::KNetworkMountsType *type* = Any) const {#paths}

Query the configured paths for which optimizations are to take place

Returns a list of paths

*See also* [setPaths](knetworkmounts.md#setPaths)()

### \[static\] KNetworkMounts \*KNetworkMounts::self() {#self}

Returns (and creates if necessary) the singleton instance

### void KNetworkMounts::setEnabled(bool *value*) {#setEnabled}

Switch the performance optimizations on or off

`value` the value to set

*See also* [isEnabled](knetworkmounts.md#isEnabled)()

### void KNetworkMounts::setOption(const KNetworkMounts::KNetworkMountOption *option*, const bool *value*) {#setOption}

Switch a performance option on or off

`option` the option to change

`value` the value to set

*See also* [KNetworkMountOption](knetworkmounts.md#KNetworkMountOption-enum)

### void KNetworkMounts::setPaths(const QStringList &*paths*, KNetworkMounts::KNetworkMountsType *type*) {#setPaths}

Set the paths for which optimizations are to take place

`paths` the paths to set

`type` the type of paths. Do not use Any

*See also* [paths](knetworkmounts.md#paths)(), [KNetworkMountsType](knetworkmounts.md#KNetworkMountsType-enum)

### void KNetworkMounts::sync() {#sync}

Synchronizes to config file

[QSettings](https://doc.qt.io/qt-6/qsettings.html) synchronization also takes place automatically at regular intervals and from [QSettings](https://doc.qt.io/qt-6/qsettings.html) destructor, see [QSettings::sync](https://doc.qt.io/qt-6/qsettings.html#sync)() documentation.

Calls [QSettings::sync](https://doc.qt.io/qt-6/qsettings.html#sync)()
