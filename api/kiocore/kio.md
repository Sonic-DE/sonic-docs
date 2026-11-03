---
title: "KIO Namespace"
description: "A namespace for KIO globals."
---

# KIO Namespace

A namespace for KIO globals. [More...](#details)

- Header: KIO
- CMake: find\_package(KF6 REQUIRED COMPONENTS KIO) target\_link\_libraries(mytarget PRIVATE KF6::KIOCore)

## Detailed Description {#details}

## Classes {#classes}

### class [AskUserActionInterface](kio-askuseractioninterface.md)

The [AskUserActionInterface](kio-askuseractioninterface.md) class allows a [KIO::Job](kio-job.md) to prompt the user for a decision when e.g. copying directories/files and there is a conflict (e.g. a file with the same name already exists at the destination).

### class [AuthInfo](kio-authinfo.md)

A two way messaging class for passing authentication information.

### class [BatchRenameJob](kio-batchrenamejob.md)

A KIO job that renames multiple files in one go.

### class [ChmodJob](kio-chmodjob.md)

This job changes permissions on a list of files or directories, optionally in a recursive manner.

### class [CopyJob](kio-copyjob.md)

[CopyJob](kio-copyjob.md) is used to move, copy or symlink files and directories.

### class [DavJob](kio-davjob.md)

### class [DeleteJob](kio-deletejob.md)

A more complex Job to delete files and directories.

### class [DesktopExecParser](kio-desktopexecparser.md)

Parses the Exec= line from a .desktop file, and process all the '%' placeholders, e.g. handling URLs vs local files.

### class [DirectorySizeJob](kio-directorysizejob.md)

Computes a directory size.

### class [EmptyTrashJob](kio-emptytrashjob.md)

### class [FileCopyJob](kio-filecopyjob.md)

### class [FileJob](kio-filejob.md)

### class [FileSystemFreeSpaceJob](kio-filesystemfreespacejob.md)

A KIO job that retrieves the total and available size of a filesystem.

### class [ForwardingWorkerBase](kio-forwardingworkerbase.md)

Worker that forwards to other workers.

### class [Job](kio-job.md)

### class [JobUiDelegateExtension](kio-jobuidelegateextension.md)

### class [JobUiDelegateFactory](kio-jobuidelegatefactory.md)

A factory for creating job ui delegates.

### class [ListJob](kio-listjob.md)

A [ListJob](kio-listjob.md) is allows you to get the get the content of a directory.

### class [MimeTypeFinderJob](kio-mimetypefinderjob.md)

[MimeTypeFinderJob](kio-mimetypefinderjob.md) finds out the MIME type of a URL.

### class [MimetypeJob](kio-mimetypejob.md)

### class [MkdirJob](kio-mkdirjob.md)

### class [MkpathJob](kio-mkpathjob.md)

A KIO job that creates a directory, after creating all parent directories necessary for this.

### class [NameFinderJob](kio-namefinderjob.md)

[NameFinderJob](kio-namefinderjob.md) finds a valid "New Folder" name.

### class [OpenWith](kio-openwith.md)

Core class for open with style dialog handling.

### class [RestoreJob](kio-restorejob.md)

[RestoreJob](kio-restorejob.md) is used to restore files from the trash.

### class [SimpleJob](kio-simplejob.md)

A simple job (one url and one command).

### class [SpecialJob](kio-specialjob.md)

A class that sends a special command to a KIO worker.

### class [StatJob](kio-statjob.md)

A KIO job that retrieves information about a file or directory.

### class [StoredTransferJob](kio-storedtransferjob.md)

[StoredTransferJob](kio-storedtransferjob.md) is a [TransferJob](kio-transferjob.md) (for downloading or uploading data) that also stores a [QByteArray](https://doc.qt.io/qt-6/qbytearray.html) with the data, making it simpler to use than the standard [TransferJob](kio-transferjob.md).

### class [TransferJob](kio-transferjob.md)

The transfer job pumps data into and/or out of a KIO worker.

### class [UDSEntry](kio-udsentry.md)

Universal Directory Service.

### class [UntrustedProgramHandlerInterface](kio-untrustedprogramhandlerinterface.md)

The [UntrustedProgramHandlerInterface](kio-untrustedprogramhandlerinterface.md) class allows ApplicationLauncherJob to prompt the user about an untrusted executable or desktop file.

### class [WorkerBase](kio-workerbase.md)

[WorkerBase](kio-workerbase.md) is the class to use to implement a worker - simply inherit [WorkerBase](kio-workerbase.md) in your worker.

### class [WorkerConfig](kio-workerconfig.md)

This class manages the configuration for KIO workers based on protocol and host.

### class [WorkerResult](kio-workerresult.md)

The result of a worker call.

## Type Documentation {#type-documentation}

### enum KIO::JobFlag {#JobFlag-enum}

**flags KIO::JobFlags**

Flags for the job properties. Not all flags are supported in all cases. Please see documentation of the calling function!

| Constant | Value | Description |
| --- | --- | --- |
| `KIO::DefaultFlags` | `0` | Show the progress info GUI, no Resume and no Overwrite |
| `KIO::HideProgressInfo` | `1` | Hide progress information dialog, i.e. don't show a GUI. |
| `KIO::Resume` | `2` | When set, automatically append to the destination file if it exists already. WARNING: this is NOT the builtin support for offering the user to resume a previous partial download. The Resume option is much less used, it allows to append to an existing file. This is used by [KIO::put](kio-transferjob.md#put)(), [KIO::file\_copy](kio-filecopyjob.md#file_copy)(), [KIO::file\_move](kio-filecopyjob.md#file_move)() |
| `KIO::Overwrite` | `4` | When set, automatically overwrite the destination if it exists already. This is used by [KIO::rename](kio-simplejob.md#rename)(), [KIO::put](kio-transferjob.md#put)(), [KIO::file\_copy](kio-filecopyjob.md#file_copy)(), [KIO::file\_move](kio-filecopyjob.md#file_move)(), [KIO::symlink](kio-simplejob.md#symlink)(). Otherwise the operation will fail with ERR\_FILE\_ALREADY\_EXIST or ERR\_DIR\_ALREADY\_EXIST |
| `KIO::NoPrivilegeExecution (since Qt 5.43)` | `8` | When set, notifies the worker that application/job does not want privilege execution. So in case of failure due to insufficient privileges show an error without attempting to run the operation as root first. (Deprecated) |

The `JobFlags` type is a typedef for `QFlags<JobFlag>. `It stores an OR combination of `JobFlag` values.

### enum KIO::LoadType {#LoadType-enum}

| Constant |   |
| --- | --- |
| `KIO::Reload` | `0` |
| `KIO::NoReload` | `1` |

### enum KIO::RenameDialog\_Option {#RenameDialog_Option-enum}

**flags KIO::RenameDialog\_Options**

| Constant | Value | Description |
| --- | --- | --- |
| `KIO::RenameDialog_Overwrite` | `1` | We have an existing destination, show details about it and offer to overwrite it |
| `KIO::RenameDialog_OverwriteItself` | `2` | Warn that the current operation would overwrite a file with itself, which is not allowed |
| `KIO::RenameDialog_Skip` | `4` | Offer a "Skip" button, to skip other files too. Requires RenameDialog\_MultipleItems |
| `KIO::RenameDialog_MultipleItems` | `8` | Set if the current operation concerns multiple files, so it makes sense to offer buttons that apply the user's choice to all files/folders |
| `KIO::RenameDialog_Resume` | `16` | Offer a "Resume" button (plus "Resume All" if RenameDialog\_MultipleItems) |
| `KIO::RenameDialog_NoRename` | `64` | Don't offer a "Rename" button |
| `KIO::RenameDialog_DestIsDirectory (since Qt 5.78)` | `128` | The destination is a directory, the dialog updates labels and tooltips accordingly |
| `KIO::RenameDialog_SourceIsDirectory (since Qt 5.78)` | `256` | The source is a directory, the dialog updates labels and tooltips accordingly |

The `RenameDialog_Options` type is a typedef for `QFlags<RenameDialog_Option>. `It stores an OR combination of `RenameDialog_Option` values.

### enum KIO::RenameDialog\_Result {#RenameDialog_Result-enum}

The result of a rename or skip dialog

| Constant | Value |   |
| --- | --- | --- |
| `KIO::Result_Cancel` | `0` |   |
| `KIO::Result_Rename` | `1` |   |
| `KIO::Result_Skip` | `2` |   |
| `KIO::Result_AutoSkip` | `3` |   |
| `KIO::Result_Overwrite` | `4` |   |
| `KIO::Result_OverwriteAll` | `5` |   |
| `KIO::Result_Resume` | `6` |   |
| `KIO::Result_Rename` | `1` |   |
| `KIO::Result_Retry` | `9` |   |
| `KIO::Result_ResumeAll` | `7` |   |
| `KIO::Result_AutoRename` | `8` |   |
| `KIO::Result_OverwriteWhenOlder (since Qt 5.77)` | `10` | Can be returned only when multiple files are passed, Option overwrite is passed and files modification times are valid |
| `KIO::Result_ReplaceInvalidChars (since Qt 5.86)` | `11` | Can be returned if the user selects to replace any character disallowed by the destination filesystem with an underscore "\_". See [SkipDialog\_Option::SkipDialog\_Replace\_Invalid\_Chars](kio.md#SkipDialog_Option-enum) |
| `KIO::Result_ReplaceAllInvalidChars (since Qt 5.86)` | `12` | The same as Result\_ReplaceInvalidChars, but the user selected to automatically replace any invalid character, without being asked about every file/folder |

### enum KIO::SkipDialog\_Option {#SkipDialog_Option-enum}

**flags KIO::SkipDialog\_Options**

\* \* \*

| Constant | Value | Description |
| --- | --- | --- |
| `KIO::SkipDialog_MultipleItems` | `8` | Set if the current operation concerns multiple files, so it makes sense to offer buttons that apply the user's choice to all files/folders. \* |
| `KIO::SkipDialog_Replace_Invalid_Chars (since Qt 5.86)` | `16` | Set if the current operation involves copying files/folders with certain characters in their names that are not supported by the destination filesystem (e.g. VFAT and NTFS disallow "\*" in file/folder names). This will make the SkipDialog show a "Replace" button that can be used to instruct the underlying job to replace any problematic character with an underscore "\_" \* |
| `KIO::SkipDialog_Hide_Retry (since Qt 5.88)` | `32` | Set if the current operation cannot be retried. For example if there is an issue that involves the destination filesystem support, e.g. VFAT and ExFat don't support symlinks, then retrying doesn't make sense. |

The `SkipDialog_Options` type is a typedef for `QFlags<SkipDialog_Option>. `It stores an OR combination of `SkipDialog_Option` values.

### enum KIO::StatDetail {#StatDetail-enum}

**flags KIO::StatDetails**

Describes the fields that a stat command will retrieve

| Constant | Value | Description |
| --- | --- | --- |
| `KIO::StatNoDetails` | `0x0` | No field returned, useful to check if a file exists |
| `KIO::StatBasic` | `0x1` | Filename, access, type, size, linkdest |
| `KIO::StatUser` | `0x2` | uid, gid |
| `KIO::StatTime` | `0x4` |   |
| `KIO::StatResolveSymlink` | `0x8` | Resolve symlinks |
| `KIO::StatAcl` | `0x10` | ACL data |
| `KIO::StatInode` | `0x20` | dev, inode |
| `KIO::StatRecursiveSize (since Qt 5.70)` | `0x40` | Recursive size |
| `KIO::StatMimeType (since Qt 5.82)` | `0x80` | MIME type |
| `KIO::StatDefaultDetails` | `StatBasic | StatUser | StatTime | StatAcl | StatResolveSymlink` | Default StatDetail flag when creating a [StatJob](kio-statjob.md). Equivalent to setting `StatBasic | StatUser | StatTime | StatAcl | StatResolveSymlink` |
| `KIO::StatSubVolId (since Qt 6.23)` | `0x100` | in case the filesystem supports it, return its subvol Identifier |
| `KIO::StatMountId (since Qt 6.23)` | `0x200` | the unique mount identifier, see man statx |
| `KIO::StatTimeNsOffset (since Qt 6.24)` | `0x400 | StatTime` | Stat will provide nanosecond precision offsets when available |
| `KIO::StatSizeOnDisk (since Qt 6.30)` | `0x800` | the space the file takes up on its storage, see UDS\_SIZE\_ON\_DISK. Off by default, since a listing carries one number per entry and most callers only want the size of the data |

The `StatDetails` type is a typedef for `QFlags<StatDetail>. `It stores an OR combination of `StatDetail` values.

*See also* [UDSEntry](kio-udsentry.md)

### UDSEntryList {#UDSEntryList-typedef}

A directory listing is a list of [UDSEntry](kio-udsentry.md) instances.

To list the name and size of all the files in a directory listing you would do:

```cpp
KIO::UDSEntryList::ConstIterator it = entries.begin();
const KIO::UDSEntryList::ConstIterator end = entries.end();
for (; it != end; ++it) {
  const KIO::UDSEntry& entry = *it;
  QString name = entry.stringValue( KIO::UDSEntry::UDS_NAME );
  bool isDir = entry.isDir();
  KIO::filesize_t size = entry.numberValue( KIO::UDSEntry::UDS_SIZE, -1 );
  ...
}
```

## Function Documentation {#function-documentation}

### \[since 6.31\] KIO::BatchRenameJob \*batchRenameWithFunction(const KFileItemList &*items*, const KIO::renameFunctionType *renameFunction*, KIO::JobFlags *flags* = DefaultFlags) {#batchRenameWithFunction}

Renames multiple files at once, like batchRenameWithFunction(const [QList](https://doc.qt.io/qt-6/qlist.html)\<[QUrl](https://doc.qt.io/qt-6/qurl.html)\> &, const renameFunctionType, [JobFlags](kio.md#JobFlag-enum)), but is given the items themselves, so that what they already know is used: a directory has no file name extension and keeps its whole name, whatever protocol its URL uses. With plain URLs that is only found out for local files.

`items` The items to rename.

`renameFunction` A function used to find the new name of each item, given its name without the extension.

Returns a pointer to the job handling the operation.

This function was introduced in Qt 6.31.

### \[since 6.16\] KIO::BatchRenameJob \*batchRenameWithFunction(const QList\<QUrl\> &*srcList*, const KIO::renameFunctionType *renameFunction*, KIO::JobFlags *flags* = DefaultFlags) {#batchRenameWithFunction-1}

Renames multiple files at once. The new names are generated by the passed-in function **\<Unknown command\>`p`** renameFunction.

`srcList` The list of items to rename.

`renameFunction` A function used to find the new name of each input files

Returns a pointer to the job handling the operation.

This function was introduced in Qt 6.16.

### QString KIO::buildErrorString(int *errorCode*, const QString &*errorText*) {#buildErrorString}

Returns a translated error message for `errorCode` using the additional error information provided by `errorText`.

`errorCode` the error code

`errorText` the additional error text

### unsigned int KIO::calculateRemainingSeconds(KIO::filesize\_t *totalSize*, KIO::filesize\_t *processedSize*, KIO::filesize\_t *speed*) {#calculateRemainingSeconds}

Calculates remaining time in seconds from total size, processed size and speed.

`totalSize` total size in bytes

`processedSize` processed size in bytes

`speed` speed in bytes per second

Returns calculated remaining time in seconds

### KIO::ChmodJob \*chmod(const KFileItemList &*lstItems*, int *permissions*, int *mask*, const QString &*newOwner*, const QString &*newGroup*, bool *recursive*, KIO::JobFlags *flags* = DefaultFlags) {#chmod}

Creates a job that changes permissions/ownership on several files or directories, optionally recursively. This version of chmod uses a [KFileItemList](kfileitemlist.md) so that it directly knows what to do with the items. TODO: a version that takes a [QList](https://doc.qt.io/qt-6/qlist.html)\<[QUrl](https://doc.qt.io/qt-6/qurl.html)\>, and a general job that stats each url and returns a [KFileItemList](kfileitemlist.md).

Note that change of ownership is only supported for local files.

Inside directories, the "x" bits will only be changed for files that had at least one "x" bit before, and for directories. This emulates the behavior of chmod +X.

`lstItems` The file items representing several files or directories.

`permissions` the permissions we want to set

`mask` the bits we are allowed to change. For instance, if mask is 0077, we don't change the "user" bits, only "group" and "others".

`newOwner` If non-empty, the new owner for the files

`newGroup` If non-empty, the new group for the files

`recursive` whether to open directories recursively

`flags` We support [HideProgressInfo](kio.md#JobFlag-enum) here

Returns the job handling the operation.

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

### QFile::Permissions KIO::convertPermissions(int *permissions*) {#convertPermissions}

Converts KIO file permissions from mode\_t to QFile::Permissions format.

This is a convenience function for converting KIO permissions parameter from mode\_t to QFile::Permissions.

`permissions` KIO file permissions.

Returns -1 if `permissions` is -1, otherwise its OR'ed QFile::Permission equivalent.

### QString KIO::convertSeconds(unsigned int *seconds*) {#convertSeconds}

Convert @p seconds to a string representing number of days, hours, minutes and seconds

`seconds` number of seconds to convert

Returns string representation in a locale depending format

### QString KIO::convertSize(KIO::filesize\_t *size*) {#convertSize}

Converts `size` from bytes to the string representation.

`size` size in bytes

Returns converted size as a string - e.g. 123.4 KiB , 12.0 MiB

### QString KIO::convertSizeFromKiB(KIO::filesize\_t *kibSize*) {#convertSizeFromKiB}

Converts size from kibi-bytes (2^10) to the string representation.

`kibSize` size in kibi-bytes (2^10)

Returns converted size as a string - e.g. 123.4 KiB , 12.0 MiB

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

### KJobUiDelegate \*createDefaultJobUiDelegate() {#createDefaultJobUiDelegate}

Convenience method: use default factory, if there's one, to create a delegate and return it.

### KJobUiDelegate \*createDefaultJobUiDelegate(KJobUiDelegate::Flags *flags*, QWidget \**window*) {#createDefaultJobUiDelegate-1}

Convenience method: use default factory, if there's one, to create a delegate and return it.

### \[since 6.27.0\] KIO::DavJob \*davMkCol(const QUrl &*url*, const QString &*properties*, KIO::JobFlags *flags* = DefaultFlags) {#davMkCol}

Creates a new [DavJob](kio-davjob.md) that issues a MKCOL command.

`url` the URL of the resource

`properties` a MKCOL document that describes the request to make

`flags` We support [HideProgressInfo](kio.md#JobFlag-enum) here

Returns the new [DavJob](kio-davjob.md)

This function was introduced in Qt 6.27.0.

### KIO::DavJob \*davPropFind(const QUrl &*url*, const QString &*properties*, const QString &*depth*, KIO::JobFlags *flags* = DefaultFlags) {#davPropFind}

Creates a new [DavJob](kio-davjob.md) that issues a PROPFIND command. PROPFIND retrieves the properties of the resource identified by the given `url`.

`url` the URL of the resource

`properties` a propfind document that describes the properties that should be retrieved

`depth` the depth of the request. Can be "0", "1" or "infinity"

`flags` We support [HideProgressInfo](kio.md#JobFlag-enum) here

Returns the new [DavJob](kio-davjob.md)

### KIO::DavJob \*davPropPatch(const QUrl &*url*, const QString &*properties*, KIO::JobFlags *flags* = DefaultFlags) {#davPropPatch}

Creates a new [DavJob](kio-davjob.md) that issues a PROPPATCH command. PROPPATCH sets the properties of the resource identified by the given `url`.

`url` the URL of the resource

`properties` a PROPPACTCH document that describes the properties that should be modified and its new values

`flags` We support [HideProgressInfo](kio.md#JobFlag-enum) here

Returns the new [DavJob](kio-davjob.md)

### KIO::DavJob \*davReport(const QUrl &*url*, const QString &*report*, const QString &*depth*, KIO::JobFlags *flags* = DefaultFlags) {#davReport}

Creates a new [DavJob](kio-davjob.md) that issues a REPORT command.

`url` the URL of the resource

`report` a REPORT document that describes the request to make

`depth` the depth of the request. Can be "0", "1" or "infinity"

`flags` We support [HideProgressInfo](kio.md#JobFlag-enum) here

Returns the new [DavJob](kio-davjob.md)

### KIO::DavJob \*davSearch(const QUrl &*url*, const QString &*nsURI*, const QString &*qName*, const QString &*query*, KIO::JobFlags *flags* = DefaultFlags) {#davSearch}

Creates a new [DavJob](kio-davjob.md) that issues a SEARCH command.

`url` the URL of the resource

`nsURI` the URI of the search method's qualified name

`qName` the local part of the search method's qualified name

`query` the search string

`flags` We support [HideProgressInfo](kio.md#JobFlag-enum) here

Returns the new [DavJob](kio-davjob.md)

### QString KIO::decodeFileName(const QString &*str*) {#decodeFileName}

Decodes (from the filename to the text displayed) This doesn't do anything anymore, it used to do the opposite of [encodeFileName](kio.md#encodeFileName) when [encodeFileName](kio.md#encodeFileName) was using %2F for '/'.

`str` the file name to decode

Returns the decoded file name

### KIO::JobUiDelegateExtension \*defaultJobUiDelegateExtension() {#defaultJobUiDelegateExtension}

Returns the default job UI delegate extension to be used by all KIO jobs (in which [HideProgressInfo](kio.md#JobFlag-enum) is not set) Can return nullptr, if no kio GUI library is loaded.

*See also* [setDefaultJobUiDelegateExtension](kio-jobuidelegateextension.md#setDefaultJobUiDelegateExtension)()

### \[since 6.0\] KIO::JobUiDelegateFactory \*defaultJobUiDelegateFactory() {#defaultJobUiDelegateFactory}

Returns the default job UI delegate factory to be used by all KIO jobs (in which [HideProgressInfo](kio.md#JobFlag-enum) is not set) Can return nullptr, if no kio GUI library is loaded.

This function was introduced in Qt 6.0.

*See also* [setDefaultJobUiDelegateFactory](kio-jobuidelegatefactory.md#setDefaultJobUiDelegateFactory)()

### KIO::DeleteJob \*del(const QList\<QUrl\> &*src*, KIO::JobFlags *flags* = DefaultFlags) {#del}

Deletes a list of files or directories.

`src` the files to delete

`flags` We support [HideProgressInfo](kio.md#JobFlag-enum) here

Returns the job handling the operation

### KIO::DeleteJob \*del(const QUrl &*src*, KIO::JobFlags *flags* = DefaultFlags) {#del-1}

Delete a file or directory.

`src` file to delete

`flags` We support [HideProgressInfo](kio.md#JobFlag-enum) here

Returns the job handling the operation

### template \<typename T\> T delegateExtension(KJob \**job*) {#delegateExtension}

Returns the child of the job's uiDelegate() that implements the given extension, or nullptr if none was found (or if the job had no uiDelegate).

### KIO::DirectorySizeJob \*directorySize(const KFileItemList &*lstItems*) {#directorySize}

Computes a directory size (by doing a recursive listing). Connect to the result signal (this is the preferred solution to avoid blocking the GUI), or use [exec](../kcoreaddons/kjob.md#exec)() for a synchronous (blocking) calculation.

This one lists the items from `lstItems`. The reason we asks for items instead of just urls, is so that we directly know if the item is a file or a directory, and in case of a file, we already have its size.

### KIO::DirectorySizeJob \*directorySize(const QUrl &*directory*) {#directorySize-1}

Computes a directory size (by doing a recursive listing). Connect to the result signal (this is the preferred solution to avoid blocking the GUI), or use [exec](../kcoreaddons/kjob.md#exec)() for a synchronous (blocking) calculation.

This one lists a single directory.

### KIO::EmptyTrashJob \*emptyTrash() {#emptyTrash}

Empties the trash.

Returns a pointer to the job handling the operation.

### QString KIO::encodeFileName(const QString &*str*) {#encodeFileName}

Encodes (from the text displayed to the real filename) This translates '/' into a "unicode fraction slash", [QChar](https://doc.qt.io/qt-6/qchar.html)(0x2044). Used by [KIO::link](kio-copyjob.md#link), for instance.

`str` the file name to encode

Returns the encoded file name

### QString KIO::favIconForUrl(const QUrl &*url*) {#favIconForUrl}

Return the "favicon" (see http://www.favicon.com) for the given `url`, if available. Does NOT attempt to download the favicon, it only returns one that is already available.

If unavailable, returns QString(). Use [KIO::FavIconRequestJob](../kiogui/kio-faviconrequestjob.md) instead of this method if you can wait for the favicon to be downloaded.

`url` the URL of the favicon

Returns the path to the icon (to be passed to QIcon()), or QString()

### KIO::FileSystemFreeSpaceJob \*fileSystemFreeSpace(const QUrl &*url*) {#fileSystemFreeSpace}

Get a filesystem's total and available space.

`url` Url to the filesystem.

Returns the job handling the operation.

### KIO::FileCopyJob \*file\_copy(const QUrl &*src*, const QUrl &*dest*, KIO::JobFlags *flags*) {#file_copy}

Overload for catching code mistakes. Do NOT call this method (it is not implemented), insert a value for permissions (-1 by default) before the [JobFlags](kio.md#JobFlag-enum).

### KIO::FileCopyJob \*file\_copy(const QUrl &*src*, const QUrl &*dest*, int *permissions* = -1, KIO::JobFlags *flags* = DefaultFlags) {#file_copy-1}

Copy a single file.

Uses either [WorkerBase::copy](kio-workerbase.md#copy)() if the worker supports that or [get](kio-transferjob.md#get)() and [put](kio-transferjob.md#put)() otherwise.

`src` Where to get the file

`dest` Where to put the file

`permissions` the file mode permissions to set on `dest`; if this is -1 (the default) no special permissions will be set on `dest`, i.e. it'll have the default system permissions for newly created files, and the owner and group permissions are not preserved.

`flags` Can be [JobFlag::HideProgressInfo](kio.md#JobFlag-enum), Overwrite and Resume here WARNING: Setting [JobFlag::Resume](kio.md#JobFlag-enum) means that the data will be appended to `dest` if `dest` exists

Returns the job handling the operation

### KIO::SimpleJob \*file\_delete(const QUrl &*src*, KIO::JobFlags *flags* = DefaultFlags) {#file_delete}

Delete a single file.

`src` File to delete.

`flags` Can be [HideProgressInfo](kio.md#JobFlag-enum) here

Returns the job handling the operation.

### KIO::FileCopyJob \*file\_move(const QUrl &*src*, const QUrl &*dest*, int *permissions* = -1, KIO::JobFlags *flags* = DefaultFlags) {#file_move}

Move a single file.

Use either [WorkerBase::rename](kio-workerbase.md#rename)() if the worker supports that, or [copy](kio-copyjob.md#copy)() and [del](kio-deletejob.md#del)() otherwise, or eventually [get](kio-transferjob.md#get)() & [put](kio-transferjob.md#put)() & [del](kio-deletejob.md#del)()

`src` Where to get the file

`dest` Where to put the file

`permissions` the file mode permissions to set on `dest`; if this is -1 (the default), no special permissions are set on `dest`, i.e. it'll have the default system permissions for newly created files, and the owner and group permissions are not preserved.

`flags` Can be [HideProgressInfo](kio.md#JobFlag-enum), Overwrite and Resume here WARNING: Setting [JobFlag::Resume](kio.md#JobFlag-enum) means that the data will be appended to `dest` if `dest` exists

Returns the job handling the operation

### KIO::TransferJob \*get(const QUrl &*url*, KIO::LoadType *reload* = NoReload, KIO::JobFlags *flags* = DefaultFlags) {#get}

Get (means: read). This is the job to use in order to "download" a file into memory. The worker emits the data through the [data](kio-transferjob.md#data)() signal.

Special case: if you want to determine the MIME type of the file first, and then read it with the appropriate component, you can still use a KIO::get() directly. When that job emits the mimeType signal, (which is guaranteed to happen before it emits any data), put the job on hold:

```cpp
job->putOnHold();
```

and forget about the job. The next time someone does a KIO::get() on the same URL (even in another process) this job will be resumed. This saves KIO from doing two requests to the server.

`url` the URL of the file

`reload` Reload to reload the file, [NoReload](kio.md#LoadType-enum) if it can be taken from the cache

`flags` Can be [HideProgressInfo](kio.md#JobFlag-enum) here

Returns the job handling the operation.

### KJobTrackerInterface \*KIO::getJobTracker() {#getJobTracker}

Returns the job tracker to be used by all KIO jobs (in which [HideProgressInfo](kio.md#JobFlag-enum) is not set)

### KIO::TransferJob \*http\_delete(const QUrl &*url*, KIO::JobFlags *flags* = DefaultFlags) {#http_delete}

HTTP DELETE.

Though this function servers the same purpose as [KIO::file\_delete](kio-simplejob.md#file_delete), unlike [file\_delete](kio-simplejob.md#file_delete) it accommodates HTTP specific actions such as redirections.

`url` url resource to delete.

`flags` Can be [HideProgressInfo](kio.md#JobFlag-enum) here

Returns the job handling the operation.

### KIO::TransferJob \*http\_post(const QUrl &*url*, const QByteArray &*postData*, KIO::JobFlags *flags* = DefaultFlags) {#http_post}

HTTP POST (for form data).

Example:

```cpp
job = KIO::http_post( url, postData, KIO::HideProgressInfo );
job->addMetaData("content-type", contentType );
```

`postData` is the data that you want to send and

`contentType` is the complete HTTP header line that specifies the content's MIME type, for example "Content-Type: text/xml".

You MUST specify content-type!

Often `contentType` is "Content-Type: application/x-www-form-urlencoded" and the `postData` is then an ASCII string (without null-termination!) with characters like space, linefeed and percent escaped like %20, %0A and %25.

`url` Where to write the data.

`postData` Encoded data to post.

`flags` Can be [HideProgressInfo](kio.md#JobFlag-enum) here

Returns the job handling the operation.

### KIO::TransferJob \*http\_post(const QUrl &*url*, QIODevice \**device*, qint64 *size* = -1, KIO::JobFlags *flags* = DefaultFlags) {#http_post-1}

HTTP POST.

This function, unlike the one that accepts a [QByteArray](https://doc.qt.io/qt-6/qbytearray.html), accepts an IO device from which to read the encoded data to be posted to the server in order to to avoid holding the content of very large post requests, e.g. multimedia file uploads, in memory.

`url` Where to write the data.

`device` the device to read from

`size` Size of the encoded post data.

`flags` Can be [HideProgressInfo](kio.md#JobFlag-enum) here

Returns the job handling the operation.

### QString KIO::iconNameForUrl(const QUrl &*url*) {#iconNameForUrl}

Return the icon name for a URL. Most of the time this returns the MIME type icon, but also has fallback to favicon and protocol-specific icon.

Pass this to QIcon::fromTheme().

### QString KIO::itemsSummaryString(uint *items*, uint *files*, uint *dirs*, KIO::filesize\_t *size*, bool *showSize*) {#itemsSummaryString}

Helper for showing information about a set of files and directories `items` the number of items (= @p files + @p dirs + number of symlinks :)

`files` the number of files

`dirs` the number of dirs

`size` the sum of the size of the @p files

`showSize` whether to show the size in the result

Returns the summary string

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

### KIO::ListJob \*listDir(const QUrl &*url*, KIO::JobFlags *flags* = DefaultFlags, ListJob::ListFlags *listFlags* = ListJob::ListFlag::IncludeHidden) {#listDir}

List the contents of `url`, which is assumed to be a directory.

"." and ".." are returned, filter them out if you don't want them.

`url` the url of the directory

`flags` Can be [HideProgressInfo](kio.md#JobFlag-enum) here

`listFlags` Can be used to control whether hidden files are included

Returns the job handling the operation.

### KIO::ListJob \*listRecursive(const QUrl &*url*, KIO::JobFlags *flags* = DefaultFlags, ListJob::ListFlags *listFlags* = ListJob::ListFlag::IncludeHidden) {#listRecursive}

The same as the previous method, but recurses subdirectories. Directory links are not followed.

"." and ".." are returned but only for the toplevel directory. Filter them out if you don't want them.

`url` the url of the directory

`flags` Can be [HideProgressInfo](kio.md#JobFlag-enum) here

`listFlags` Can be used to control whether hidden files are included

Returns the job handling the operation.

### KIO::MimetypeJob \*mimetype(const QUrl &*url*, KIO::JobFlags *flags* = DefaultFlags) {#mimetype}

Find MIME type for one file or directory.

If you are going to download the file right after determining its MIME type, then don't use this, prefer using a [KIO::get](kio-transferjob.md#get)() job instead. See the note about putting the job on hold once the MIME type is determined.

`url` the URL of the file

`flags` Can be [HideProgressInfo](kio.md#JobFlag-enum) here

Returns the job handling the operation.

### KIO::MkdirJob \*mkdir(const QUrl &*url*, int *permissions* = -1) {#mkdir}

Creates a single directory.

`url` The URL of the directory to create.

`permissions` The permissions to set after creating the directory (unix-style), -1 for default permissions. Returns a pointer to the job handling the operation.

### KIO::MkpathJob \*mkpath(const QUrl &*url*, const QUrl &*baseUrl* = QUrl(), KIO::JobFlags *flags* = DefaultFlags) {#mkpath}

Creates a directory, creating parent directories as needed. Unlike [KIO::mkdir](kio-mkdirjob.md#mkdir)(), the job will succeed if the directory exists already.

`url` The URL of the directory to create.

`baseUrl` Optionally, the URL to start from, which is known to exist (e.g. the directory currently listed).

`flags` mkpath() supports [HideProgressInfo](kio.md#JobFlag-enum).

If `baseUrl` is not an ancestor of `url`, `baseUrl` will be ignored.

Returns a pointer to the job handling the operation.

### KIO::StatJob \*mostLocalUrl(const QUrl &*url*, KIO::JobFlags *flags* = DefaultFlags) {#mostLocalUrl-1}

Tries to map a local URL for the given URL, using a KIO job. This only makes sense for protocols that have Class ":local" (such protocols most likely have KIO workers that set [UDSEntry::UDS\_LOCAL\_PATH](kio-udsentry.md#StandardFieldTypes-enum)); ideally you should check the URL protocol Class before creating a [StatJob](kio-statjob.md). See [KProtocolInfo::protocolClass](kprotocolinfo.md#protocolClass)().

Starts a (stat) job for determining the "most local URL" for a given URL. Retrieve the result with [StatJob::mostLocalUrl](kio-statjob.md#mostLocalUrl) in the result slot.

`url` The URL we are stat'ing.

Sample usage:

Here the KIO worker name is "foo", which for example could be:

- "desktop", "fonts", "kdeconnect", these have class ":local"
- "ftp", "sftp", "smb", these have class ":internet"

```cpp
QUrl url(QStringLiteral("foo://bar/");
if (url.isLocalFile()) { // If it's a local URL, there is no need to stat
   [...]
} else if (KProtocolInfo::protocolClass(url.scheme()) == QLatin1String(":local")) {
    // Not a local URL, but if the protocol class is ":local", we may be able to stat
    // and get a "most local URL"
    auto *job = KIO::mostLocalUrl(url);
    job->uiDelegate()->setWindow(this);
    connect(job, &KJob::result, this, &MyClass::slotMostLocalUrlResult);
    [...]
    // And in slotMostLocalUrlResult(KJob *job)
    if (job->error()) {
        [...] // Doesn't exist, ideally show an error message
    } else {
        const QUrl localUrl = job->mostLocalUrl();
        // localUrl = file:///local/path/to/bar/
        [...]
    }
}
```

### KIO::SimpleJob \*mount(bool *ro*, const QByteArray &*fstype*, const QString &*dev*, const QString &*point*, KIO::JobFlags *flags* = DefaultFlags) {#mount}

Mount filesystem.

Special job for kio\_file.

`ro` Mount read-only if `true`.

`fstype` File system type (e.g. "ext2", can be empty).

`dev` Device (e.g. /dev/sda0).

`point` Mount point, can be `null`.

`flags` Can be [HideProgressInfo](kio.md#JobFlag-enum) here

Returns the job handling the operation.

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

### QString KIO::number(KIO::filesize\_t *size*) {#number}

Converts a size to a string representation Not unlike [QString::number](https://doc.qt.io/qt-6/qstring.html#number)(...)

`size` size in bytes

Returns converted size as a string - e.g. 123456789

### KIO::FileJob \*open(const QUrl &*url*, QIODevice::OpenMode *mode*) {#open-1}

Open ( random access I/O )

The file-job emits [open](kio-filejob.md#open)() when opened

On error the [open](kio-filejob.md#open)() signal is not emitted. To catch errors please connect to the [result](../kcoreaddons/kjob.md#result)() signal.

`url` the URL of the file

`mode` the access privileges: see OpenMode

Returns the file-handling job. It will never return 0. Errors are handled asynchronously (emitted as signals).

### KIO::TransferJob \*put(const QUrl &*url*, int *permissions*, KIO::JobFlags *flags* = DefaultFlags) {#put}

Put (means: write)

`url` Where to write data.

`permissions` May be -1. In this case no special permission mode is set.

`flags` Can be [HideProgressInfo](kio.md#JobFlag-enum), Overwrite and Resume here.

> **Warning:** Setting Resume means that the data will be appended to `url` if `url` exists.

Returns the job handling the operation.

### QByteArray KIO::rawErrorDetail(int *errorCode*, const QString &*errorText*, const QUrl \**reqUrl* = nullptr, int *method* = -1) {#rawErrorDetail}

Returns translated error details for `errorCode` using the additional error information provided by `errorText` , `reqUrl` (the request URL), and the KIO worker `method` .

`errorCode` the error code

`errorText` the additional error text

`reqUrl` the request URL

`method` the KIO worker method

Returns the following data:

- [QString](https://doc.qt.io/qt-6/qstring.html) errorName - the name of the error
- [QString](https://doc.qt.io/qt-6/qstring.html) techName - if not null, the more technical name of the error
- [QString](https://doc.qt.io/qt-6/qstring.html) description - a description of the error
- [QStringList](https://doc.qt.io/qt-6/qstringlist.html) causes - a list of possible causes of the error
- [QStringList](https://doc.qt.io/qt-6/qstringlist.html) solutions - a liso of solutions for the error

### KIO::SimpleJob \*rename(const QUrl &*src*, const QUrl &*dest*, KIO::JobFlags *flags* = DefaultFlags) {#rename}

Rename a file or directory. Warning: this operation fails if a direct renaming is not possible (like with files or dirs on separate partitions) Use move or [file\_move](kio-filecopyjob.md#file_move) in this case.

`src` The original URL

`dest` The final URL

`flags` Can be Overwrite here

Returns the job handling the operation.

### KIO::RestoreJob \*restoreFromTrash(const QList\<QUrl\> &*urls*, KIO::JobFlags *flags* = DefaultFlags) {#restoreFromTrash}

Restore a set of trashed files or directories.

`urls` the trash:/ URLs to restore. The trash implementation will know where the files came from and will restore them to their original location.

`flags` restoreFromTrash() supports [HideProgressInfo](kio.md#JobFlag-enum).

Returns the job handling the operation

### KIO::SimpleJob \*rmdir(const QUrl &*url*) {#rmdir}

Removes a single directory.

The directory is assumed to be empty. The job will fail if the directory is not empty. Use [KIO::del](kio-deletejob.md#del)() ([DeleteJob](kio-deletejob.md)) to delete non-empty directories.

`url` The URL of the directory to remove.

Returns a pointer to the job handling the operation.

### void setDefaultJobUiDelegateExtension(KIO::JobUiDelegateExtension \**extension*) {#setDefaultJobUiDelegateExtension}

Internal. Allows the KIO widgets library to register its widget-based job UI delegate extension automatically.

*See also* [defaultJobUiDelegateExtension](kio-jobuidelegateextension.md#defaultJobUiDelegateExtension)()

### \[since 6.0\] void setDefaultJobUiDelegateFactory(KIO::JobUiDelegateFactory \**factory*) {#setDefaultJobUiDelegateFactory}

Internal. Allows the KIO widgets library to register its widget-based job UI delegate factory automatically.

This function was introduced in Qt 6.0.

*See also* [defaultJobUiDelegateFactory](kio-jobuidelegatefactory.md#defaultJobUiDelegateFactory)()

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

### KIO::StatJob \*stat(const QUrl &*url*, KIO::JobFlags *flags* = DefaultFlags) {#stat}

Find all details for one file or directory.

`url` the URL of the file

`flags` Can be [HideProgressInfo](kio.md#JobFlag-enum) here

Returns the job handling the operation.

### \[since 6.0\] KIO::StatJob \*stat(const QUrl &*url*, KIO::StatJob::StatSide *side*, KIO::StatDetails *details* = KIO::StatDefaultDetails, KIO::JobFlags *flags* = DefaultFlags) {#stat-1}

Find all details for one file or directory.

This version includes two additional parameters, `side` and `details`.

`url` the URL of the file

`side` is [SourceSide](kio-statjob.md#StatSide-enum) when stating a source file (we will do a get on it if the stat works) and [DestinationSide](kio-statjob.md#StatSide-enum) when stating a destination file (target of a copy). The reason for this parameter is that in some cases the KIO worker might not be able to determine a file's existence (e.g. HTTP doesn't allow it, FTP has issues with case-sensitivity on some systems). When the worker can't reliably determine the existence of a file, it will:

- be optimistic if [SourceSide](kio-statjob.md#StatSide-enum), i.e. it will assume the file exists, and if it doesn't this will appear when actually trying to download it
- be pessimistic if [DestinationSide](kio-statjob.md#StatSide-enum), i.e. it will assume the file doesn't exist, to prevent showing "about to overwrite" errors to the user. If you simply want to check for existence without downloading/uploading afterwards, then you should use [DestinationSide](kio-statjob.md#StatSide-enum).

`details` selects the level of details we want. You should minimize the detail level for better performance.

`flags` Can be [HideProgressInfo](kio.md#JobFlag-enum) here

Returns the job handling the operation.

This function was introduced in Qt 6.0.

### KIO::StoredTransferJob \*storedGet(const QUrl &*url*, KIO::LoadType *reload* = NoReload, KIO::JobFlags *flags* = DefaultFlags) {#storedGet}

Get (means: read), into a single [QByteArray](https://doc.qt.io/qt-6/qbytearray.html).

`url` the URL of the file

`reload` Reload to reload the file, [NoReload](kio.md#LoadType-enum) if it can be taken from the cache

`flags` Can be [HideProgressInfo](kio.md#JobFlag-enum) here

Returns the job handling the operation.

### KIO::StoredTransferJob \*storedHttpPost(const QByteArray &*arr*, const QUrl &*url*, KIO::JobFlags *flags* = DefaultFlags) {#storedHttpPost}

HTTP POST (means: write) data from a single [QByteArray](https://doc.qt.io/qt-6/qbytearray.html).

`arr` The data to write

`url` Where to write data.

`flags` Can be [HideProgressInfo](kio.md#JobFlag-enum) here.

Returns the job handling the operation.

### KIO::StoredTransferJob \*storedHttpPost(QIODevice \**device*, const QUrl &*url*, qint64 *size* = -1, KIO::JobFlags *flags* = DefaultFlags) {#storedHttpPost-1}

HTTP POST (means: write) data from the given IO device.

`device` Device from which the encoded data to be posted is read. Must be open for reading.

`url` Where to write data.

`size` Size of the encoded data to be posted.

`flags` Can be [HideProgressInfo](kio.md#JobFlag-enum) here.

Returns the job handling the operation.

### KIO::StoredTransferJob \*storedPut(QIODevice \**input*, const QUrl &*url*, int *permissions*, KIO::JobFlags *flags* = DefaultFlags) {#storedPut}

Put (means: write) data from a [QIODevice](https://doc.qt.io/qt-6/qiodevice.html).

`input` The data to write, a device to read from. Must be open for reading (data will be read from the current position).

`url` Where to write data.

`permissions` May be -1. In this case no special permission mode is set.

`flags` Can be [HideProgressInfo](kio.md#JobFlag-enum), Overwrite and Resume here. WARNING: Setting Resume means that the data will be appended to `dest` if `dest` exists.

Returns the job handling the operation.

### KIO::StoredTransferJob \*storedPut(const QByteArray &*arr*, const QUrl &*url*, int *permissions*, KIO::JobFlags *flags* = DefaultFlags) {#storedPut-1}

Put (means: write) data from a single [QByteArray](https://doc.qt.io/qt-6/qbytearray.html).

`arr` The data to write

`url` Where to write data.

`permissions` May be -1. In this case no special permission mode is set.

`flags` Can be [HideProgressInfo](kio.md#JobFlag-enum), Overwrite and Resume here. WARNING: Setting Resume means that the data will be appended to `url` if `url` exists.

Returns the job handling the operation.

### KIO::SimpleJob \*symlink(const QString &*target*, const QUrl &*dest*, KIO::JobFlags *flags* = DefaultFlags) {#symlink}

Create or move a symlink. This is the lowlevel operation, similar to [file\_copy](kio-filecopyjob.md#file_copy) and [file\_move](kio-filecopyjob.md#file_move). It doesn't do any check (other than those the worker does) and it doesn't show rename and skip dialogs - use [KIO::link](kio-copyjob.md#link) for that.

`target` The string that will become the "target" of the link (can be relative)

`dest` The symlink to create.

`flags` Can be Overwrite and [HideProgressInfo](kio.md#JobFlag-enum)

Returns the job handling the operation.

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

### KIO::SimpleJob \*unmount(const QString &*point*, KIO::JobFlags *flags* = DefaultFlags) {#unmount}

Unmount filesystem.

Special job for kio\_file.

`point` Point to unmount.

`flags` Can be [HideProgressInfo](kio.md#JobFlag-enum) here

Returns the job handling the operation.

### QString KIO::unsupportedActionErrorString(const QString &*protocol*, int *cmd*) {#unsupportedActionErrorString}

Returns an appropriate error message if the given command `cmd` is an unsupported action (ERR\_UNSUPPORTED\_ACTION).

`protocol` name of the protocol

`cmd` given command

### QUrl KIO::upUrl(const QUrl &*url*) {#upUrl}

This function is useful to implement the "Up" button in a file manager for example.

Returns a URL that is a level higher

### bool KIO::operator!=(const KIO::UDSEntry &*entry*, const KIO::UDSEntry &*other*) {#operator-not-eq}

Returns true if the entry does not contain the same data as the other

### QDBusArgument &KIO::operator\<\<(QDBusArgument &*argument*, const KIO::AuthInfo &*a*) {#operator-lt-lt}

### QDataStream &KIO::operator\<\<(QDataStream &*s*, const KIO::AuthInfo &*a*) {#operator-lt-lt-1}

### bool KIO::operator==(const KIO::UDSEntry &*entry*, const KIO::UDSEntry &*other*) {#operator-eq-eq}

Returns true if the entry contains the same data as the other

### QDataStream &KIO::operator\>\>(QDataStream &*s*, KIO::AuthInfo &*a*) {#operator-gt-gt}

### const QDBusArgument &KIO::operator\>\>(const QDBusArgument &*argument*, KIO::AuthInfo &*a*) {#operator-gt-gt-1}
