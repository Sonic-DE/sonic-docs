---
title: "KIO::MimeTypeFinderJob Class"
description: "MimeTypeFinderJob finds out the MIME type of a URL."
---

# KIO::MimeTypeFinderJob Class

[MimeTypeFinderJob](kio-mimetypefinderjob.md) finds out the MIME type of a URL. [More...](#details)

- **Header:** `#include <KIO/MimeTypeFinderJob>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS KIO)`  
  `target_link_libraries(mytarget PRIVATE KF6::KIOCore)`
- **Inherits:** [KCompositeJob](../kcoreaddons/kcompositejob.md)

[List of all members, including inherited members](kio-mimetypefinderjob-members.md)

## Public Functions

- [MimeTypeFinderJob(const QUrl &url, QObject \*parent = nullptr)](#MimeTypeFinderJob)
- [~MimeTypeFinderJob()](#dtor.MimeTypeFinderJob)
- [bool isAuthenticationPromptEnabled() const](#isAuthenticationPromptEnabled)
- [QString mimeType() const](#mimeType)
- [void setAuthenticationPromptEnabled(bool enable)](#setAuthenticationPromptEnabled)
- [void setFollowRedirections(bool b)](#setFollowRedirections)
- [void setSuggestedFileName(const QString &suggestedFileName)](#setSuggestedFileName)
- [void start()](#start)
- [QString suggestedFileName() const](#suggestedFileName)

## Detailed Description {#details}

## Member Function Documentation {#member-function-documentation}

### \[explicit\] MimeTypeFinderJob::MimeTypeFinderJob(const QUrl &*url*, QObject \**parent* = nullptr) {#MimeTypeFinderJob}

Creates an [MimeTypeFinderJob](kio-mimetypefinderjob.md) for a URL.

`url` the URL of the file/directory to examine

### \[override virtual noexcept\] MimeTypeFinderJob::~MimeTypeFinderJob() {#dtor.MimeTypeFinderJob}

Destructor

Note that by default jobs auto-delete themselves after emitting result.

### bool MimeTypeFinderJob::isAuthenticationPromptEnabled() const {#isAuthenticationPromptEnabled}

Returns where authentication prompts are enabled or disabled.

*See also* [setAuthenticationPromptEnabled](kio-mimetypefinderjob.md#setAuthenticationPromptEnabled)()

### QString MimeTypeFinderJob::mimeType() const {#mimeType}

Returns the MIME type.

Only valid after the [result](../kcoreaddons/kjob.md#result)() signal has been emitted.

### void MimeTypeFinderJob::setAuthenticationPromptEnabled(bool *enable*) {#setAuthenticationPromptEnabled}

Enable/disable authentication prompt, if the URL requires one. They are enabled by default. This method allows to disable such prompts for jobs that should fail rather than bother the user, if authentication is needed. Example: for starting the associated program (i.e. when OpenUrlJob uses [MimeTypeFinderJob](kio-mimetypefinderjob.md)), we want auth prompts. But for using a nice icon in a notification, we don't.

*See also* [isAuthenticationPromptEnabled](kio-mimetypefinderjob.md#isAuthenticationPromptEnabled)()

### void MimeTypeFinderJob::setFollowRedirections(bool *b*) {#setFollowRedirections}

Sets whether the job should follow URL redirections. This is enabled by default.

`b` whether to follow redirections or not

### void MimeTypeFinderJob::setSuggestedFileName(const QString &*suggestedFileName*) {#setSuggestedFileName}

Sets the file name to use in the case of downloading the file to a tempfile, in order to give it to a non-URL-aware application. Some apps rely on the extension to determine the MIME type of the file. Usually the file name comes from the URL, but in the case of the HTTP Content-Disposition header, we need to override the file name.

`suggestedFileName` the file name

*See also* [suggestedFileName](kio-mimetypefinderjob.md#suggestedFileName)()

### \[override virtual\] void MimeTypeFinderJob::start() {#start}

Reimplements: [KJob::start()](../kcoreaddons/kjob.md#start).

Starts the job. You must call this, after having called all the needed setters.

### QString MimeTypeFinderJob::suggestedFileName() const {#suggestedFileName}

Returns the suggested filename, either set by [setSuggestedFileName](kio-mimetypefinderjob.md#setSuggestedFileName) or returned by the [KIO::get](kio-transferjob.md#get) job

*See also* [setSuggestedFileName](kio-mimetypefinderjob.md#setSuggestedFileName)()
