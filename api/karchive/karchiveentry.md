---
title: "KArchiveEntry Class"
description: "Base class for the archive-file's directory structure."
---

# KArchiveEntry Class

Base class for the archive-file's directory structure. [More...](#details)

- **Header:** `#include <KArchiveEntry>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS Archive)`  
  `target_link_libraries(mytarget PRIVATE KF6::Archive)`
- **Inherited By:** [KArchiveDirectory](karchivedirectory.md) and [KArchiveFile](karchivefile.md)

[List of all members, including inherited members](karchiveentry-members.md)

## Public Functions

- [KArchiveEntry(KArchive \*archive, const QString &name, int access, const QDateTime &date, const QString &user, const QString &group, const QString &symlink)](#KArchiveEntry)
- [QDateTime date() const](#date)
- [QString group() const](#group)
- [bool isDirectory() const](#isDirectory)
- [bool isFile() const](#isFile)
- [QString name() const](#name)
- [mode\_t permissions() const](#permissions)
- [QString symLinkTarget() const](#symLinkTarget)
- [QString user() const](#user)

## Detailed Description {#details}

*See also* [KArchiveFile](karchivefile.md), [KArchiveDirectory](karchivedirectory.md)

## Member Function Documentation {#member-function-documentation}

### KArchiveEntry::KArchiveEntry(KArchive \**archive*, const QString &*name*, int *access*, const QDateTime &*date*, const QString &*user*, const QString &*group*, const QString &*symlink*) {#KArchiveEntry}

Creates a new entry.

`archive` the entries archive

`name` the name of the entry

`access` the permissions in unix format

`date` the date (in seconds since 1970)

`user` the user that owns the entry

`group` the group that owns the entry

`symlink` the symlink, or QString()

### QDateTime KArchiveEntry::date() const {#date}

Creation date of the file.

Returns the creation date

### QString KArchiveEntry::group() const {#group}

Group of the user who created the file.

Returns the group of the file

### \[virtual\] bool KArchiveEntry::isDirectory() const {#isDirectory}

Checks whether the entry is a directory.

Returns true if this entry is a directory

### \[virtual\] bool KArchiveEntry::isFile() const {#isFile}

Checks whether the entry is a file.

Returns true if this entry is a file

### QString KArchiveEntry::name() const {#name}

Name of the file without path.

Returns the file name without path

### mode\_t KArchiveEntry::permissions() const {#permissions}

The permissions and mode flags as returned by the stat() function in st\_mode.

Returns the permissions

### QString KArchiveEntry::symLinkTarget() const {#symLinkTarget}

Symlink if there is one.

Returns the symlink, or QString()

### QString KArchiveEntry::user() const {#user}

User who created the file.

Returns the owner of the file
