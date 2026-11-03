---
title: "KIO::ForwardingWorkerBase Class"
description: "Worker that forwards to other workers."
---

# KIO::ForwardingWorkerBase Class

Worker that forwards to other workers. [More...](#details)

- **Header:** `#include <KIO/ForwardingWorkerBase>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS KIO)`  
  `target_link_libraries(mytarget PRIVATE KF6::KIOCore)`
- **Inherits:** [QObject](https://doc.qt.io/qt-6/qobject.html) and [KIO::WorkerBase](kio-workerbase.md)

[List of all members, including inherited members](kio-forwardingworkerbase-members.md)

## Public Types

- [enum ForwardingWorkerBase::UDSEntryCreationMode](#UDSEntryCreationMode-enum)

## Protected Functions

- [void adjustUDSEntry(KIO::UDSEntry &entry, KIO::ForwardingWorkerBase::UDSEntryCreationMode creationMode) const](#adjustUDSEntry)
- [QUrl processedUrl() const](#processedUrl)
- [QUrl requestedUrl() const](#requestedUrl)
- [bool rewriteUrl(const QUrl &url, QUrl &newURL)](#rewriteUrl)

## Detailed Description {#details}

This class should be used as a base for KIO workers acting as a forwarder to other KIO workers. It has been designed to support only local filesystem like KIO workers.

If the resulting KIO worker should be a simple proxy, you only need to implement the [ForwardingWorkerBase::rewriteUrl](kio-forwardingworkerbase.md#rewriteUrl)() method.

For more advanced behavior, the classic KIO worker methods should be reimplemented, because their default behavior in this class is to forward using the [ForwardingWorkerBase::rewriteUrl](kio-forwardingworkerbase.md#rewriteUrl)() method.

A possible code snippet for an advanced [stat](kio-workerbase.md#stat)() behavior would look like this in the child class:

```cpp
WorkerResult ChildProtocol::stat(const QUrl &url)
{
    bool is_special = false;

    // Process the URL to see if it should have
    // a special treatment

    if (is_special) {
        // Handle the URL ourselves
        KIO::UDSEntry entry;
        // Fill entry with values
        statEntry(entry);
        return WorkerResult::pass();
    }
    // Setup the KIO worker internal state if
    // required by ChildProtocol::rewriteUrl()
    return ForwardingWorkerBase::stat(url);
}
```

Of course in this case, you surely need to reimplement [listDir](kio-workerbase.md#listDir)() and [get](kio-workerbase.md#get)() accordingly.

If you want view on directories to be correctly refreshed when something changes on a forwarded URL, you'll need a companion kded module to emit the KDirNotify Files\*() D-Bus signals.

*See also* [ForwardingWorkerBase::rewriteUrl](kio-forwardingworkerbase.md#rewriteUrl)()

## Member Type Documentation {#member-type-documentation}

### enum ForwardingWorkerBase::UDSEntryCreationMode {#UDSEntryCreationMode-enum}

| Constant | Value | Description |
| --- | --- | --- |
| `KIO::ForwardingWorkerBase::UDSEntryCreationInStat` | `0` | The entry is created during a stat operation. |
| `KIO::ForwardingWorkerBase::UDSEntryCreationInListDir` | `1` | The entry is created during a [listDir](kio-listjob.md#listDir) operation. |

## Member Function Documentation {#member-function-documentation}

### \[virtual protected\] void ForwardingWorkerBase::adjustUDSEntry(KIO::UDSEntry &*entry*, KIO::ForwardingWorkerBase::UDSEntryCreationMode *creationMode*) const {#adjustUDSEntry}

Adjusts a [UDSEntry](kio-udsentry.md) before it's sent in the reply to the KIO worker endpoint. This is the default implementation working in most cases, but sometimes you could make use of more forwarding black magic (for example dynamically transform any desktop file into a fake directory...)

`entry` the [UDSEntry](kio-udsentry.md) to adjust

`creationMode` the operation for which this entry is created

### \[protected\] QUrl ForwardingWorkerBase::processedUrl() const {#processedUrl}

Return the URL being processed by the KIO worker Only access it inside [adjustUDSEntry](kio-forwardingworkerbase.md#adjustUDSEntry)()

### \[protected\] QUrl ForwardingWorkerBase::requestedUrl() const {#requestedUrl}

Return the URL asked to the KIO worker Only access it inside [adjustUDSEntry](kio-forwardingworkerbase.md#adjustUDSEntry)()

### \[pure virtual protected\] bool ForwardingWorkerBase::rewriteUrl(const QUrl &*url*, QUrl &*newURL*) {#rewriteUrl}

Rewrite an url to its forwarded counterpart. It should return true if everything was ok, and false otherwise.

If a problem is detected it's up to this method to trigger error() before returning. Returning false silently cancels the current KIO worker operation.

`url` The URL as given during the KIO worker call

`newURL` The new URL to forward the KIO worker call to

Returns true if the given url could be correctly rewritten
