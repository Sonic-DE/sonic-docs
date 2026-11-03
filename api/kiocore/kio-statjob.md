---
title: "KIO::StatJob Class"
description: "A KIO job that retrieves information about a file or directory."
---

# KIO::StatJob Class

A KIO job that retrieves information about a file or directory. [More...](#details)

- **Header:** `#include <KIO/StatJob>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS KIO)`  
  `target_link_libraries(mytarget PRIVATE KF6::KIOCore)`
- **Inherits:** [KIO::SimpleJob](kio-simplejob.md)

[List of all members, including inherited members](kio-statjob-members.md)

## Public Types

- [enum StatJob::StatSide](#StatSide-enum)

## Public Functions

- [QUrl mostLocalUrl() const](#mostLocalUrl)
- [void setDetails(KIO::StatDetails details)](#setDetails)
- [void setSide(KIO::StatJob::StatSide side)](#setSide)
- [const KIO::UDSEntry &statResult() const](#statResult)

## Signals

- [void permanentRedirection(KIO::Job \*job, const QUrl &fromUrl, const QUrl &toUrl)](#permanentRedirection)
- [void redirection(KIO::Job \*job, const QUrl &url)](#redirection)

## Detailed Description {#details}

*See also* [KIO::stat()](kio-index.md)

## Member Type Documentation {#member-type-documentation}

### enum StatJob::StatSide {#StatSide-enum}

| Constant |   |
| --- | --- |
| `KIO::StatJob::SourceSide` | `0` |
| `KIO::StatJob::DestinationSide` | `1` |

## Member Function Documentation {#member-function-documentation}

### QUrl StatJob::mostLocalUrl() const {#mostLocalUrl}

most local URL

Since this method depends on [UDSEntry::UDS\_LOCAL\_PATH](kio-udsentry.md#StandardFieldTypes-enum) having been previously set by a KIO worker, ideally you should first check that the protocol Class of the URL being stat'ed is ":local" before creating the [StatJob](kio-statjob.md) at all. Typically only ":local" KIO workers set UDS\_LOCAL\_PATH. See [KProtocolInfo::protocolClass](kprotocolinfo.md#protocolClass)().

Call this in a slot connected to the result signal, and only after making sure no error happened.

Returns the most local URL for the URL we were stat'ing

Sample usage:

```cpp
auto *job = KIO::mostLocalUrl("desktop:/foo");
job->uiDelegate()->setWindow(this);
connect(job, &KJob::result, this, &MyClass::slotMostLocalUrlResult);
[...]
// and in slotMostLocalUrlResult(KJob *job)
if (job->error()) {
   [...] // doesn't exist
} else {
   const QUrl localUrl = job->mostLocalUrl();
   // localUrl = file:///$HOME/Desktop/foo
   [...]
}
```

### \[signal\] void StatJob::permanentRedirection(KIO::Job \**job*, const QUrl &*fromUrl*, const QUrl &*toUrl*) {#permanentRedirection}

Signals a permanent redirection.

The redirection itself is handled internally.

`job` the job that is redirected

`fromUrl` the original URL

`toUrl` the new URL

### \[signal\] void StatJob::redirection(KIO::Job \**job*, const QUrl &*url*) {#redirection}

Signals a redirection.

Use to update the URL shown to the user. The redirection itself is handled internally.

`job` the job that is redirected

`url` the new url

### void StatJob::setDetails(KIO::StatDetails *details*) {#setDetails}

Selects the level of `details` we want.

### void StatJob::setSide(KIO::StatJob::StatSide *side*) {#setSide}

A [stat](kio-statjob.md#stat)() can have two meanings. Either we want to read from this URL, or to check if we can write to it. First case is "source", second is "dest". It is necessary to know what the [StatJob](kio-statjob.md) is for, to tune the KIO worker's behavior (e.g. with FTP).

By default it is [SourceSide](kio-statjob.md#StatSide-enum).

`side` [SourceSide](kio-statjob.md#StatSide-enum) or [DestinationSide](kio-statjob.md#StatSide-enum)

### const KIO::UDSEntry &StatJob::statResult() const {#statResult}

Result of the stat operation.

Call this in the slot connected to result, and only after making sure no error happened.

Returns the result of the stat

## Related Non-Members {#related-non-members}

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
