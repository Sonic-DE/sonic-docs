---
title: "KIO::CopyJob Class"
description: "CopyJob is used to move, copy or symlink files and directories."
---

# KIO::CopyJob Class

[CopyJob](kio-copyjob.md) is used to move, copy or symlink files and directories. [More...](#details)

- **Header:** `#include <KIO/CopyJob>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS KIO)`  
  `target_link_libraries(mytarget PRIVATE KF6::KIOCore)`
- **Inherits:** [KIO::Job](kio-job.md)

[List of all members, including inherited members](kio-copyjob-members.md)

## Public Types

- [enum CopyJob::CopyMode](#CopyMode-enum)

## Public Functions

- [QUrl destUrl() const](#destUrl)
- [bool doResume()](#doResume)
- [bool doSuspend()](#doSuspend)
- [KIO::CopyJob::CopyMode operationMode() const](#operationMode)
- [void setAutoRename(bool autoRename)](#setAutoRename)
- [void setAutoSkip(bool autoSkip)](#setAutoSkip)
- [void setDefaultPermissions(bool b)](#setDefaultPermissions)
- [void setWriteIntoExistingDirectories(bool overwriteAllDirs)](#setWriteIntoExistingDirectories)
- [QList\<QUrl\> srcUrls() const](#srcUrls)

## Signals

- [void copying(KIO::Job \*job, const QUrl &src, const QUrl &dest)](#copying)
- [void copyingDone(KIO::Job \*job, const QUrl &from, const QUrl &to, const QDateTime &mtime, bool directory, bool renamed)](#copyingDone)
- [void copyingLinkDone(KIO::Job \*job, const QUrl &from, const QString &target, const QUrl &to)](#copyingLinkDone)
- [void creatingDir(KIO::Job \*job, const QUrl &dir)](#creatingDir)
- [void linking(KIO::Job \*job, const QString &target, const QUrl &to)](#linking)
- [void moving(KIO::Job \*job, const QUrl &from, const QUrl &to)](#moving)
- [void processedDirs(KIO::Job \*job, unsigned long dirs)](#processedDirs)
- [void processedFiles(KIO::Job \*job, unsigned long files)](#processedFiles)
- [void renamed(KIO::Job \*job, const QUrl &from, const QUrl &to)](#renamed)

## Detailed Description {#details}

Don't create the job directly, but use [KIO::copy](kio-copyjob.md#copy)(), [KIO::move](kio-copyjob.md#move)(), [KIO::link](kio-copyjob.md#link)() and friends.

*See also* [copy](kio-copyjob.md#copy)(), [copyAs](kio-copyjob.md#copyAs)(), [move](kio-copyjob.md#move)(), [moveAs](kio-copyjob.md#moveAs)(), [link](kio-copyjob.md#link)(), [linkAs](kio-copyjob.md#linkAs)()

## Member Type Documentation {#member-type-documentation}

### enum CopyJob::CopyMode {#CopyMode-enum}

Defines the mode of the operation

| Constant |   |
| --- | --- |
| `KIO::CopyJob::Copy` | `0` |
| `KIO::CopyJob::Move` | `1` |
| `KIO::CopyJob::Link` | `2` |

## Member Function Documentation {#member-function-documentation}

### \[signal\] void CopyJob::copying(KIO::Job \**job*, const QUrl &*src*, const QUrl &*dest*) {#copying}

The job is copying a file or directory.

Note: This signal is used for progress dialogs, it's not emitted for every file or directory (this would be too slow), but every 200ms.

`job` the job that emitted this signal

`src` the URL of the file or directory that is currently being copied

`dest` the destination of the current operation

### \[signal\] void CopyJob::copyingDone(KIO::Job \**job*, const QUrl &*from*, const QUrl &*to*, const QDateTime &*mtime*, bool *directory*, bool *renamed*) {#copyingDone}

The job emits this signal when copying or moving a file or directory successfully finished. This signal is mainly for the Undo feature. If you simply want to know when a copy job is done, use [result](../kcoreaddons/kjob.md#result)().

`job` the job that emitted this signal

`from` the source URL

`to` the destination URL

`mtime` the modification time of the source file, hopefully set on the destination file too (when the KIO worker supports it).

`directory` indicates whether a file or directory was successfully copied/moved. true for a directory, false for file

`renamed` indicates that the destination URL was created using a rename operation (i.e. fast directory moving). true if is has been renamed

### \[signal\] void CopyJob::copyingLinkDone(KIO::Job \**job*, const QUrl &*from*, const QString &*target*, const QUrl &*to*) {#copyingLinkDone}

The job is copying or moving a symbolic link, that points to target. The new link is created in `to`. The existing one is/was in `from`. This signal is mainly for the Undo feature.

`job` the job that emitted this signal

`from` the source URL

`target` the target

`to` the destination URL

### \[signal\] void CopyJob::creatingDir(KIO::Job \**job*, const QUrl &*dir*) {#creatingDir}

The job is creating the directory `dir`.

This signal is emitted for every directory being created.

`job` the job that emitted this signal

`dir` the directory that is currently being created

### QUrl CopyJob::destUrl() const {#destUrl}

Returns the destination URL.

### \[override virtual\] bool CopyJob::doResume() {#doResume}

Reimplements: [Job::doResume()](kio-job.md#doResume).

### \[override virtual\] bool CopyJob::doSuspend() {#doSuspend}

Reimplements: [Job::doSuspend()](kio-job.md#doSuspend).

### \[signal\] void CopyJob::linking(KIO::Job \**job*, const QString &*target*, const QUrl &*to*) {#linking}

The job is creating a symbolic link.

Note: This signal is used for progress dialogs, it's not emitted for every file or directory (this would be too slow), but every 200ms.

`job` the job that emitted this signal

`target` the URL of the file or directory that is currently being linked

`to` the destination of the current operation

### \[signal\] void CopyJob::moving(KIO::Job \**job*, const QUrl &*from*, const QUrl &*to*) {#moving}

The job is moving a file or directory.

Note: This signal is used for progress dialogs, it's not emitted for every file or directory (this would be too slow), but every 200ms.

`job` the job that emitted this signal

`from` the URL of the file or directory that is currently being moved

`to` the destination of the current operation

### KIO::CopyJob::CopyMode CopyJob::operationMode() const {#operationMode}

Returns the mode of the operation (copy, move, or link), depending on whether [KIO::copy](kio-copyjob.md#copy)(), [KIO::move](kio-copyjob.md#move)() or [KIO::link](kio-copyjob.md#link)() was called.

### \[signal\] void CopyJob::processedDirs(KIO::Job \**job*, unsigned long *dirs*) {#processedDirs}

Sends the number of processed directories.

`job` the job that emitted this signal

`dirs` the number of processed dirs

### \[signal\] void CopyJob::processedFiles(KIO::Job \**job*, unsigned long *files*) {#processedFiles}

Sends the number of processed files.

`job` the job that emitted this signal

`files` the number of processed files

### \[signal\] void CopyJob::renamed(KIO::Job \**job*, const QUrl &*from*, const QUrl &*to*) {#renamed}

The user chose to rename `from` to `to`.

`job` the job that emitted this signal

`from` the original name

`to` the new name

### void CopyJob::setAutoRename(bool *autoRename*) {#setAutoRename}

Rename files automatically when the destination already exists, instead of the default behavior (interactive mode: showing a dialog to the user, non-interactive mode: aborting with an error). Initially added for a unit test.

### void CopyJob::setAutoSkip(bool *autoSkip*) {#setAutoSkip}

Skip copying or moving any file when the destination already exists, instead of the default behavior (interactive mode: showing a dialog to the user, non-interactive mode: aborting with an error). Initially added for a unit test.

### void CopyJob::setDefaultPermissions(bool *b*) {#setDefaultPermissions}

By default the permissions of the copied files will be those of the source files.

But when copying "template" files to "new" files, people prefer the umask to apply, rather than the template's permissions. For that case, call setDefaultPermissions(true)

### void CopyJob::setWriteIntoExistingDirectories(bool *overwriteAllDirs*) {#setWriteIntoExistingDirectories}

Reuse any directory that already exists, instead of the default behavior (interactive mode: showing a dialog to the user, non-interactive mode: aborting with an error).

### QList\<QUrl\> CopyJob::srcUrls() const {#srcUrls}

Returns the list of source URLs.

## Related Non-Members {#related-non-members}

### KIO::CopyJob \*copy(const QList\<QUrl\> &*src*, const QUrl &*dest*, KIO::JobFlags *flags* = DefaultFlags) {#copy}

Copy a list of file/dirs `src` into a destination directory `dest`.

`src` the list of files and/or directories

`dest` the destination

`flags` copy() supports [HideProgressInfo](kio.md#JobFlag-enum) and Overwrite. Note: Overwrite has the meaning of both "write into existing directories" and "overwrite existing files". However if "dest" exists, then src is copied into a subdir of dest, just like "cp" does.

Returns the job handling the operation

### KIO::CopyJob \*copy(const QUrl &*src*, const QUrl &*dest*, KIO::JobFlags *flags* = DefaultFlags) {#copy-1}

Copy a file or directory `src` into the destination `dest`, which can be a file (including the final filename) or a directory (into which `src` will be copied).

This emulates the cp command completely.

`src` the file or directory to copy `dest` the destination `flags` [copy](kio-copyjob.md#copy)() supports [HideProgressInfo](kio.md#JobFlag-enum) and Overwrite. Note: Overwrite has the meaning of both "write into existing directories" and "overwrite existing files". However if "dest" exists, then src is copied into a subdir of dest, just like "cp" does. Use [copyAs](kio-copyjob.md#copyAs) if you don't want that.

Returns the job handling the operation

*See also* [copyAs](kio-copyjob.md#copyAs)()

### KIO::CopyJob \*copyAs(const QUrl &*src*, const QUrl &*dest*, KIO::JobFlags *flags* = DefaultFlags) {#copyAs}

Copy a file or directory `src` into the destination `dest`, which is the destination name in any case, even for a directory.

As opposed to [copy](kio-copyjob.md#copy)(), this doesn't emulate cp, but is the only way to copy a directory, giving it a new name and getting an error box if a directory already exists with the same name (or writing the contents of `src` into `dest`, when using Overwrite).

`src` the file or directory to copy `dest` the destination `flags` copyAs() supports [HideProgressInfo](kio.md#JobFlag-enum) and Overwrite.

> **Note:** Overwrite has the meaning of both "write into existing directories" and "overwrite existing files".

Returns the job handling the operation

### KIO::CopyJob \*link(const QList\<QUrl\> &*src*, const QUrl &*destDir*, KIO::JobFlags *flags* = DefaultFlags) {#link}

Create several links If the protocols and hosts are the same, a Unix symlink will be created. Otherwise, a .desktop file of Type Link and pointing to the src URL will be created.

`src` The existing files or directories, 'targets' of the link.

`destDir` Destination directory where the links will be created.

`flags` link() supports [HideProgressInfo](kio.md#JobFlag-enum) only

Returns the job handling the operation

### KIO::CopyJob \*link(const QUrl &*src*, const QUrl &*destDir*, KIO::JobFlags *flags* = DefaultFlags) {#link-1}

Create a link. If the protocols and hosts are the same, a Unix symlink will be created. Otherwise, a .desktop file of Type Link and pointing to the src URL will be created.

`src` The existing file or directory, 'target' of the link.

`destDir` Destination directory where the link will be created.

`flags` [link](kio-copyjob.md#link)() supports [HideProgressInfo](kio.md#JobFlag-enum) only

Returns the job handling the operation

### KIO::CopyJob \*linkAs(const QUrl &*src*, const QUrl &*dest*, KIO::JobFlags *flags* = DefaultFlags) {#linkAs}

Create a link. Unlike [link](kio-copyjob.md#link)() this operation will fail when `dest` is an existing directory rather than the final name for the link. If the protocols and hosts are the same, a Unix symlink will be created. Otherwise, a .desktop file of Type Link and pointing to the src URL will be created.

`src` The existing file or directory, 'target' of the link.

`dest` Destination (i.e. the final symlink)

`flags` linkAs() supports [HideProgressInfo](kio.md#JobFlag-enum) only

Returns the job handling the operation

*See also* [link](kio-copyjob.md#link)(), [copyAs](kio-copyjob.md#copyAs)()

### KIO::CopyJob \*move(const QList\<QUrl\> &*src*, const QUrl &*dest*, KIO::JobFlags *flags* = DefaultFlags) {#move}

Moves a list of files or directories `src` to the given destination `dest`.

`src` the list of files or directories to copy

`dest` the destination

`flags` move() supports [HideProgressInfo](kio.md#JobFlag-enum) and Overwrite. Note: Overwrite has the meaning of both "write into existing directories" and "overwrite existing files". However if "dest" exists, then src is copied into a subdir of dest, just like "cp" does.

Returns the job handling the operation

*See also* [copy](kio-copyjob.md#copy)()

### KIO::CopyJob \*move(const QUrl &*src*, const QUrl &*dest*, KIO::JobFlags *flags* = DefaultFlags) {#move-1}

Moves a file or directory `src` to the given destination `dest`.

`src` the file or directory to copy

`dest` the destination

`flags` [move](kio-copyjob.md#move)() supports [HideProgressInfo](kio.md#JobFlag-enum) and Overwrite. Note: Overwrite has the meaning of both "write into existing directories" and "overwrite existing files". However if "dest" exists, then src is copied into a subdir of dest, just like "cp" does.

Returns the job handling the operation

*See also* [copy](kio-copyjob.md#copy)(), [moveAs](kio-copyjob.md#moveAs)()

### KIO::CopyJob \*moveAs(const QUrl &*src*, const QUrl &*dest*, KIO::JobFlags *flags* = DefaultFlags) {#moveAs}

Moves a file or directory `src` to the given destination `dest`. Unlike [move](kio-copyjob.md#move)() this operation will not move `src` into `dest` when `dest` exists: it will either fail, or move the contents of `src` into it if Overwrite is set.

`src` the file or directory to copy

`dest` the destination

`flags` moveAs() supports [HideProgressInfo](kio.md#JobFlag-enum) and Overwrite. Note: Overwrite has the meaning of both "write into existing directories" and "overwrite existing files".

Returns the job handling the operation

*See also* [copyAs](kio-copyjob.md#copyAs)()

### KIO::CopyJob \*trash(const QList\<QUrl\> &*src*, KIO::JobFlags *flags* = DefaultFlags) {#trash}

Trash a list of files or directories. This is currently only supported for local files and directories.

`src` the files to delete

`flags` trash() supports [HideProgressInfo](kio.md#JobFlag-enum) only

Returns the job handling the operation

### KIO::CopyJob \*trash(const QUrl &*src*, KIO::JobFlags *flags* = DefaultFlags) {#trash-1}

Trash a file or directory. This is currently only supported for local files and directories. Use [QUrl::fromLocalFile](https://doc.qt.io/qt-6/qurl.html#fromLocalFile) to create a URL from a local file path.

`src` file to delete

`flags` [trash](kio-copyjob.md#trash)() supports [HideProgressInfo](kio.md#JobFlag-enum) only

Returns the job handling the operation
