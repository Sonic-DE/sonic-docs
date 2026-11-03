---
title: "KIO::ListJob Class"
description: "A ListJob is allows you to get the get the content of a directory."
---

# KIO::ListJob Class

A [ListJob](kio-listjob.md) is allows you to get the get the content of a directory. [More...](#details)

- **Header:** `#include <KIO/ListJob>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS KIO)`  
  `target_link_libraries(mytarget PRIVATE KF6::KIOCore)`
- **Inherits:** [KIO::SimpleJob](kio-simplejob.md)

[List of all members, including inherited members](kio-listjob-members.md)

## Public Types

- [enum ListJob::ListFlag](#ListFlag-enum)

## Public Functions

- [const QUrl &redirectionUrl() const](#redirectionUrl)
- [void setDetails(KIO::StatDetails details)](#setDetails) (since 6.25)
- [void setUnrestricted(bool unrestricted)](#setUnrestricted)

## Signals

- [void entries(KIO::Job \*job, const KIO::UDSEntryList &list)](#entries)
- [void permanentRedirection(KIO::Job \*job, const QUrl &fromUrl, const QUrl &toUrl)](#permanentRedirection)
- [void redirection(KIO::Job \*job, const QUrl &url)](#redirection)
- [void subError(KIO::ListJob \*job, KIO::ListJob \*subJob)](#subError)

## Detailed Description {#details}

Don't create the job directly, but use [KIO::listRecursive](kio-listjob.md#listRecursive)() or [KIO::listDir](kio-listjob.md#listDir)() instead.

*See also* [KIO::listRecursive()](kio-index.md), [KIO::listDir()](kio-index.md)

## Member Type Documentation {#member-type-documentation}

### enum ListJob::ListFlag {#ListFlag-enum}

**flags ListJob::ListFlags**

| Constant | Value | Description |
| --- | --- | --- |
| `KIO::ListJob::ListFlag::ExcludeHidden (since Qt 6.23)` | `0` | Don't include items whose name starts with '.' |
| `KIO::ListJob::ListFlag::IncludeHidden` | `1 << 0` | Include hidden files in the listing. |
| `KIO::ListJob::ListFlag::ExcludeDot (since Qt 6.23)` | `2 << 0` | Skip the '.' entry for the root dir, there are always skipped for sub-directories |
| `KIO::ListJob::ListFlag::ExcludeDotDot (since Qt 6.23)` | `1 << 2` | Skip the '..' entry for the root dir, there are always skipped for sub-directories |
| `KIO::ListJob::ListFlag::ExcludeDotAndDotDot (since Qt 6.23)` | `ExcludeDot | ExcludeDotDot` | = ExcludeDot \| ExcludeDotDot |

The `ListFlags` type is a typedef for `QFlags<ListFlag>. `It stores an OR combination of `ListFlag` values.

## Member Function Documentation {#member-function-documentation}

### \[signal\] void ListJob::entries(KIO::Job \**job*, const KIO::UDSEntryList &*list*) {#entries}

This signal emits the entry found by the job while listing. The progress signals aren't specific to [ListJob](kio-listjob.md). It simply uses [SimpleJob](kio-simplejob.md)'s processedSize (number of entries listed) and totalSize (total number of entries, if known), as well as percent.

`job` the job that emitted this signal

`list` the list of UDSEntries

### \[signal\] void ListJob::permanentRedirection(KIO::Job \**job*, const QUrl &*fromUrl*, const QUrl &*toUrl*) {#permanentRedirection}

Signals a permanent redirection. The redirection itself is handled internally.

`job` the job that emitted this signal

`fromUrl` the original URL

`toUrl` the new URL

### \[signal\] void ListJob::redirection(KIO::Job \**job*, const QUrl &*url*) {#redirection}

Signals a redirection. Use to update the URL shown to the user. The redirection itself is handled internally.

`job` the job that is redirected

`url` the new url

### const QUrl &ListJob::redirectionUrl() const {#redirectionUrl}

Returns the [ListJob](kio-listjob.md)'s redirection URL. This will be invalid if there was no redirection.

### \[since 6.25\] void ListJob::setDetails(KIO::StatDetails *details*) {#setDetails}

Selects the level of `details` we want.

This function was introduced in Qt 6.25.

### void ListJob::setUnrestricted(bool *unrestricted*) {#setUnrestricted}

Do not apply any KIOSK restrictions to this job.

### \[signal\] void ListJob::subError(KIO::ListJob \**job*, KIO::ListJob \**subJob*) {#subError}

This signal is emitted when a sub-directory could not be listed. The job keeps going, thus doesn't result in an overall error.

`job` the job that emitted the signal

`subJob` the job listing a sub-directory, which failed. Use [url](kio-simplejob.md#url)(), [error](../kcoreaddons/kjob.md#error)() and [errorText](../kcoreaddons/kjob.md#errorText)() on that job to find out more.

## Related Non-Members {#related-non-members}

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
