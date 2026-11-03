---
title: "Obsolete Members for KIO::WorkerBase"
description: "Deprecated members of KIO::WorkerBase."
parent: "kiocore/kio-workerbase"
---

# Obsolete Members for KIO::WorkerBase

**The following members of class [WorkerBase](kio-workerbase.md) are deprecated.** We strongly advise against using them in new code.

## Public Functions

- [void addTemporaryAuthorization(const QString &action)](#addTemporaryAuthorization) (deprecated in 6.19)
- [int connectTimeout()](#connectTimeout) (deprecated in 6.11)
- [void connectWorker(const QString &path)](#connectWorker) (deprecated in 6.29)
- [void disconnectWorker()](#disconnectWorker) (deprecated in 6.29)
- [void errorPage()](#errorPage) (deprecated in 6.3)
- [int proxyConnectTimeout()](#proxyConnectTimeout) (deprecated in 6.11)
- [int readTimeout()](#readTimeout) (deprecated in 6.11)
- [KIO::PrivilegeOperationStatus requestPrivilegeOperation(const QString &operationDetails)](#requestPrivilegeOperation) (deprecated in 6.19)
- [int responseTimeout()](#responseTimeout) (deprecated in 6.11)
- [void setIncomingMetaData(const KIO::MetaData &metaData)](#setIncomingMetaData) (deprecated in 6.19)
- [void workerStatus(const QString &host, bool connected)](#workerStatus) (deprecated in 6.19)
- [void worker\_status()](#worker_status) (deprecated in 6.19)

## Obsolete Member Function Documentation {#obsolete-member-function-documentation}

### \[deprecated in 6.19\] void WorkerBase::addTemporaryAuthorization(const QString &*action*) {#addTemporaryAuthorization}

This function is deprecated since 6.19. We strongly advise against using it in new code.

Adds `action` to the list of PolicyKit actions which the worker is authorized to perform.

`action` the PolicyKit action

Not implemented

### \[deprecated in 6.11\] int WorkerBase::connectTimeout() {#connectTimeout}

This function is deprecated since 6.11. We strongly advise against using it in new code.

Returns timeout value for connecting to remote host.

This is not used.

### \[deprecated in 6.29\] void WorkerBase::connectWorker(const QString &*path*) {#connectWorker}

This function is deprecated since 6.29. We strongly advise against using it in new code.

Internal function to connect a worker to either the worker pool or the application.

### \[deprecated in 6.29\] void WorkerBase::disconnectWorker() {#disconnectWorker}

This function is deprecated since 6.29. We strongly advise against using it in new code.

Internal function to disconnect a worker from either the worker pool or the application.

### \[deprecated in 6.3\] void WorkerBase::errorPage() {#errorPage}

This function is deprecated since 6.3. We strongly advise against using it in new code.

Tell that we will only get an error page here. This means: the data you'll get isn't the data you requested, but an error page (usually HTML) that describes an error.

Not implemented.

### \[deprecated in 6.11\] int WorkerBase::proxyConnectTimeout() {#proxyConnectTimeout}

This function is deprecated since 6.11. We strongly advise against using it in new code.

Returns the timeout value for connecting to proxy in secs.

This is not used.

### \[deprecated in 6.11\] int WorkerBase::readTimeout() {#readTimeout}

This function is deprecated since 6.11. We strongly advise against using it in new code.

Returns the timeout value for read from subsequent data from remote host in secs.

This is not used.

### \[deprecated in 6.19\] KIO::PrivilegeOperationStatus WorkerBase::requestPrivilegeOperation(const QString &*operationDetails*) {#requestPrivilegeOperation}

This function is deprecated since 6.19. We strongly advise against using it in new code.

Checks with job if privilege operation is allowed. Returns privilege operation status.

Not implemented

*See also* [PrivilegeOperationStatus](kio-obsolete.md#PrivilegeOperationStatus-enum)

### \[deprecated in 6.11\] int WorkerBase::responseTimeout() {#responseTimeout}

This function is deprecated since 6.11. We strongly advise against using it in new code.

Returns the timeout value for read from first data from remote host in seconds.

This is not used.

### \[deprecated in 6.19\] void WorkerBase::setIncomingMetaData(const KIO::MetaData &*metaData*) {#setIncomingMetaData}

This function is deprecated since 6.19. We strongly advise against using it in new code.

Set the Incoming Meta Data This is only really useful if your worker wants to overwrite the metadata for consumption in other worker functions; this overwrites existing metadata set by the client!

`metaData` metadata to set

Not used

### \[deprecated in 6.19\] void WorkerBase::workerStatus(const QString &*host*, bool *connected*) {#workerStatus}

This function is deprecated since 6.19. We strongly advise against using it in new code.

Used to report the status of the worker.

`host` the worker is currently connected to. (Should be empty if not connected)

`connected` Whether an actual network connection exists.

Not implemented.

### \[virtual, deprecated in 6.19\] void WorkerBase::worker\_status() {#worker_status}

This function is deprecated since 6.19. We strongly advise against using it in new code.

Called to get the status of the worker. Worker should respond by calling [workerStatus](kio-workerbase-obsolete.md#workerStatus)(...)

Not implemented.
