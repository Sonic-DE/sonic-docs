---
title: "KArchiveDirectory Class"
description: "A directory in an archive."
---

# KArchiveDirectory Class

A directory in an archive. [More...](#details)

- **Header:** `#include <KArchiveDirectory>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS Archive)`  
  `target_link_libraries(mytarget PRIVATE KF6::Archive)`
- **Inherits:** [KArchiveEntry](karchiveentry.md)

[List of all members, including inherited members](karchivedirectory-members.md)  
[Deprecated members](karchivedirectory-obsolete.md)

## Public Functions

- [KArchiveDirectory(KArchive \*archive, const QString &name, int access, const QDateTime &date, const QString &user, const QString &group, const QString &symlink)](#KArchiveDirectory)
- [bool copyTo(const QString &dest, bool recursive = true) const](#copyTo)
- [QStringList entries() const](#entries)
- [const KArchiveEntry \*entry(const QString &name) const](#entry)
- [const KArchiveFile \*file(const QString &name) const](#file)
- [bool removeEntryV2(KArchiveEntry \*)](#removeEntryV2) (since 6.13)

## Detailed Description {#details}

*See also* [KArchive](karchive-index.md), [KArchiveFile](karchivefile.md)

## Member Function Documentation {#member-function-documentation}

### KArchiveDirectory::KArchiveDirectory(KArchive \**archive*, const QString &*name*, int *access*, const QDateTime &*date*, const QString &*user*, const QString &*group*, const QString &*symlink*) {#KArchiveDirectory}

Creates a new directory entry.

`archive` the entries archive

`name` the name of the entry

`access` the permissions in unix format

`date` the date (in seconds since 1970)

`user` the user that owns the entry

`group` the group that owns the entry

`symlink` the symlink, or QString()

### bool KArchiveDirectory::copyTo(const QString &*dest*, bool *recursive* = true) const {#copyTo}

Extracts all entries in this archive directory to the directory

`dest`.

`dest` the directory to extract to

`recursive` if set to true, subdirectories are extracted as well

Returns true on success, false if the directory (dest + '/' + [name](karchiveentry.md#name)()) couldn't be created

### QStringList KArchiveDirectory::entries() const {#entries}

Returns a list of sub-entries.

Note that the list is not sorted, it's even in random order (due to using a hashtable). Use sort() on the result to sort the list by filename.

Returns the names of all entries in this directory (filenames, no path).

### const KArchiveEntry \*KArchiveDirectory::entry(const QString &*name*) const {#entry}

Returns the entry in the archive with the given name.

The entry could be a file or a directory, use [isFile](karchiveentry.md#isFile)() to find out which one it is.

`name` may be "test1", "mydir/test3", "mydir/mysubdir/test3", etc.

Returns a pointer to the entry in the directory, or a null pointer if there is no such entry.

### const KArchiveFile \*KArchiveDirectory::file(const QString &*name*) const {#file}

Returns the file entry in the archive with the given name.

If the entry exists and is a file, a [KArchiveFile](karchivefile.md) is returned.

Otherwise, a null pointer is returned.

This is a convenience method for [entry](karchivedirectory.md#entry)(), when we know the entry is expected to be a file.

`name` may be "test1", "mydir/test3", "mydir/mysubdir/test3", etc.

Returns a pointer to the file entry in the directory, or a null pointer if there is no such file entry.

### \[since 6.13\] bool KArchiveDirectory::removeEntryV2(*KArchiveEntry \**) {#removeEntryV2}

Removes an entry from the directory.

Returns whether the entry was removed or not.

This function was introduced in Qt 6.13.
