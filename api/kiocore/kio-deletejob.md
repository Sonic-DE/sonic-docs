---
title: "KIO::DeleteJob Class"
description: "A more complex Job to delete files and directories."
---

# KIO::DeleteJob Class

A more complex Job to delete files and directories. [More...](#details)

- **Header:** `#include <KIO/DeleteJob>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS KIO)`  
  `target_link_libraries(mytarget PRIVATE KF6::KIOCore)`
- **Inherits:** [KIO::Job](kio-job.md)

[List of all members, including inherited members](kio-deletejob-members.md)

## Public Functions

- [QList\<QUrl\> urls() const](#urls)

## Signals

- [void deleting(KIO::Job \*job, const QUrl &file)](#deleting)
- [void processedDirs(KIO::Job \*job, unsigned long dirs)](#processedDirs)
- [void processedFiles(KIO::Job \*job, unsigned long files)](#processedFiles)
- [void totalDirs(KJob \*job, unsigned long dirs)](#totalDirs)
- [void totalFiles(KJob \*job, unsigned long files)](#totalFiles)

## Detailed Description {#details}

Don't create the job directly, but use [KIO::del](kio-deletejob.md#del)() instead.

*See also* [KIO::del()](kio-index.md)

## Member Function Documentation {#member-function-documentation}

### \[signal\] void DeleteJob::deleting(KIO::Job \**job*, const QUrl &*file*) {#deleting}

Sends the URL of the file that is currently being deleted.

`job` the job that emitted this signal

`file` the URL of the file or directory that is being deleted

### \[signal\] void DeleteJob::processedDirs(KIO::Job \**job*, unsigned long *dirs*) {#processedDirs}

Sends the number of processed directories.

`job` the job that emitted this signal

`dirs` the number of processed dirs

### \[signal\] void DeleteJob::processedFiles(KIO::Job \**job*, unsigned long *files*) {#processedFiles}

Sends the number of processed files.

`job` the job that emitted this signal

`files` the number of processed files

### \[signal\] void DeleteJob::totalDirs(KJob \**job*, unsigned long *dirs*) {#totalDirs}

Emitted when the total number of directories is known.

`job` the job that emitted this signal

`dirs` the total number of directories

### \[signal\] void DeleteJob::totalFiles(KJob \**job*, unsigned long *files*) {#totalFiles}

Emitted when the total number of files is known.

`job` the job that emitted this signal

`files` the total number of files

### QList\<QUrl\> DeleteJob::urls() const {#urls}

Returns the list of URLs.

## Related Non-Members {#related-non-members}

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
