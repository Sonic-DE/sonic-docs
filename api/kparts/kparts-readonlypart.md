---
title: "KParts::ReadOnlyPart Class"
description: "Base class for any \"viewer\" part."
---

# KParts::ReadOnlyPart Class

Base class for any "viewer" part. [More...](#details)

- **Header:** `#include <KParts/ReadOnlyPart>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS Parts)`  
  `target_link_libraries(mytarget PRIVATE KF6::Parts)`
- **Inherits:** [KParts::Part](kparts-part.md)
- **Inherited By:** [KParts::ReadWritePart](kparts-readwritepart.md)

[List of all members, including inherited members](kparts-readonlypart-members.md)

## Properties

- [\[read-only\] url : QUrl](#url-prop)

## Public Functions

- [ReadOnlyPart(QObject \*parent = nullptr, const KPluginMetaData &data = {})](#ReadOnlyPart)
- [KParts::OpenUrlArguments arguments() const](#arguments)
- [bool closeStream()](#closeStream)
- [bool closeUrl()](#closeUrl)
- [bool isProgressInfoEnabled() const](#isProgressInfoEnabled)
- [KParts::NavigationExtension \*navigationExtension() const](#navigationExtension)
- [bool openStream(const QString &mimeType, const QUrl &url)](#openStream)
- [void setArguments(const KParts::OpenUrlArguments &arguments)](#setArguments)
- [void setProgressInfoEnabled(bool show)](#setProgressInfoEnabled)
- [QUrl url() const](#url)
- [bool writeStream(const QByteArray &data)](#writeStream)

## Public Slots

- [bool openUrl(const QUrl &url)](#openUrl)

## Signals

- [void canceled(const QString &errMsg)](#canceled)
- [void completed()](#completed)
- [void completedWithPendingAction()](#completedWithPendingAction)
- [void started(KIO::Job \*job)](#started)
- [void urlChanged(const QUrl &url)](#urlChanged)

## Protected Functions

- [void guiActivateEvent(KParts::GUIActivateEvent \*event)](#guiActivateEvent)
- [QString localFilePath() const](#localFilePath)
- [bool openFile()](#openFile)
- [void setLocalFilePath(const QString &localFilePath)](#setLocalFilePath)
- [void setUrl(const QUrl &url)](#setUrl)

## Detailed Description {#details}

This class takes care of network transparency for you, in the simplest way (downloading to a temporary file, then letting the part load from the temporary file). To use the built-in network transparency, you only need to implement [openFile](kparts-readonlypart.md#openFile)(), not [openUrl](kparts-readonlypart.md#openUrl)().

To implement network transparency differently (e.g. for progressive loading, like a web browser does for instance), or to prevent network transparency (but why would you do that?), you can override [openUrl](kparts-readonlypart.md#openUrl)().

An application using [KParts](kparts-module.md) can use the signals to show feedback while the URL is being loaded.

[ReadOnlyPart](kparts-readonlypart.md) handles the window caption by setting it to the current URL (set in [openUrl](kparts-readonlypart.md#openUrl)(), and each time the part is activated). If you want another caption, set it in [openFile](kparts-readonlypart.md#openFile)() and, if the part might ever be used with a part manager, in [guiActivateEvent](kparts-readonlypart.md#guiActivateEvent)().

## Property Documentation {#property-documentation}

### \[read-only\] url : QUrl {#url-prop}

**Access functions:**

- `QUrl` **[url](kparts-readonlypart.md#url)**() const

## Member Function Documentation {#member-function-documentation}

### \[explicit\] ReadOnlyPart::ReadOnlyPart(QObject \**parent* = nullptr, const KPluginMetaData &*data* = {}) {#ReadOnlyPart}

Constructor.

See also Part for the setXXX methods to call.

### KParts::OpenUrlArguments ReadOnlyPart::arguments() const {#arguments}

Returns the arguments that were used to open this URL.

*See also* [setArguments](kparts-readonlypart.md#setArguments)()

### \[signal\] void ReadOnlyPart::canceled(const QString &*errMsg*) {#canceled}

Emit this if loading is canceled by the user or by an error. `errMsg` the error message, empty if the user canceled the loading voluntarily.

### bool ReadOnlyPart::closeStream() {#closeStream}

Terminate the sending of data to the part. With some data types (text, html...) closeStream might never actually be called, in the case of continuous streams, for instance plain text or HTML data.

### \[virtual\] bool ReadOnlyPart::closeUrl() {#closeUrl}

Called when closing the current URL (for example, a document), for instance when switching to another URL (note that [openUrl](kparts-readonlypart.md#openUrl)() calls it automatically in this case).

If the current URL is not fully loaded yet, aborts loading.

Deletes the temporary file used when the URL is remote.

Resets the current [url](kparts-readonlypart.md#url)() to QUrl().

Returns always `true`, but the return value exists for reimplementations

### \[signal\] void ReadOnlyPart::completed() {#completed}

Emit this when you have completed loading data.

Hosting applications will want to know when the process of loading the data is finished, so that they can access the data when everything is loaded.

### \[signal\] void ReadOnlyPart::completedWithPendingAction() {#completedWithPendingAction}

This signal is similar to the `KParts::ReadOnlyPart::completed()` signal except it is only emitted if there is still a pending action to be executed on a delayed timer.

An example of this is the meta-refresh tags on web pages used to reload/redirect after a certain period of time. This signal is useful if you want to give the user the ability to cancel such pending actions.

### \[override virtual protected\] void ReadOnlyPart::guiActivateEvent(KParts::GUIActivateEvent \**event*) {#guiActivateEvent}

Reimplements: [Part::guiActivateEvent(KParts::GUIActivateEvent \*event)](kparts-part.md#guiActivateEvent).

Reimplemented from Part, so that the window caption is set to the current URL (decoded) when the part is activated.

This is the usual behavior in 99% of applications. Reimplement if you don't like it - test for event-\>activated()!

> **Note:** This is done with [GUIActivateEvent](kparts-guiactivateevent.md) and not with [PartActivateEvent](kparts-partactivateevent.md) because it's handled by the main window (which gets the event after the [PartActivateEvent](kparts-partactivateevent.md) events have been sent).

### bool ReadOnlyPart::isProgressInfoEnabled() const {#isProgressInfoEnabled}

Returns whether the part shows the progress info dialog used by the internal KIO job.

### \[protected\] QString ReadOnlyPart::localFilePath() const {#localFilePath}

Returns the local file path associated with this part.

> **Note:** The result will only be valid if [openUrl](kparts-readonlypart.md#openUrl)() or [setLocalFilePath](kparts-readonlypart.md#setLocalFilePath)() has previously been called.

*See also* [setLocalFilePath](kparts-readonlypart.md#setLocalFilePath)()

### KParts::NavigationExtension \*ReadOnlyPart::navigationExtension() const {#navigationExtension}

This convenience method returns the [NavigationExtension](kparts-navigationextension.md) for this part, or `nullptr` if there isn't one.

### \[virtual protected\] bool ReadOnlyPart::openFile() {#openFile}

If the part uses the standard implementation of [openUrl](kparts-readonlypart.md#openUrl)(), it must reimplement this to open the local file. The default implementation simply returns false.

If this method returns true the part emits [completed](kparts-readonlypart.md#completed)(), otherwise it emits [canceled](kparts-readonlypart.md#canceled)().

*See also* [completed](kparts-readonlypart.md#completed)(), [canceled](kparts-readonlypart.md#canceled)()

### bool ReadOnlyPart::openStream(const QString &*mimeType*, const QUrl &*url*) {#openStream}

Initiate sending data to this part. This is an alternative to [openUrl](kparts-readonlypart.md#openUrl)(), which allows the user of the part to load the data itself, and send it progressively to the part.

`mimeType` the type of data that is going to be sent to this part.

`url` the URL representing this data. Although not directly used, every [ReadOnlyPart](kparts-readonlypart.md) has a URL (see [url](kparts-readonlypart.md#url)()), so this simply sets it.

Returns `true` if the part supports progressive loading and accepts data, `false` otherwise.

### \[virtual slot\] bool ReadOnlyPart::openUrl(const QUrl &*url*) {#openUrl}

Only reimplement this if you don't want the network transparency support to download from the URL into a temporary file (when the URL isn't local). Otherwise, reimplement [openFile](kparts-readonlypart.md#openFile)() only.

If you reimplement it, don't forget to set the caption, usually with

```cpp
Q_EMIT setWindowCaption( url.toDisplayString(QUrl::PreferLocalFile) );
```

and also, if the URL refers to a local file, resolve it to a local path and call [setLocalFilePath](kparts-readonlypart.md#setLocalFilePath)().

### void ReadOnlyPart::setArguments(const KParts::OpenUrlArguments &*arguments*) {#setArguments}

Sets the arguments to use for the next [openUrl](kparts-readonlypart.md#openUrl)() call.

*See also* [arguments](kparts-readonlypart.md#arguments)()

### \[protected\] void ReadOnlyPart::setLocalFilePath(const QString &*localFilePath*) {#setLocalFilePath}

Sets the local file path associated with this part.

*See also* [localFilePath](kparts-readonlypart.md#localFilePath)()

### void ReadOnlyPart::setProgressInfoEnabled(bool *show*) {#setProgressInfoEnabled}

Call this to turn off the progress info dialog used by the internal KIO job. Use this if you provide another way of displaying progress info (e.g. a statusbar), using the signals emitted by this class, and/or those emitted by the job given by [started](kparts-readonlypart.md#started)().

*See also* [isProgressInfoEnabled](kparts-readonlypart.md#isProgressInfoEnabled)()

### \[protected\] void ReadOnlyPart::setUrl(const QUrl &*url*) {#setUrl}

Sets the URL associated with this part.

*See also* [url](kparts-readonlypart.md#url)()

### \[signal\] void ReadOnlyPart::started(KIO::Job \**job*) {#started}

The part emits this when starting to load data.

If using a [KIO::Job](../kiocore/kio-job.md), it provides the `job` so that progress information can be shown. Otherwise, `job` is `nullptr`.

### QUrl ReadOnlyPart::url() const {#url}

Returns the URL currently opened in (or being opened by) this part.

> **Note:** The URL is not cleared if [openUrl](kparts-readonlypart.md#openUrl)() fails to load the URL. Call [closeUrl](kparts-readonlypart.md#closeUrl)() if you need to explicitly reset it.

> **Note:** Getter function for property [url](kparts-readonlypart.md#url-prop).

*See also* [setUrl](kparts-readonlypart.md#setUrl)()

### \[signal\] void ReadOnlyPart::urlChanged(const QUrl &*url*) {#urlChanged}

Emitted by the part when [url](kparts-readonlypart.md#url)() changes

### bool ReadOnlyPart::writeStream(const QByteArray &*data*) {#writeStream}

Send some data to the part. [openStream](kparts-readonlypart.md#openStream) must have been called previously, and must have returned `true`.

Returns `true` if the data was accepted by the part. If false is returned, the application should stop sending data, and doesn't have to call [closeStream](kparts-readonlypart.md#closeStream).
