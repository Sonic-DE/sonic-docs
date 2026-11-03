---
title: "KIO::SimpleJob Class"
description: "A simple job (one url and one command)."
---

# KIO::SimpleJob Class

A simple job (one url and one command). [More...](#details)

- **Header:** `#include <KIO/SimpleJob>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS KIO)`  
  `target_link_libraries(mytarget PRIVATE KF6::KIOCore)`
- **Inherits:** [KIO::Job](kio-job.md)
- **Inherited By:** [KIO::EmptyTrashJob](kio-emptytrashjob.md), [KIO::FileJob](kio-filejob.md), [KIO::FileSystemFreeSpaceJob](kio-filesystemfreespacejob.md), [KIO::ListJob](kio-listjob.md), [KIO::MkdirJob](kio-mkdirjob.md), [KIO::StatJob](kio-statjob.md), and [KIO::TransferJob](kio-transferjob.md)

[List of all members, including inherited members](kio-simplejob-members.md)  
[Deprecated members](kio-simplejob-obsolete.md)

## Public Functions

- [bool isRedirectionHandlingEnabled() const](#isRedirectionHandlingEnabled)
- [void putOnHold()](#putOnHold)
- [void setRedirectionHandlingEnabled(bool handle)](#setRedirectionHandlingEnabled)
- [const QUrl &url() const](#url)

## Public Slots

- [void slotFinished()](#slotFinished)
- [void slotMetaData(const KIO::MetaData &\_metaData)](#slotMetaData)

## Static Public Members

- [void removeOnHold()](#removeOnHold)

## Detailed Description {#details}

This is the base class for all jobs that are scheduled. Other jobs are high-level jobs ([CopyJob](kio-copyjob.md), [DeleteJob](kio-deletejob.md), [FileCopyJob](kio-filecopyjob.md)...) that manage subjobs but aren't scheduled directly.

## Member Function Documentation {#member-function-documentation}

### bool SimpleJob::isRedirectionHandlingEnabled() const {#isRedirectionHandlingEnabled}

Returns true when redirections are handled internally, the default.

### \[virtual\] void SimpleJob::putOnHold() {#putOnHold}

Abort job. Suspends worker to be reused by another job for the same request.

### \[static\] void SimpleJob::removeOnHold() {#removeOnHold}

Discard suspended worker.

### void SimpleJob::setRedirectionHandlingEnabled(bool *handle*) {#setRedirectionHandlingEnabled}

Set `handle` to false to prevent the internal handling of redirections.

When this flag is set, redirection requests are simply forwarded to the caller instead of being handled internally.

*See also* [isRedirectionHandlingEnabled](kio-simplejob.md#isRedirectionHandlingEnabled)()

### \[virtual protected slot\] void SimpleJob::slotFinished() {#slotFinished}

Called when the worker marks the job as finished.

### \[virtual protected slot\] void SimpleJob::slotMetaData(const KIO::MetaData &*\_metaData*) {#slotMetaData}

MetaData from the worker is received.

`_metaData` the meta data

*See also* [metaData](kio-job.md#metaData)()

### const QUrl &SimpleJob::url() const {#url}

Returns the [SimpleJob](kio-simplejob.md)'s URL

## Related Non-Members {#related-non-members}

### KIO::SimpleJob \*chmod(const QUrl &*url*, int *permissions*) {#chmod}

Changes permissions on a file or directory. See the other chmod in chmodjob.h for changing many files or directories.

`url` The URL of file or directory.

`permissions` The permissions to set.

Returns the job handling the operation.

### KIO::SimpleJob \*chown(const QUrl &*url*, const QString &*owner*, const QString &*group*) {#chown}

Changes ownership and group of a file or directory.

`url` The URL of file or directory.

`owner` the new owner

`group` the new group

Returns the job handling the operation.

### KIO::SimpleJob \*file\_delete(const QUrl &*src*, KIO::JobFlags *flags* = DefaultFlags) {#file_delete}

Delete a single file.

`src` File to delete.

`flags` Can be [HideProgressInfo](kio.md#JobFlag-enum) here

Returns the job handling the operation.

### KIO::SimpleJob \*mount(bool *ro*, const QByteArray &*fstype*, const QString &*dev*, const QString &*point*, KIO::JobFlags *flags* = DefaultFlags) {#mount}

Mount filesystem.

Special job for kio\_file.

`ro` Mount read-only if `true`.

`fstype` File system type (e.g. "ext2", can be empty).

`dev` Device (e.g. /dev/sda0).

`point` Mount point, can be `null`.

`flags` Can be [HideProgressInfo](kio.md#JobFlag-enum) here

Returns the job handling the operation.

### KIO::SimpleJob \*rename(const QUrl &*src*, const QUrl &*dest*, KIO::JobFlags *flags* = DefaultFlags) {#rename}

Rename a file or directory. Warning: this operation fails if a direct renaming is not possible (like with files or dirs on separate partitions) Use move or [file\_move](kio-filecopyjob.md#file_move) in this case.

`src` The original URL

`dest` The final URL

`flags` Can be Overwrite here

Returns the job handling the operation.

### KIO::SimpleJob \*rmdir(const QUrl &*url*) {#rmdir}

Removes a single directory.

The directory is assumed to be empty. The job will fail if the directory is not empty. Use [KIO::del](kio-deletejob.md#del)() ([DeleteJob](kio-deletejob.md)) to delete non-empty directories.

`url` The URL of the directory to remove.

Returns a pointer to the job handling the operation.

### KIO::SimpleJob \*setModificationTime(const QUrl &*url*, const QDateTime &*mtime*) {#setModificationTime}

Changes the modification time on a file or directory.

`url` The URL of file or directory.

`mtime` The modification time to set.

Returns the job handling the operation.

### KIO::SimpleJob \*special(const QUrl &*url*, const QByteArray &*data*, KIO::JobFlags *flags* = DefaultFlags) {#special}

Execute any command that is specific to one worker (protocol).

Examples are : HTTP POST, mount and unmount (kio\_file)

`url` The URL isn't passed to the worker, but is used to know which worker to send it to :-)

`data` Packed data. The meaning is completely dependent on the worker, but usually starts with an int for the command number.

`flags` Can be [HideProgressInfo](kio.md#JobFlag-enum) here

Returns the job handling the operation.

### KIO::SimpleJob \*symlink(const QString &*target*, const QUrl &*dest*, KIO::JobFlags *flags* = DefaultFlags) {#symlink}

Create or move a symlink. This is the lowlevel operation, similar to [file\_copy](kio-filecopyjob.md#file_copy) and [file\_move](kio-filecopyjob.md#file_move). It doesn't do any check (other than those the worker does) and it doesn't show rename and skip dialogs - use [KIO::link](kio-copyjob.md#link) for that.

`target` The string that will become the "target" of the link (can be relative)

`dest` The symlink to create.

`flags` Can be Overwrite and [HideProgressInfo](kio.md#JobFlag-enum)

Returns the job handling the operation.

### KIO::SimpleJob \*unmount(const QString &*point*, KIO::JobFlags *flags* = DefaultFlags) {#unmount}

Unmount filesystem.

Special job for kio\_file.

`point` Point to unmount.

`flags` Can be [HideProgressInfo](kio.md#JobFlag-enum) here

Returns the job handling the operation.
