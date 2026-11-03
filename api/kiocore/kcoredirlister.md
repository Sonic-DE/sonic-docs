---
title: "KCoreDirLister Class"
description: "Helper class for the kiojob used to list and update a directory."
---

# KCoreDirLister Class

Helper class for the kiojob used to list and update a directory. [More...](#details)

- **Header:** `#include <KCoreDirLister>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS KIO)`  
  `target_link_libraries(mytarget PRIVATE KF6::KIOCore)`
- **Inherits:** [QObject](https://doc.qt.io/qt-6/qobject.html)

[List of all members, including inherited members](kcoredirlister-members.md)

## Public Types

- [enum KCoreDirLister::OpenUrlFlag](#OpenUrlFlag-enum)
- [enum KCoreDirLister::WhichItems](#WhichItems-enum)

## Properties

- [autoErrorHandlingEnabled : bool](#autoErrorHandlingEnabled-prop)
- [autoUpdate : bool](#autoUpdate-prop)
- [delayedMimeTypes : bool](#delayedMimeTypes-prop)
- [dirOnlyMode : bool](#dirOnlyMode-prop)
- [mimeFilter : QStringList](#mimeFilter-prop)
- [nameFilter : QString](#nameFilter-prop)
- [requestMimeTypeWhileListing : bool](#requestMimeTypeWhileListing-prop)
- [showHiddenFiles : bool](#showHiddenFiles-prop)

## Public Functions

- [KCoreDirLister(QObject \*parent = nullptr)](#KCoreDirLister)
- [bool autoErrorHandlingEnabled() const](#autoErrorHandlingEnabled)
- [bool autoUpdate() const](#autoUpdate)
- [void clearMimeFilter()](#clearMimeFilter)
- [bool delayedMimeTypes() const](#delayedMimeTypes)
- [bool dirOnlyMode() const](#dirOnlyMode)
- [QList\<QUrl\> directories() const](#directories)
- [void emitChanges()](#emitChanges)
- [KFileItem findByName(const QString &name) const](#findByName)
- [KFileItem findByUrl(const QUrl &url) const](#findByUrl)
- [void forgetDirs(const QUrl &dirUrl)](#forgetDirs)
- [bool isFinished() const](#isFinished)
- [KFileItemList items(KCoreDirLister::WhichItems which = FilteredItems) const](#items)
- [KFileItemList itemsForDir(const QUrl &dirUrl, KCoreDirLister::WhichItems which = FilteredItems) const](#itemsForDir)
- [QStringList mimeFilters() const](#mimeFilters)
- [QString nameFilter() const](#nameFilter)
- [bool openUrl(const QUrl &dirUrl, KCoreDirLister::OpenUrlFlags flags = NoFlags)](#openUrl)
- [bool quickFilterMode() const](#quickFilterMode) (since 6.14)
- [bool requestMimeTypeWhileListing() const](#requestMimeTypeWhileListing)
- [KFileItem rootItem() const](#rootItem)
- [void setAutoErrorHandlingEnabled(bool enable)](#setAutoErrorHandlingEnabled)
- [void setAutoUpdate(bool enable)](#setAutoUpdate)
- [void setDelayedMimeTypes(bool delayedMimeTypes)](#setDelayedMimeTypes)
- [void setDirOnlyMode(bool dirsOnly)](#setDirOnlyMode)
- [void setMimeExcludeFilter(const QStringList &mimeList)](#setMimeExcludeFilter)
- [void setMimeFilter(const QStringList &mimeList)](#setMimeFilter)
- [void setNameFilter(const QString &filter)](#setNameFilter)
- [void setQuickFilterMode(bool quickFilterMode)](#setQuickFilterMode) (since 6.14)
- [void setRequestMimeTypeWhileListing(bool request)](#setRequestMimeTypeWhileListing)
- [void setShowHiddenFiles(bool showHiddenFiles)](#setShowHiddenFiles)
- [bool showHiddenFiles() const](#showHiddenFiles)
- [void stop()](#stop)
- [void stop(const QUrl &dirUrl)](#stop-1)
- [void updateDirectory(const QUrl &dirUrl)](#updateDirectory)
- [QUrl url() const](#url)

## Signals

- [void canceled()](#canceled)
- [void clear()](#clear)
- [void clearDir(const QUrl &dirUrl)](#clearDir)
- [void completed()](#completed)
- [void infoMessage(const QString &msg)](#infoMessage)
- [void itemsAdded(const QUrl &directoryUrl, const KFileItemList &items)](#itemsAdded)
- [void itemsDeleted(const KFileItemList &items)](#itemsDeleted)
- [void itemsFilteredByMime(const KFileItemList &items)](#itemsFilteredByMime)
- [void jobError(KIO::Job \*job)](#jobError)
- [void listingDirCanceled(const QUrl &dirUrl)](#listingDirCanceled)
- [void listingDirCompleted(const QUrl &dirUrl)](#listingDirCompleted)
- [void newItems(const KFileItemList &items)](#newItems)
- [void percent(int percent)](#percent)
- [void processedSize(KIO::filesize\_t size)](#processedSize)
- [void redirection(const QUrl &oldUrl, const QUrl &newUrl)](#redirection)
- [void refreshItems(const QList\<QPair\<KFileItem, KFileItem\>\> &items)](#refreshItems)
- [void speed(int bytes\_per\_second)](#speed)
- [void started(const QUrl &dirUrl)](#started)
- [void totalSize(KIO::filesize\_t size)](#totalSize)

## Static Public Members

- [KFileItem cachedItemForUrl(const QUrl &url)](#cachedItemForUrl)

## Protected Functions

- [void jobStarted(KIO::ListJob \*)](#jobStarted)

## Detailed Description {#details}

The dir lister deals with the kiojob used to list and update a directory and has signals for the user of this class (e.g. konqueror view or kdesktop) to create/destroy its items when asked.

This class is independent from the graphical representation of the dir (icon container, tree view, ...) and it stores the items (as KFileItems).

Typical usage:

- Create an instance.
- Connect to at least update, clear, [itemsAdded](kcoredirlister.md#itemsAdded), and [itemsDeleted](kcoredirlister.md#itemsDeleted).
- Call [openUrl](kcoredirlister.md#openUrl) - the signals will be called.
- Reuse the instance when opening a new url ([openUrl](kcoredirlister.md#openUrl)).
- Destroy the instance when not needed anymore (usually destructor).

Advanced usage : call [openUrl](kcoredirlister.md#openUrl) with [OpenUrlFlag::Keep](kcoredirlister.md#OpenUrlFlag-enum) to list directories without forgetting the ones previously read (e.g. for a tree view)

## Member Type Documentation {#member-type-documentation}

### enum KCoreDirLister::OpenUrlFlag {#OpenUrlFlag-enum}

**flags KCoreDirLister::OpenUrlFlags**

| Constant | Value | Description |
| --- | --- | --- |
| `KCoreDirLister::NoFlags` | `0x0` | No additional flags specified. |
| `KCoreDirLister::Keep` | `0x1` | Previous directories aren't forgotten. (they are still watched by kdirwatch and their items are kept for this [KCoreDirLister](kcoredirlister.md)). This is useful for e.g. a treeview. |
| `KCoreDirLister::Reload` | `0x2` | Indicates whether to use the cache or to reread the directory from the disk. Use only when opening a dir not yet listed by this lister without using the cache. Otherwise use [updateDirectory](kcoredirlister.md#updateDirectory). |

The `OpenUrlFlags` type is a typedef for `QFlags<OpenUrlFlag>. `It stores an OR combination of `OpenUrlFlag` values.

### enum KCoreDirLister::WhichItems {#WhichItems-enum}

Used by [items](kcoredirlister.md#items)() and [itemsForDir](kcoredirlister.md#itemsForDir)() to specify whether you want all items for a directory or just the filtered ones.

| Constant |   |
| --- | --- |
| `KCoreDirLister::AllItems` | `0` |
| `KCoreDirLister::FilteredItems` | `1` |

## Property Documentation {#property-documentation}

### autoErrorHandlingEnabled : bool {#autoErrorHandlingEnabled-prop}

**Access functions:**

- `bool` **[autoErrorHandlingEnabled](kcoredirlister.md#autoErrorHandlingEnabled)**() const
- `void` **[setAutoErrorHandlingEnabled](kcoredirlister.md#setAutoErrorHandlingEnabled)**(`bool` *enable*)

### autoUpdate : bool {#autoUpdate-prop}

**Access functions:**

- `bool` **[autoUpdate](kcoredirlister.md#autoUpdate)**() const
- `void` **[setAutoUpdate](kcoredirlister.md#setAutoUpdate)**(`bool` *enable*)

### delayedMimeTypes : bool {#delayedMimeTypes-prop}

**Access functions:**

- `bool` **[delayedMimeTypes](kcoredirlister.md#delayedMimeTypes)**() const
- `void` **[setDelayedMimeTypes](kcoredirlister.md#setDelayedMimeTypes)**(`bool` *delayedMimeTypes*)

### dirOnlyMode : bool {#dirOnlyMode-prop}

**Access functions:**

- `bool` **[dirOnlyMode](kcoredirlister.md#dirOnlyMode)**() const
- `void` **[setDirOnlyMode](kcoredirlister.md#setDirOnlyMode)**(`bool` *dirsOnly*)

### mimeFilter : QStringList {#mimeFilter-prop}

**Access functions:**

- `QStringList` **[mimeFilters](kcoredirlister.md#mimeFilters)**() const
- `void` **[setMimeFilter](kcoredirlister.md#setMimeFilter)**(const `QStringList` &*mimeList*)
- `void` **[clearMimeFilter](kcoredirlister.md#clearMimeFilter)**()

### nameFilter : QString {#nameFilter-prop}

**Access functions:**

- `QString` **[nameFilter](kcoredirlister.md#nameFilter)**() const
- `void` **[setNameFilter](kcoredirlister.md#setNameFilter)**(const `QString` &*filter*)

### requestMimeTypeWhileListing : bool {#requestMimeTypeWhileListing-prop}

**Access functions:**

- `bool` **[requestMimeTypeWhileListing](kcoredirlister.md#requestMimeTypeWhileListing)**() const
- `void` **[setRequestMimeTypeWhileListing](kcoredirlister.md#setRequestMimeTypeWhileListing)**(`bool` *request*)

### showHiddenFiles : bool {#showHiddenFiles-prop}

**Access functions:**

- `bool` **[showHiddenFiles](kcoredirlister.md#showHiddenFiles)**() const
- `void` **[setShowHiddenFiles](kcoredirlister.md#setShowHiddenFiles)**(`bool` *showHiddenFiles*)

## Member Function Documentation {#member-function-documentation}

### KCoreDirLister::KCoreDirLister(QObject \**parent* = nullptr) {#KCoreDirLister}

Create a directory lister.

### bool KCoreDirLister::autoErrorHandlingEnabled() const {#autoErrorHandlingEnabled}

Checks whether auto error handling is enabled.

If enabled, it will show an error dialog to the user when an error occurs (assuming the application links to [KIOWidgets](../kiowidgets/kiowidgets-module.md)). It is turned on by default.

Returns `true` if auto error handling is enabled, `false` otherwise

> **Note:** Getter function for property [autoErrorHandlingEnabled](kcoredirlister.md#autoErrorHandlingEnabled-prop).

*See also* [setAutoErrorHandlingEnabled](kcoredirlister.md#setAutoErrorHandlingEnabled)()

### bool KCoreDirLister::autoUpdate() const {#autoUpdate}

Checks whether [KDirWatch](../kcoreaddons/kdirwatch.md) will automatically update directories. This is enabled by default.

Returns `true` if [KDirWatch](../kcoreaddons/kdirwatch.md) is used to automatically update directories

> **Note:** Getter function for property [autoUpdate](kcoredirlister.md#autoUpdate-prop).

*See also* [setAutoUpdate](kcoredirlister.md#setAutoUpdate)()

### \[static\] KFileItem KCoreDirLister::cachedItemForUrl(const QUrl &*url*) {#cachedItemForUrl}

Return the [KFileItem](kfileitem.md) for the given URL, if it was listed recently and it's still in the cache, which is always the case if a directory view is currently showing this item. If not, then it might be in the cache; if not in the cache a a null [KFileItem](kfileitem.md) will be returned.

If you really need a [KFileItem](kfileitem.md) for this URL in all cases, then use [KIO::stat](kio-statjob.md#stat)() instead.

### \[signal\] void KCoreDirLister::canceled() {#canceled}

Tell the view that the user canceled the listing. No running jobs are left.

### \[signal\] void KCoreDirLister::clear() {#clear}

Signals to the view to remove all items (when e.g. going from dirA to dirB). Make sure to connect to this signal to avoid having duplicate items in the view.

### \[signal\] void KCoreDirLister::clearDir(const QUrl &*dirUrl*) {#clearDir}

Signals to the view to clear all items from directory `dirUrl`.

This is only emitted if the lister is holding more than one directory.

`dirUrl` the directory that the view should clear all items from

### void KCoreDirLister::clearMimeFilter() {#clearMimeFilter}

Clears the MIME type based filter.

You need to call [emitChanges](kcoredirlister.md#emitChanges)() afterwards.

> **Note:** Resetter function for property [mimeFilter](kcoredirlister.md#mimeFilter-prop).

*See also* [setMimeFilter](kcoredirlister.md#setMimeFilter)

### \[signal\] void KCoreDirLister::completed() {#completed}

Tell the view that listing is finished. There are no jobs running anymore.

### bool KCoreDirLister::delayedMimeTypes() const {#delayedMimeTypes}

Returns `true` if the "delayed MIME types" feature was enabled

> **Note:** Getter function for property [delayedMimeTypes](kcoredirlister.md#delayedMimeTypes-prop).

*See also* [setDelayedMimeTypes](kcoredirlister.md#setDelayedMimeTypes)

### bool KCoreDirLister::dirOnlyMode() const {#dirOnlyMode}

Checks whether this [KCoreDirLister](kcoredirlister.md) only lists directories or all items (directories and files), by default all items are listed.

Returns `true` if only directories are listed, `false` otherwise

> **Note:** Getter function for property [dirOnlyMode](kcoredirlister.md#dirOnlyMode-prop).

*See also* [setDirOnlyMode](kcoredirlister.md#setDirOnlyMode)()

### QList\<QUrl\> KCoreDirLister::directories() const {#directories}

Returns all URLs that are listed by this [KCoreDirLister](kcoredirlister.md). This is only useful if you called [openUrl](kcoredirlister.md#openUrl)() with [OpenUrlFlag::Keep](kcoredirlister.md#OpenUrlFlag-enum), as it happens in a treeview, for example. (Note that the base url is included in the list as well, of course.)

### void KCoreDirLister::emitChanges() {#emitChanges}

Actually emit the changes made with [setShowHiddenFiles](kcoredirlister.md#setShowHiddenFiles), [setDirOnlyMode](kcoredirlister.md#setDirOnlyMode), [setNameFilter](kcoredirlister.md#setNameFilter) and [setMimeFilter](kcoredirlister.md#setMimeFilter).

### KFileItem KCoreDirLister::findByName(const QString &*name*) const {#findByName}

Find an item by its name. `name` the item name

### KFileItem KCoreDirLister::findByUrl(const QUrl &*url*) const {#findByUrl}

Find an item by its URL.

`url` the item URL

### void KCoreDirLister::forgetDirs(const QUrl &*dirUrl*) {#forgetDirs}

Stop listening for further changes in the given directory. When a new directory is opened with [OpenUrlFlag::Keep](kcoredirlister.md#OpenUrlFlag-enum) the caller will keep being notified of file changes for all directories that were kept open. This call selectively removes a directory from sending future notifications to this [KCoreDirLister](kcoredirlister.md).

`dirUrl` the directory URL.

### \[signal\] void KCoreDirLister::infoMessage(const QString &*msg*) {#infoMessage}

Emitted to display information about running jobs.

Examples of message are "Resolving host", "Connecting to host...", etc.

`msg` the info message

### bool KCoreDirLister::isFinished() const {#isFinished}

Returns `true` if no I/O operation is currently in progress.

Returns `true` if finished, `false` otherwise

### KFileItemList KCoreDirLister::items(KCoreDirLister::WhichItems *which* = FilteredItems) const {#items}

Returns the items listed for the current [url](kcoredirlister.md#url)().

This method will not start listing a directory, you should only call this in a slot connected to the finished() signal.

The items in the [KFileItemList](kfileitemlist.md) are copies of the items used by [KCoreDirLister](kcoredirlister.md).

`which` specifies whether the returned list will contain all entries or only the ones that passed the [nameFilter](kcoredirlister.md#nameFilter)(), mimeFilter(), etc. Note that the latter causes iteration over all the items, filtering them. If this is too slow for you, use the [newItems](kcoredirlister.md#newItems)() signal, sending out filtered items in chunks

### \[signal\] void KCoreDirLister::itemsAdded(const QUrl &*directoryUrl*, const KFileItemList &*items*) {#itemsAdded}

Signal that new items were found during directory listing. Alternative signal emitted at the same time as [newItems](kcoredirlister.md#newItems)(), but itemsAdded also passes the url of the parent directory.

`items` a list of new items

### \[signal\] void KCoreDirLister::itemsDeleted(const KFileItemList &*items*) {#itemsDeleted}

Signal that items have been deleted

`items` the list of deleted items

### \[signal\] void KCoreDirLister::itemsFilteredByMime(const KFileItemList &*items*) {#itemsFilteredByMime}

Send a list of items filtered-out by MIME type.

`items` the list of filtered items

### KFileItemList KCoreDirLister::itemsForDir(const QUrl &*dirUrl*, KCoreDirLister::WhichItems *which* = FilteredItems) const {#itemsForDir}

Returns the items listed for the given `dirUrl`.

This method will not start listing `dirUrl`, you should only call this in a slot connected to the finished() signal.

The items in the [KFileItemList](kfileitemlist.md) are copies of the items used by [KCoreDirLister](kcoredirlister.md).

`dirUrl` specifies the url for which the items should be returned. This is only useful if you use [KCoreDirLister](kcoredirlister.md) with multiple URLs i.e. using bool [OpenUrlFlag::Keep](kcoredirlister.md#OpenUrlFlag-enum) in [openUrl](kcoredirlister.md#openUrl)()

`which` specifies whether the returned list will contain all entries or only the ones that passed the [nameFilter](kcoredirlister.md#nameFilter), [mimeFilter](kcoredirlister.md#mimeFilter-prop), etc. Note that the latter causes iteration over all the items, filtering them. If this is too slow for you, use the [newItems](kcoredirlister.md#newItems)() signal, sending out filtered items in chunks

Returns the items listed for `dirUrl`

### \[signal\] void KCoreDirLister::jobError(KIO::Job \**job*) {#jobError}

Emitted if listing a directory fails with an error.

A typical implementation in a widgets-based application would show a message box by calling this in a slot connected to this signal:

```cpp
job->uiDelegate()->showErrorMessage()
```

Many applications might prefer to embed the error message though (e.g. by using the KMessageWidget class, from the KWidgetsAddons Framework).

`the` job with an error

### \[virtual protected\] void KCoreDirLister::jobStarted(*KIO::ListJob \**) {#jobStarted}

Reimplemented by [KDirLister](../kiowidgets/kdirlister.md) to associate windows with jobs

### \[signal\] void KCoreDirLister::listingDirCanceled(const QUrl &*dirUrl*) {#listingDirCanceled}

Tell the view that the listing of the directory `dirUrl` was canceled. There might be other running jobs left.

`dirUrl` the directory URL

### \[signal\] void KCoreDirLister::listingDirCompleted(const QUrl &*dirUrl*) {#listingDirCompleted}

Tell the view that the listing of the directory `dirUrl` is finished. There might be other running jobs left.

`dirUrl` the directory URL

### QStringList KCoreDirLister::mimeFilters() const {#mimeFilters}

Returns the list of MIME type based filters, as set via [setMimeFilter](kcoredirlister.md#setMimeFilter)().

Empty, when no MIME type filter is set.

> **Note:** Getter function for property [mimeFilter](kcoredirlister.md#mimeFilter-prop).

### QString KCoreDirLister::nameFilter() const {#nameFilter}

Returns the current name filter, as set via [setNameFilter](kcoredirlister.md#setNameFilter)().

Can be QString() if filtering is turned off

> **Note:** Getter function for property [nameFilter](kcoredirlister.md#nameFilter-prop).

*See also* [setNameFilter](kcoredirlister.md#setNameFilter)()

### \[signal\] void KCoreDirLister::newItems(const KFileItemList &*items*) {#newItems}

Signal new items.

`items` a list of new items

### bool KCoreDirLister::openUrl(const QUrl &*dirUrl*, KCoreDirLister::OpenUrlFlags *flags* = NoFlags) {#openUrl}

Run the directory lister on the given url.

This method causes [KCoreDirLister](kcoredirlister.md) to emit all the items of `dirUrl`, in any case. Depending on `flags`, either [clear](kcoredirlister.md#clear)() or [clearDir](kcoredirlister.md#clearDir)(const [QUrl](https://doc.qt.io/qt-6/qurl.html) &) will be emitted first.

The [newItems](kcoredirlister.md#newItems)() signal may be emitted more than once to supply you with KFileItems, up until the signal [completed](kcoredirlister.md#completed)() is emitted (and [isFinished](kcoredirlister.md#isFinished)() returns `true`).

`dirUrl` the directory URL.

`flags` whether to keep previous directories, and whether to reload, see [OpenUrlFlags](kcoredirlister.md#OpenUrlFlag-enum)

Returns `true` if successful, `false` otherwise (e.g. if `dirUrl` is invalid)

### \[signal\] void KCoreDirLister::percent(int *percent*) {#percent}

Progress signal showing the overall progress of the [KCoreDirLister](kcoredirlister.md).

This allows using a progress bar very easily. (see QProgressBar)

`percent` the progress in percent

### \[signal\] void KCoreDirLister::processedSize(KIO::filesize\_t *size*) {#processedSize}

Regularly emitted to show the progress of this [KCoreDirLister](kcoredirlister.md).

`size` the processed size in bytes

### \[since 6.14\] bool KCoreDirLister::quickFilterMode() const {#quickFilterMode}

Returns true if quickfiltering is enabled.

If true, list only files that match the filter text.

Returns `true` if any files and folders matching filter are listed, `false` otherwise.

This function was introduced in Qt 6.14.

*See also* [setQuickFilterMode](kcoredirlister.md#setQuickFilterMode)(bool)

### \[signal\] void KCoreDirLister::redirection(const QUrl &*oldUrl*, const QUrl &*newUrl*) {#redirection}

Signals a redirection.

`oldUrl` the original URL

`newUrl` the new URL

### \[signal\] void KCoreDirLister::refreshItems(const QList\<QPair\<KFileItem, KFileItem\>\> &*items*) {#refreshItems}

Signal an item to refresh (its MIME-type/icon/name has changed).

> **Note:** [KFileItem::refresh](kfileitem.md#refresh) has already been called on those items.

`items` the items to refresh. This is a list of pairs, where the first item in the pair is the OLD item, and the second item is the NEW item. This allows to track which item has changed, especially after a renaming.

### bool KCoreDirLister::requestMimeTypeWhileListing() const {#requestMimeTypeWhileListing}

Checks whether this [KCoreDirLister](kcoredirlister.md) requests the MIME type of files from the worker.

Enabling this will tell the worker used for listing that it should try to determine the mime type of entries while listing them. This potentially reduces the speed at which entries are listed but ensures mime types are immediately available when an entry is added, greatly speeding up things like mime type filtering.

By default this is disabled.

Returns `true` if the worker is asked for MIME types, `false` otherwise.

> **Note:** Getter function for property [requestMimeTypeWhileListing](kcoredirlister.md#requestMimeTypeWhileListing-prop).

*See also* [setRequestMimeTypeWhileListing](kcoredirlister.md#setRequestMimeTypeWhileListing)()

### KFileItem KCoreDirLister::rootItem() const {#rootItem}

Returns the file item of the URL.

Can return an empty [KFileItem](kfileitem.md).

Returns the file item for [url](kcoredirlister.md#url)() itself (".")

### void KCoreDirLister::setAutoErrorHandlingEnabled(bool *enable*) {#setAutoErrorHandlingEnabled}

Enable or disable auto error handling.

If enabled, it will show an error dialog to the user when an error occurs. It is turned on by default.

`enable` true to enable auto error handling, false to disable

`parent` the parent widget for the error dialogs, can be `nullptr` for top-level

> **Note:** Setter function for property [autoErrorHandlingEnabled](kcoredirlister.md#autoErrorHandlingEnabled-prop).

*See also* [autoErrorHandlingEnabled](kcoredirlister.md#autoErrorHandlingEnabled)()

### void KCoreDirLister::setAutoUpdate(bool *enable*) {#setAutoUpdate}

Toggle automatic directory updating, when a directory changes (using [KDirWatch](../kcoreaddons/kdirwatch.md)).

`enable` set to `true` to enable or `false` to disable

> **Note:** Setter function for property [autoUpdate](kcoredirlister.md#autoUpdate-prop).

*See also* [autoUpdate](kcoredirlister.md#autoUpdate)()

### void KCoreDirLister::setDelayedMimeTypes(bool *delayedMimeTypes*) {#setDelayedMimeTypes}

Delayed MIME types feature: If enabled, MIME types will be fetched on demand, which leads to a faster initial directory listing, where icons get progressively replaced with the correct one while you run [KFileItem::determineMimeType](kfileitem.md#determineMimeType)() through the items with unknown or imprecise MIME type (e.g. files with no extension or an unknown extension).

> **Note:** Setter function for property [delayedMimeTypes](kcoredirlister.md#delayedMimeTypes-prop).

*See also* [delayedMimeTypes](kcoredirlister.md#delayedMimeTypes)()

### void KCoreDirLister::setDirOnlyMode(bool *dirsOnly*) {#setDirOnlyMode}

Call this to list only directories (by default all items (directories and files) are listed).

You need to call [emitChanges](kcoredirlister.md#emitChanges)() afterwards.

`dirsOnly` set to `true` to list only directories

> **Note:** Setter function for property [dirOnlyMode](kcoredirlister.md#dirOnlyMode-prop).

*See also* [dirOnlyMode](kcoredirlister.md#dirOnlyMode)()

### void KCoreDirLister::setMimeExcludeFilter(const QStringList &*mimeList*) {#setMimeExcludeFilter}

Filtering should be done with [KFileFilter](kfilefilter.md). This will be implemented in a later revision of [KCoreDirLister](kcoredirlister.md). This method may be removed then.

Set MIME type based exclude filter to only list items not matching the given MIME types Since 6.20 mime globs such as "image/\*" are supported.

> **Note:** setting the filter does not automatically reload directory. Also calling this function will not affect any named filter already set.

`mimeList` a list of MIME types

*See also* [clearMimeFilter](kcoredirlister.md#clearMimeFilter)

### void KCoreDirLister::setMimeFilter(const QStringList &*mimeList*) {#setMimeFilter}

Set MIME type based filter to only list items matching the given MIME types. Since 6.20 mime globs such as "image/\*" are supported.

> **Note:** Setting the filter does not automatically reload directory. Also calling this function will not affect any named filter already set.

You need to call [emitChanges](kcoredirlister.md#emitChanges)() afterwards.

`mimeList` a list of MIME types

> **Note:** Setter function for property [mimeFilter](kcoredirlister.md#mimeFilter-prop).

*See also* [clearMimeFilter](kcoredirlister.md#clearMimeFilter)

### void KCoreDirLister::setNameFilter(const QString &*filter*) {#setNameFilter}

Set a name filter to only list items matching this name, e.g. "\*.cpp".

You can set more than one filter by separating them with whitespace, e.g "\*.cpp \*.h".

> **Note:** the directory is not automatically reloaded. You need to call [emitChanges](kcoredirlister.md#emitChanges)() afterwards.

`filter` the new filter, QString() to disable filtering

> **Note:** Setter function for property [nameFilter](kcoredirlister.md#nameFilter-prop).

*See also* [nameFilter](kcoredirlister.md#nameFilter)()

### \[since 6.14\] void KCoreDirLister::setQuickFilterMode(bool *quickFilterMode*) {#setQuickFilterMode}

Call this to set the quick filtering mode on, which will filter through all the items based by their name, ignoring them if the name does not fit.

This is equal to the Dolphin quick filter mode.

You need to call [emitChanges](kcoredirlister.md#emitChanges)() afterwards.

`quickFilterMode` set to `true` to list only files and folders that match the filter text.

This function was introduced in Qt 6.14.

*See also* [quickFilterMode](kcoredirlister.md#quickFilterMode)()

### void KCoreDirLister::setRequestMimeTypeWhileListing(bool *request*) {#setRequestMimeTypeWhileListing}

Toggles whether to request MIME types from the worker or in-process.

`request` set to `true` to request MIME types from the worker.

> **Note:** If this is changed while the lister is already listing a directory, it will only have an effect the next time [openUrl](kcoredirlister.md#openUrl)() is called.

> **Note:** Setter function for property [requestMimeTypeWhileListing](kcoredirlister.md#requestMimeTypeWhileListing-prop).

*See also* [requestMimeTypeWhileListing](kcoredirlister.md#requestMimeTypeWhileListing)()

### void KCoreDirLister::setShowHiddenFiles(bool *showHiddenFiles*) {#setShowHiddenFiles}

Toggles whether hidden files (e.g. files whose name start with '.' on Unix) are shown/ By default hidden files are not shown.

You need to call [emitChanges](kcoredirlister.md#emitChanges)() afterwards.

`showHiddenFiles` set to true/false to show/hide hidden files respectively

> **Note:** Setter function for property [showHiddenFiles](kcoredirlister.md#showHiddenFiles-prop).

*See also* [showHiddenFiles](kcoredirlister.md#showHiddenFiles)()

### bool KCoreDirLister::showHiddenFiles() const {#showHiddenFiles}

Checks whether hidden files (e.g. files whose name start with '.' on Unix) will be shown. By default this option is disabled (hidden files are not shown).

Returns `true` if hidden files are shown, `false` otherwise

> **Note:** Getter function for property [showHiddenFiles](kcoredirlister.md#showHiddenFiles-prop).

*See also* [setShowHiddenFiles](kcoredirlister.md#setShowHiddenFiles)()

### \[signal\] void KCoreDirLister::speed(int *bytes\_per\_second*) {#speed}

Emitted to display information about the speed of the jobs.

`bytes_per_second` the speed in bytes/s

### \[signal\] void KCoreDirLister::started(const QUrl &*dirUrl*) {#started}

Tell the view that this [KCoreDirLister](kcoredirlister.md) has started to list `dirUrl`. Note that this does not imply that there is really a job running! I.e. KCoreDirLister::jobs() may return an empty list, in which case the items are taken from the cache.

The view knows that [openUrl](kcoredirlister.md#openUrl) should start it, so this might seem useless, but the view also needs to know when an automatic update happens.

`dirUrl` the URL to list

### void KCoreDirLister::stop() {#stop}

Stop listing all directories currently being listed.

Emits [canceled](kcoredirlister.md#canceled)() if there was at least one job running. Emits [listingDirCanceled](kcoredirlister.md#listingDirCanceled)(const [QUrl](https://doc.qt.io/qt-6/qurl.html) &) for each stopped job if there is more than one directory being watched by this [KCoreDirLister](kcoredirlister.md).

### void KCoreDirLister::stop(const QUrl &*dirUrl*) {#stop-1}

Stop listing the given directory.

Emits [canceled](kcoredirlister.md#canceled)() if the killed job was the last running one. Emits [listingDirCanceled](kcoredirlister.md#listingDirCanceled)(const [QUrl](https://doc.qt.io/qt-6/qurl.html) &) for the killed job if there is more than one directory being watched by this [KCoreDirLister](kcoredirlister.md).

No signal is emitted if there was no job running for `dirUrl`.

`dirUrl` the directory URL

### \[signal\] void KCoreDirLister::totalSize(KIO::filesize\_t *size*) {#totalSize}

Emitted when we know the size of the jobs.

`size` the total size in bytes

### void KCoreDirLister::updateDirectory(const QUrl &*dirUrl*) {#updateDirectory}

Update the directory `dirUrl`. This method causes [KCoreDirLister](kcoredirlister.md) to only emit the items of `dirUrl` that actually changed compared to the current state in the cache, and updates the cache.

The current implementation calls updateDirectory automatically for local files, using [KDirWatch](../kcoreaddons/kdirwatch.md) (if [autoUpdate](kcoredirlister.md#autoUpdate)() is `true`), but it might be useful to force an update manually.

`dirUrl` the directory URL

### QUrl KCoreDirLister::url() const {#url}

Returns the top level URL that is listed by this [KCoreDirLister](kcoredirlister.md).

It might be different from the one given with [openUrl](kcoredirlister.md#openUrl)() if there was a redirection. If you called [openUrl](kcoredirlister.md#openUrl)() with [OpenUrlFlag::Keep](kcoredirlister.md#OpenUrlFlag-enum) this is the first url opened (e.g. in a treeview this is the root).
