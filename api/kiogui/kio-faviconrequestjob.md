---
title: "KIO::FavIconRequestJob Class"
description: "FavIconRequestJob handles the retrieval of a favicon (either from the local cache or from the internet)."
---

# KIO::FavIconRequestJob Class

[FavIconRequestJob](kio-faviconrequestjob.md) handles the retrieval of a favicon (either from the local cache or from the internet). [More...](#details)

- **Header:** `#include <KIO/FavIconRequestJob>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS KIO)`  
  `target_link_libraries(mytarget PRIVATE KIOGui)`
- **Inherits:** [KCompositeJob](../kcoreaddons/kcompositejob.md)

[List of all members, including inherited members](kio-faviconrequestjob-members.md)

## Public Functions

- [FavIconRequestJob(const QUrl &hostUrl, KIO::LoadType reload = KIO::NoReload, QObject \*parent = nullptr)](#FavIconRequestJob)
- [~FavIconRequestJob()](#dtor.FavIconRequestJob)
- [QUrl hostUrl() const](#hostUrl)
- [QString iconFile() const](#iconFile)
- [void setIconUrl(const QUrl &iconUrl)](#setIconUrl)

## Detailed Description {#details}

For instance, the icon for http://www.google.com exists at http://www.google.com/favicon.ico This job will (the first time) download the favicon, and make it available as a local PNG for fast lookups afterwards.

Usage: Create a [FavIconRequestJob](kio-faviconrequestjob.md), connect to result([KJob](../kcoreaddons/kjob.md) \*), and from there use [iconFile](kio-faviconrequestjob.md#iconFile)().

```cpp
// Let's say we want to show the icon for QUrl m_url
KIO::FavIconRequestJob *job = new KIO::FavIconRequestJob(m_url);
connect(job, &KIO::FavIconRequestJob::result, this, [job, this](KJob *){
    if (!job->error()) {
        // show the icon using QIcon(job->iconFile())
    }
});
```

For a given HTTP URL, you can find out if a favicon is available by calling [KIO::favIconForUrl](../kiocore/kio.md#favIconForUrl)() in [KIOCore](../kiocore/kiocore-module.md). It is however not necessary to check this first, [FavIconRequestJob](kio-faviconrequestjob.md) will do this first and emit result right away if a cached icon is available and not too old.

In Web Browsers, additional information exists: the HTML for a given page can specify something like &lt;link rel="shortcut icon" href="another\_favicon.ico" /&gt; To handle this, call job-\>[setIconUrl](kio-faviconrequestjob.md#setIconUrl)(iconUrl). (KParts-based web engines use the signal BrowserExtension::setIconUrl to call back into the web browser application, which should then call this). The signal urlIconChanged will be emitted once the icon has been downloaded.

The on-disk cache is shared between processes.

## Member Function Documentation {#member-function-documentation}

### \[explicit\] FavIconRequestJob::FavIconRequestJob(const QUrl &*hostUrl*, KIO::LoadType *reload* = KIO::NoReload, QObject \**parent* = nullptr) {#FavIconRequestJob}

[FavIconRequestJob](kio-faviconrequestjob.md) constructor

`hostUrl` The web page URL. We only use the scheme and host.

`reload` set this to reload to skip the cache and force a refresh of the favicon.

`parent` parent object

### \[override virtual noexcept\] FavIconRequestJob::~FavIconRequestJob() {#dtor.FavIconRequestJob}

Destructor. You do not need to delete the job, it will delete automatically, unless you call setAutoDelete(false).

### QUrl FavIconRequestJob::hostUrl() const {#hostUrl}

Returns the URL passed to the constructor

### QString FavIconRequestJob::iconFile() const {#iconFile}

Returns the full local path to the icon from the cache. Only call this in the slot connected to the result([KJob](../kcoreaddons/kjob.md)\*) signal. Returns the path to the icon file

### void FavIconRequestJob::setIconUrl(const QUrl &*iconUrl*) {#setIconUrl}

setIconUrl allows to set, for a specific URL, a different icon URL than the default one for the host (http://host/favicon.ico)

This information is stored in the on-disk cache, so that other FavIconRequestJobs for this url and [KIO::favIconForUrl](../kiocore/kio.md#favIconForUrl) will return the icon specified here.

`iconUrl` the URL to the icon, usually parsed from the HTML
