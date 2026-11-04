---
title: "KFileSystemType Namespace"
description: "Additions to Qt Core."
---

# KFileSystemType Namespace

Additions to Qt Core. [More...](#details)

- **Header:** `#include <KFileSystemType>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS CoreAddons)`  
  `target_link_libraries(mytarget PRIVATE KF6::CoreAddons)`

## Detailed Description {#details}

Provides utility functions for the type of file systems.

## Type Documentation {#type-documentation}

### enum KFileSystemType::Type {#Type-enum}

| Constant | Value | Description |
| --- | --- | --- |
| `KFileSystemType::Unknown` | `0` | Unknown |
| `KFileSystemType::Nfs` | `1` | NFS or other full-featured networked filesystems (autofs, subfs, cachefs, sshfs) |
| `KFileSystemType::Smb` | `2` | SMB/CIFS mount (networked but with some FAT-like behavior) |
| `KFileSystemType::Fat` | `3` | FAT or similar (msdos, FAT, VFAT) |
| `KFileSystemType::Ramfs` | `4` | RAMDISK mount |
| `KFileSystemType::Other` | `5` | Ext3, Ext4, ReiserFs, and so on. "Normal" local filesystems. |
| `KFileSystemType::Ntfs (since Qt 5.85)` | `6` | NTFS filesystem |
| `KFileSystemType::Exfat (since Qt 5.86)` | `7` | ExFat filesystem |
| `KFileSystemType::Fuse (since Qt 5.100)` | `8` | (Filesystem in USErspace) on a block device, holding a filesystem this machine could not name. The kernel calls this kind of mount fuseblk. |
| `KFileSystemType::FuseNoDev (since Qt 6.30)` | `9` | A fuse mount with no block device behind it, the kind /proc/filesystems marks nodev, which is a different thing from the nodev mount option. The files come from a program rather than from a filesystem on a disk, and that program may be serving a directory that lives on another machine. |

## Function Documentation {#function-documentation}

### QString KFileSystemType::fileSystemName(KFileSystemType::Type *type*) {#fileSystemName}

Returns the possibly translated name of a filesystem corresponding to a value from [KFileSystemType::Type](kfilesystemtype.md#Type-enum).

### KFileSystemType::Type KFileSystemType::fileSystemType(const QString &*path*) {#fileSystemType}

For a given `path`, returns the filesystem type, one of [KFileSystemType::Type](kfilesystemtype.md#Type-enum) values. If the type can't be determined, [KFileSystemType::Unknown](kfilesystemtype.md#Type-enum) is returned.
