---
title: "KIO::Job Class"
description: "Network transparent access to files and data."
---

# KIO::Job Class

Network transparent access to files and data. [More...](#details)

- **Header:** `#include <KIO/Job>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS KIO)`  
  `target_link_libraries(mytarget PRIVATE KF6::KIOCore)`
- **Inherits:** [KCompositeJob](../kcoreaddons/kcompositejob.md)
- **Inherited By:** [KIO::BatchRenameJob](kio-batchrenamejob.md), [KIO::ChmodJob](kio-chmodjob.md), [KIO::CopyJob](kio-copyjob.md), [KIO::DeleteJob](kio-deletejob.md), [KIO::DirectorySizeJob](kio-directorysizejob.md), [KIO::FileCopyJob](kio-filecopyjob.md), [KIO::MkpathJob](kio-mkpathjob.md), [KIO::RestoreJob](kio-restorejob.md), and [KIO::SimpleJob](kio-simplejob.md)

[List of all members, including inherited members](kio-job-members.md)

## Public Functions

- [void addMetaData(const QMap\<QString, QString\> &values)](#addMetaData)
- [void addMetaData(const QString &key, const QString &value)](#addMetaData-1)
- [QStringList detailedErrorStrings(const QUrl \*reqUrl = nullptr, int method = -1) const](#detailedErrorStrings)
- [QString errorString() const](#errorString)
- [void mergeMetaData(const QMap\<QString, QString\> &values)](#mergeMetaData)
- [KIO::MetaData metaData() const](#metaData)
- [KIO::Job \*parentJob() const](#parentJob)
- [QString queryMetaData(const QString &key)](#queryMetaData)
- [void setMetaData(const KIO::MetaData &metaData)](#setMetaData)
- [void setParentJob(KIO::Job \*parentJob)](#setParentJob)
- [void setUiDelegateExtension(KIO::JobUiDelegateExtension \*extension)](#setUiDelegateExtension)
- [KIO::JobUiDelegateExtension \*uiDelegateExtension() const](#uiDelegateExtension)

## Signals

- [void connected(KIO::Job \*job)](#connected)

## Protected Functions

- [bool addSubjob(KJob \*job)](#addSubjob)
- [bool doKill()](#doKill)
- [bool doResume()](#doResume)
- [bool doSuspend()](#doSuspend)
- [bool removeSubjob(KJob \*job)](#removeSubjob)

## Detailed Description {#details}

The base class for all jobs. For all jobs created in an application, the code looks like

```cpp
KIO::Job* job = KIO::someoperation(some parameters);
connect(job, &KJob::result, this, &MyClass::slotResult);
```

(other connects, specific to the job)

And slotResult is usually at least:

```cpp
void MyClass::slotResult(KJob *job)
{
  if (job->error()) {
    job->uiDelegate()->showErrorMessage();
  }
}
```

## Member Function Documentation {#member-function-documentation}

### void Job::addMetaData(const QMap\<QString, QString\> &*values*) {#addMetaData}

Add key/value pairs to the meta data that is sent to the worker. If a certain key already existed, it will be overridden.

`values` the meta data to add

*See also* [setMetaData](kio-job.md#setMetaData)(), [mergeMetaData](kio-job.md#mergeMetaData)()

### void Job::addMetaData(const QString &*key*, const QString &*value*) {#addMetaData-1}

Add key/value pair to the meta data that is sent to the worker.

`key` the key of the meta data

`value` the value of the meta data

*See also* [setMetaData](kio-job.md#setMetaData)(), [mergeMetaData](kio-job.md#mergeMetaData)()

### \[override virtual protected\] bool Job::addSubjob(KJob \**job*) {#addSubjob}

Reimplements: [KCompositeJob::addSubjob(KJob \*job)](../kcoreaddons/kcompositejob.md#addSubjob).

Add a job that has to be finished before a result is emitted. This has obviously to be called before the finish signal is emitted by the worker.

`job` the subjob to add

### \[signal\] void Job::connected(KIO::Job \**job*) {#connected}

Emitted when the worker successfully connected to the host. There is no guarantee the worker will send this, and this is currently unused (in the applications).

`job` the job that emitted this signal

### QStringList Job::detailedErrorStrings(const QUrl \**reqUrl* = nullptr, int *method* = -1) const {#detailedErrorStrings}

Converts an error code and a non-i18n error message into i18n strings suitable for presentation in a detailed error message box.

`reqUrl` the request URL that generated this error message

`method` the method that generated this error message (unimplemented)

Returns the following strings: title, error + description, causes+solutions

### \[override virtual protected\] bool Job::doKill() {#doKill}

Reimplements: [KJob::doKill()](../kcoreaddons/kjob.md#doKill).

Abort this job.

This kills all subjobs and deletes the job.

### \[override virtual protected\] bool Job::doResume() {#doResume}

Reimplements: [KJob::doResume()](../kcoreaddons/kjob.md#doResume).

Resume this job

*See also* [suspend](../kcoreaddons/kjob.md#suspend)()

### \[override virtual protected\] bool Job::doSuspend() {#doSuspend}

Reimplements: [KJob::doSuspend()](../kcoreaddons/kjob.md#doSuspend).

Suspend this job

*See also* [resume](../kcoreaddons/kjob.md#resume)()

### \[override virtual\] QString Job::errorString() const {#errorString}

Reimplements: [KJob::errorString() const](../kcoreaddons/kjob.md#errorString).

Converts an error code and a non-i18n error message into an error message in the current language. The low level (non-i18n) error message (usually a url) is put into the translated error message using %1.

Example for errid == ERR\_CANNOT\_OPEN\_FOR\_READING:

```cpp
i18n("Could not read\n%1", errortext);
```

Use this to display the error yourself, but for a dialog box use [uiDelegate](../kcoreaddons/kjob.md#uiDelegate)()-\>showErrorMessage(). Do not call it if [error](../kcoreaddons/kjob.md#error)() is not 0.

Returns the error message and if there is no error, a message telling the user that the app is broken, so check with [error](../kcoreaddons/kjob.md#error)() whether there is an error

### void Job::mergeMetaData(const QMap\<QString, QString\> &*values*) {#mergeMetaData}

Add key/value pairs to the meta data that is sent to the worker. If a certain key already existed, it will remain unchanged.

`values` the meta data to merge

*See also* [setMetaData](kio-job.md#setMetaData)(), [addMetaData](kio-job.md#addMetaData)()

### KIO::MetaData Job::metaData() const {#metaData}

Get meta data received from the worker. (Valid when first data is received and/or worker is finished)

Returns the job's meta data

*See also* [setMetaData](kio-job.md#setMetaData)()

### KIO::Job \*Job::parentJob() const {#parentJob}

Returns the parent job, or `nullptr` if there is none

*See also* [setParentJob](kio-job.md#setParentJob)

### QString Job::queryMetaData(const QString &*key*) {#queryMetaData}

Query meta data received from the worker. (Valid when first data is received and/or worker is finished)

`key` the key of the meta data to retrieve

Returns the value of the meta data, or QString() if the `key` does not exist

### \[override virtual protected\] bool Job::removeSubjob(KJob \**job*) {#removeSubjob}

Reimplements: [KCompositeJob::removeSubjob(KJob \*job)](../kcoreaddons/kcompositejob.md#removeSubjob).

Mark a sub job as being done.

Note that this does not terminate the parent job, even if `job` is the last subjob. emitResult must be called to indicate that the job is complete.

`job` the subjob to remove

### void Job::setMetaData(const KIO::MetaData &*metaData*) {#setMetaData}

Set meta data to be sent to the worker, replacing existing meta data.

`metaData` the meta data to set

*See also* [metaData](kio-job.md#metaData)(), [addMetaData](kio-job.md#addMetaData)(), [mergeMetaData](kio-job.md#mergeMetaData)()

### void Job::setParentJob(KIO::Job \**parentJob*) {#setParentJob}

Set the parent Job. One example use of this is when [FileCopyJob](kio-filecopyjob.md) calls RenameDialog::open, it must pass the correct progress ID of the parent [CopyJob](kio-copyjob.md) (to hide the progress dialog). You can set the parent job only once. By default a job does not have a parent job.

`parentJob` the new parent job

*See also* [parentJob](kio-job.md#parentJob)()

### void Job::setUiDelegateExtension(KIO::JobUiDelegateExtension \**extension*) {#setUiDelegateExtension}

Sets the UI delegate extension to be used by this job.

The default UI delegate extension is [KIO::defaultJobUiDelegateExtension](kio-jobuidelegateextension.md#defaultJobUiDelegateExtension)()

*See also* [uiDelegateExtension](kio-job.md#uiDelegateExtension)()

### KIO::JobUiDelegateExtension \*Job::uiDelegateExtension() const {#uiDelegateExtension}

Retrieves the UI delegate extension used by this job.

*See also* [setUiDelegateExtension](kio-job.md#setUiDelegateExtension)()
