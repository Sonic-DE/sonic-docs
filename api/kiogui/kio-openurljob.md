---
title: "KIO::OpenUrlJob Class"
description: "OpenUrlJob finds out the right way to \"open\" a URL."
---

# KIO::OpenUrlJob Class

[OpenUrlJob](kio-openurljob.md) finds out the right way to "open" a URL. [More...](#details)

- **Header:** `#include <KIO/OpenUrlJob>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS KIO)`  
  `target_link_libraries(mytarget PRIVATE KIOGui)`
- **Inherits:** [KCompositeJob](../kcoreaddons/kcompositejob.md)

[List of all members, including inherited members](kio-openurljob-members.md)

## Public Functions

- [OpenUrlJob(const QUrl &url, QObject \*parent = nullptr)](#OpenUrlJob)
- [OpenUrlJob(const QUrl &url, const QString &mimeType, QObject \*parent = nullptr)](#OpenUrlJob-1)
- [~OpenUrlJob()](#dtor.OpenUrlJob)
- [void setDeleteTemporaryFile(bool b)](#setDeleteTemporaryFile)
- [void setEnableExternalBrowser(bool b)](#setEnableExternalBrowser)
- [void setFollowRedirections(bool b)](#setFollowRedirections)
- [void setRunExecutables(bool allow)](#setRunExecutables)
- [void setShowOpenOrExecuteDialog(bool b)](#setShowOpenOrExecuteDialog)
- [void setStartupId(const QByteArray &startupId)](#setStartupId)
- [void setSuggestedFileName(const QString &suggestedFileName)](#setSuggestedFileName)
- [void start()](#start)
- [QUrl url() const](#url) (since 6.14)

## Signals

- [void mimeTypeFound(const QString &mimeType)](#mimeTypeFound)

## Static Public Members

- [bool isExecutableFile(const QUrl &url, const QString &mimetypeName)](#isExecutableFile)

## Detailed Description {#details}

This includes finding out its MIME type, and then the associated application, or running desktop files, executables, etc. It also honours the "use this webbrowser for all http(s) URLs" setting.

For the "Open With" dialog functionality to work, make sure to set KIO::JobUiDelegate as the delegate for this job (in widgets applications).

```cpp
// Since 5.98 use:
job->setUiDelegate(KIO::createDefaultJobUiDelegate(KJobUiDelegate::AutoHandlingEnabled, window));
// For older releases use:
job->setUiDelegate(new KIO::JobUiDelegate(KJobUiDelegate::AutoHandlingEnabled, window));
```

## Member Function Documentation {#member-function-documentation}

### \[explicit\] OpenUrlJob::OpenUrlJob(const QUrl &*url*, QObject \**parent* = nullptr) {#OpenUrlJob}

Creates an [OpenUrlJob](kio-openurljob.md) in order to open a URL.

`url` the URL of the file/directory to open

### \[explicit\] OpenUrlJob::OpenUrlJob(const QUrl &*url*, const QString &*mimeType*, QObject \**parent* = nullptr) {#OpenUrlJob-1}

Creates an [OpenUrlJob](kio-openurljob.md) for the case where the MIME type is already known.

`url` the URL of the file/directory to open

`mimeType` the type of file/directory. See [QMimeType](https://doc.qt.io/qt-6/qmimetype.html).

### \[override virtual noexcept\] OpenUrlJob::~OpenUrlJob() {#dtor.OpenUrlJob}

Destructor

Note that by default jobs auto-delete themselves after emitting result.

### \[static\] bool OpenUrlJob::isExecutableFile(const QUrl &*url*, const QString &*mimetypeName*) {#isExecutableFile}

Returns whether the `url` of type `mimetypeName` is executable. To be executable the file must pass the following rules: -\# Must reside on the local filesystem. -\# Must be marked as executable for the user by the filesystem. -\# The MIME type must inherit application/x-executable, application/x-executable-script

### \[signal\] void OpenUrlJob::mimeTypeFound(const QString &*mimeType*) {#mimeTypeFound}

Emitted when the MIME type is determined. This can be used for special cases like webbrowsers who want to embed the URL in some cases, rather than starting a different application. In that case they can kill the job.

### void OpenUrlJob::setDeleteTemporaryFile(bool *b*) {#setDeleteTemporaryFile}

Specifies that the URL passed to the application will be deleted when it exits (if the URL is a local file)

### void OpenUrlJob::setEnableExternalBrowser(bool *b*) {#setEnableExternalBrowser}

Sets whether the external webbrowser setting should be honoured.

This is enabled by default.

This should only be disabled in webbrowser applications.

`b` whether to let the external browser handle the URL or not

### void OpenUrlJob::setFollowRedirections(bool *b*) {#setFollowRedirections}

Sets whether the job should follow URL redirections.

This is enabled by default.

`b` whether to follow redirections or not.

### void OpenUrlJob::setRunExecutables(bool *allow*) {#setRunExecutables}

Set this to true if this class should allow the user to run executables. Unlike KF5's KRun, this setting is OFF by default here for security reasons. File managers can enable this, but e.g. web browsers, mail clients etc. shouldn't.

### void OpenUrlJob::setShowOpenOrExecuteDialog(bool *b*) {#setShowOpenOrExecuteDialog}

Set this to `true` if this class should show a dialog to ask the user about how to handle various types of executable files; note that executing/running remote files is disallowed as that is not secure (in the case of remote shell scripts and .desktop files, they are always opened as text in the default application):

- For native binaries: whether to execute or cancel
- For .exe files: whether to execute or cancel, ("execute" on Linux in this context means running the file with the default application (e.g. WINE))
- For executable shell scripts: whether to execute the file or open it as text in the default application; note that if the file doesn't have the execute bit, it'll always be opened as text
- For .desktop files: whether to run the file or open it as text in the default application; note that if the .desktop file is located in a non-standard location (on Linux standard locations are /usr/share/applications or ~/.local/share/applications) and does not have the execute bit, another dialog (see UntrustedProgramHandlerInterface) will be launched to ask the user whether they trust running the application (the one the .desktop file launches based on the Exec line)

Note that the dialog, ExecutableFileOpenDialog (from KIOWidgets), provides an option to remember the last value used and not ask again, if that is set, then the dialog will not be shown.

When set to `true` this will take precedence over [setRunExecutables](kio-openurljob.md#setRunExecutables) (the latter can be used to allow running executables without first asking the user for confirmation).

### void OpenUrlJob::setStartupId(const QByteArray &*startupId*) {#setStartupId}

Sets the platform-specific startup id of the application launch.

`startupId` startup id, if any (otherwise "").

For X11, this would be the id for the Startup Notification protocol.

### void OpenUrlJob::setSuggestedFileName(const QString &*suggestedFileName*) {#setSuggestedFileName}

Sets the file name to use in the case of downloading the file to a tempfile, in order to give it to a non-URL-aware application. Some apps rely on the extension to determine the MIME type of the file. Usually the file name comes from the URL, but in the case of the HTTP Content-Disposition header, we need to override the file name.

`suggestedFileName` the file name

### \[override virtual\] void OpenUrlJob::start() {#start}

Reimplements: [KJob::start()](../kcoreaddons/kjob.md#start).

Starts the job. You must call this, after having called all the needed setters. This is a GUI job, never use [exec](../kcoreaddons/kjob.md#exec)(), it would block user interaction.

### \[since 6.14\] QUrl OpenUrlJob::url() const {#url}

Returns the URL the [OpenUrlJob](kio-openurljob.md) was created with.

This function was introduced in Qt 6.14.
