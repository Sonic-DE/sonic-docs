---
title: "KIO::NameFinderJob Class"
description: "NameFinderJob finds a valid \"New Folder\" name."
---

# KIO::NameFinderJob Class

[NameFinderJob](kio-namefinderjob.md) finds a valid "New Folder" name. [More...](#details)

- **Header:** `#include <KIO/NameFinderJob>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS KIO)`  
  `target_link_libraries(mytarget PRIVATE KF6::KIOCore)`
- **Inherits:** [KCompositeJob](../kcoreaddons/kcompositejob.md)

[List of all members, including inherited members](kio-namefinderjob-members.md)

## Public Functions

- [NameFinderJob(const QUrl &baseUrl, const QString &name, QObject \*parent)](#NameFinderJob)
- [~NameFinderJob()](#dtor.NameFinderJob)
- [QUrl baseUrl() const](#baseUrl)
- [QString finalName() const](#finalName)
- [QUrl finalUrl() const](#finalUrl)
- [void start()](#start)

## Detailed Description {#details}

This job is useful when suggesting a new folder/file name, e.g. in [KNewFileMenu](../kiofilewidgets/knewfilemenu.md), the text box is pre-filled with a suggested name, typically in the form "New Folder"; to offer a valid name (i.e. one that doesn't already exist), you can use a [NameFinderJob](kio-namefinderjob.md).

Internally it uses a [KIO::StatJob](kio-statjob.md) to determine if e.g. "New Folder" already exists, and in such a case it will use [KFileUtils::makeSuggestedName](../kcoreaddons/kfileutils.md#makeSuggestedName)() to make a new name, e.g. "New Folder (1)", then if the latter exists, [KFileUtils::makeSuggestedName](../kcoreaddons/kfileutils.md#makeSuggestedName)() will be called again... etc, until it finds a name that doesn't already exist.

Since [NameFinderJob](kio-namefinderjob.md) uses a [KIO::StatJob](kio-statjob.md), the code is asynchronous, which means it should work for both local and remote filesystems without blocking I/O calls (this is important when interacting with network mounts (e.g. SMB, NFS), from the upstream [QFile](https://doc.qt.io/qt-6/qfile.html) perspective these network mounts are "local" files even though they could actually reside on a server halfway across the world).

Note that [KIO::StatJob](kio-statjob.md) will resolve URLs such as "desktop:/" to the most local URL, hence it's advisable to always use [baseUrl](kio-namefinderjob.md#baseUrl)() (or [finalUrl](kio-namefinderjob.md#finalUrl)()) to get the actual URL.

If the job fails for any reason targerUrl() will return an empty URL.

> **Note:** You must call [start](kio-namefinderjob.md#start)() to start the job.

```cpp
// Create the job
auto nameJob = new KIO::NameFinderJob(baseUrl, name, this);
// Connect to the result() slot, and after making sure there were no errors call
// finalUrl(), baseUrl() or finalName() to get the new url (base
// url + suggested name), base url or suggested name, respectively
connect(nameJob, &KJob::result, this, []() {
    if (!nameJob->error()) {
        const QUrl newBaseUrl = nameJob->baseUrl();
        const QUrl newName = nameJob->finalName();
        .....
        // Create the new dir "newName" in "newBaseUrl"
    }
});

// Start the job
nameJob->start();
```

## Member Function Documentation {#member-function-documentation}

### \[explicit\] NameFinderJob::NameFinderJob(const QUrl &*baseUrl*, const QString &*name*, QObject \**parent*) {#NameFinderJob}

Creates a [NameFinderJob](kio-namefinderjob.md) to get a "New Folder" (or "Text File.txt") name that doesn't already exist.

`baseUrl` URL of the directory where a new folder/file is going to be created

`name` the initially proposed name of the new folder/file

### \[override virtual noexcept\] NameFinderJob::~NameFinderJob() {#dtor.NameFinderJob}

Destructor

Note that by default jobs auto-delete themselves after emitting result.

### QUrl NameFinderJob::baseUrl() const {#baseUrl}

Call this to get the base URL (i.e. the URL of the folder where a new folder/file is going to be created). Note that this could return a different URL from the one the job was initially called on, since the [StatJob](kio-statjob.md) (which is used internally) will resolve the URL to the most local one. See [KIO::StatJob::mostLocalUrl](kio-statjob.md#mostLocalUrl)() for more details.

Typically you should call this in a slot connected to the [result](../kcoreaddons/kjob.md#result)() signal, and after making sure no errors occurred.

### QString NameFinderJob::finalName() const {#finalName}

Call this to get the suggested new folder/file name. Typically you should call this in a slot connected to the [result](../kcoreaddons/kjob.md#result)() signal and after making sure no errors occurred.

### QUrl NameFinderJob::finalUrl() const {#finalUrl}

Call this to get the full target URL (basically the [baseUrl](kio-namefinderjob.md#baseUrl)() + "/" + [finalName](kio-namefinderjob.md#finalName)()). Typically you should call this in a slot connected to the [result](../kcoreaddons/kjob.md#result)() signal, and after making sure no errors occurred (if there were an error this method will return an empty URL).

### \[override virtual\] void NameFinderJob::start() {#start}

Reimplements: [KJob::start()](../kcoreaddons/kjob.md#start).

Starts the job.
