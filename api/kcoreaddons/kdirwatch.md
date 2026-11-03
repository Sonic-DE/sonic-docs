---
title: "KDirWatch Class"
description: "Class for watching directory and file changes."
---

# KDirWatch Class

Class for watching directory and file changes. [More...](#details)

- **Header:** `#include <KDirWatch>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS CoreAddons)`  
  `target_link_libraries(mytarget PRIVATE KF6::CoreAddons)`
- **Inherits:** [QObject](https://doc.qt.io/qt-6/qobject.html)

[List of all members, including inherited members](kdirwatch-members.md)

## Public Types

- [enum KDirWatch::Method](#Method-enum)
- [enum KDirWatch::WatchMode](#WatchMode-enum)

## Public Functions

- [KDirWatch(QObject \*parent = nullptr)](#KDirWatch)
- [~KDirWatch()](#dtor.KDirWatch)
- [void addDir(const QString &path, KDirWatch::WatchModes watchModes = WatchDirOnly)](#addDir)
- [void addFile(const QString &file)](#addFile)
- [bool contains(const QString &path) const](#contains)
- [QDateTime ctime(const QString &path) const](#ctime)
- [KDirWatch::Method internalMethod() const](#internalMethod)
- [bool isStopped()](#isStopped)
- [void removeDir(const QString &path)](#removeDir)
- [void removeFile(const QString &file)](#removeFile)
- [bool restartDirScan(const QString &path)](#restartDirScan)
- [void startScan(bool notify = false, bool skippedToo = false)](#startScan)
- [bool stopDirScan(const QString &path)](#stopDirScan)
- [void stopScan()](#stopScan)

## Public Slots

- [void setCreated(const QString &path)](#setCreated)
- [void setDeleted(const QString &path)](#setDeleted)
- [void setDirty(const QString &path)](#setDirty)

## Signals

- [void created(const QString &path)](#created)
- [void deleted(const QString &path)](#deleted)
- [void dirty(const QString &path)](#dirty)

## Static Public Members

- [bool exists()](#exists)
- [KDirWatch \*self()](#self)

## Detailed Description {#details}

Watch directories and files for changes. The watched directories or files don't have to exist yet.

When a watched directory is changed, i.e. when files therein are created or deleted, [KDirWatch](kdirwatch.md) will emit the signal [dirty](kdirwatch.md#dirty)().

When a watched, but previously not existing directory gets created, [KDirWatch](kdirwatch.md) will emit the signal [created](kdirwatch.md#created)().

When a watched directory gets deleted, [KDirWatch](kdirwatch.md) will emit the signal [deleted](kdirwatch.md#deleted)(). The directory is still watched for new creation.

When a watched file is changed, i.e. attributes changed or written to, [KDirWatch](kdirwatch.md) will emit the signal [dirty](kdirwatch.md#dirty)().

Scanning of particular directories or files can be stopped temporarily and restarted. The whole class can be stopped and restarted. Directories and files can be added/removed from the list in any state.

The implementation uses the INOTIFY functionality on LINUX. As a last resort, a regular polling for change of modification times is done; the polling interval is a global config option: DirWatch/PollInterval and DirWatch/NFSPollInterval for NFS mounted directories. The choice of implementation can be adjusted by the user, with the key \[DirWatch\] PreferredMethod={Stat\|[QFSWatch](kdirwatch.md#Method-enum)\|inotify}

## Member Type Documentation {#member-type-documentation}

### enum KDirWatch::Method {#Method-enum}

| Constant | Value | Description |
| --- | --- | --- |
| `KDirWatch::INotify` | `0` | INotify |
| `KDirWatch::Stat` | `1` | Stat |
| `KDirWatch::QFSWatch` | `2` | [QFileSystemWatcher](https://doc.qt.io/qt-6/qfilesystemwatcher.html) |

### enum KDirWatch::WatchMode {#WatchMode-enum}

**flags KDirWatch::WatchModes**

Available watch modes for directory monitoring

| Constant | Value | Description |
| --- | --- | --- |
| `KDirWatch::WatchDirOnly` | `0` | Watch just the specified directory |
| `KDirWatch::WatchFiles` | `0x01` | Watch also all files contained by the directory |
| `KDirWatch::WatchSubDirs` | `0x02` | Watch also all the subdirs contained by the directory |

The `WatchModes` type is a typedef for `QFlags<WatchMode>. `It stores an OR combination of `WatchMode` values.

## Member Function Documentation {#member-function-documentation}

### \[explicit\] KDirWatch::KDirWatch(QObject \**parent* = nullptr) {#KDirWatch}

Constructor.

Scanning begins immediately when a dir/file watch is added.

`parent` the parent of the [QObject](https://doc.qt.io/qt-6/qobject.html) (or `nullptr` for parent-less KDataTools)

### \[override virtual noexcept\] KDirWatch::~KDirWatch() {#dtor.KDirWatch}

Destructor.

Stops scanning and cleans up.

### void KDirWatch::addDir(const QString &*path*, KDirWatch::WatchModes *watchModes* = WatchDirOnly) {#addDir}

Adds a directory to be watched.

The directory does not have to exist. When `watchModes` is set to [WatchDirOnly](kdirwatch.md#WatchMode-enum) (the default), the signals [dirty](kdirwatch.md#dirty)(), [created](kdirwatch.md#created)(), [deleted](kdirwatch.md#deleted)() can be emitted, all for the watched directory. When `watchModes` is set to [WatchFiles](kdirwatch.md#WatchMode-enum), all files in the watched directory are watched for changes, too. Thus, the signals [dirty](kdirwatch.md#dirty)(), [created](kdirwatch.md#created)(), [deleted](kdirwatch.md#deleted)() can be emitted. When `watchModes` is set to [WatchSubDirs](kdirwatch.md#WatchMode-enum), all subdirs are watched using the same flags specified in `watchModes` (symlinks aren't followed). If the `path` points to a symlink to a directory, the target directory is watched instead. If you want to watch the link, use `addFile()`.

`path` the path to watch

`watchModes` watch modes

*See also* [KDirWatch::WatchMode](kdirwatch.md#WatchMode-enum)

### void KDirWatch::addFile(const QString &*file*) {#addFile}

Adds a file to be watched. If it's a symlink to a directory, it watches the symlink itself.

`file` the file to watch

### bool KDirWatch::contains(const QString &*path*) const {#contains}

Check if a directory is being watched by this [KDirWatch](kdirwatch.md) instance `path` the directory to check Returns true if the directory is being watched

### \[signal\] void KDirWatch::created(const QString &*path*) {#created}

Emitted when a file or directory (being watched explicitly) is created. This is not emitted when creating a file is created in a watched directory.

`path` the path of the file or directory

*See also* [setCreated](kdirwatch.md#setCreated)()

### QDateTime KDirWatch::ctime(const QString &*path*) const {#ctime}

Returns the time the directory/file was last changed.

`path` the file to check

Returns the date of the last modification

### \[signal\] void KDirWatch::deleted(const QString &*path*) {#deleted}

Emitted when a file or directory is deleted.

The object is still watched for new creation.

`path` the path of the file or directory

*See also* [setDeleted](kdirwatch.md#setDeleted)()

### \[signal\] void KDirWatch::dirty(const QString &*path*) {#dirty}

Emitted when a watched object is changed. For a directory this signal is emitted when files therein are created or deleted. For a file this signal is emitted when its size or attributes change.

When you watch a directory, changes in the size or attributes of contained files may or may not trigger this signal to be emitted depending on which backend is used by [KDirWatch](kdirwatch.md).

The new ctime is set before the signal is emitted.

`path` the path of the file or directory

*See also* [setDirty](kdirwatch.md#setDirty)()

### \[static\] bool KDirWatch::exists() {#exists}

Returns true if there is an instance of [KDirWatch](kdirwatch.md).

*See also* [KDirWatch::self](kdirwatch.md#self)()

### KDirWatch::Method KDirWatch::internalMethod() const {#internalMethod}

Returns the preferred internal method to watch for changes.

### bool KDirWatch::isStopped() {#isStopped}

Is scanning stopped? After creation of a [KDirWatch](kdirwatch.md) instance, this is false. Returns true when scanning stopped

### void KDirWatch::removeDir(const QString &*path*) {#removeDir}

Removes a directory from the list of scanned directories.

If specified path is not in the list this does nothing.

`path` the path of the dir to be removed from the list

### void KDirWatch::removeFile(const QString &*file*) {#removeFile}

Removes a file from the list of watched files.

If specified path is not in the list this does nothing.

`file` the file to be removed from the list

### bool KDirWatch::restartDirScan(const QString &*path*) {#restartDirScan}

Restarts scanning for specified path.

It doesn't notify about the changes (by emitting a signal). The ctime value is reset.

Call it when you are finished with big operations on that path, *and* when *you* have refreshed that path.

`path` the path to restart scanning

Returns `true` if the `path` is being watched, otherwise false

*See also* [stopDirScan](kdirwatch.md#stopDirScan)()

### \[static\] KDirWatch \*KDirWatch::self() {#self}

The [KDirWatch](kdirwatch.md) instance usually globally used in an application. It is automatically deleted when the application exits.

However, you can create an arbitrary number of [KDirWatch](kdirwatch.md) instances aside from this one - for those you have to take care of memory management.

This function returns an instance of [KDirWatch](kdirwatch.md). If there is none, it will be created.

Returns a [KDirWatch](kdirwatch.md) instance

### \[slot\] void KDirWatch::setCreated(const QString &*path*) {#setCreated}

Emits [created](kdirwatch.md#created)().

`path` the path of the file or directory

*See also* [created](kdirwatch.md#created)()

### \[slot\] void KDirWatch::setDeleted(const QString &*path*) {#setDeleted}

Emits [deleted](kdirwatch.md#deleted)().

`path` the path of the file or directory

*See also* [deleted](kdirwatch.md#deleted)()

### \[slot\] void KDirWatch::setDirty(const QString &*path*) {#setDirty}

Emits [dirty](kdirwatch.md#dirty)().

`path` the path of the file or directory

*See also* [dirty](kdirwatch.md#dirty)()

### void KDirWatch::startScan(bool *notify* = false, bool *skippedToo* = false) {#startScan}

Starts scanning of all dirs in list.

`notify` If true, all changed directories (since [stopScan](kdirwatch.md#stopScan)() call) will be notified for refresh. If notify is false, all ctimes will be reset (except those who are stopped, but only if `skippedToo` is false) and changed dirs won't be notified. You can start scanning even if the list is empty. First call should be called with `false` or else all directories in list will be notified.

`skippedToo` if true, the skipped directories (scanning of which was stopped with [stopDirScan](kdirwatch.md#stopDirScan)() ) will be reset and notified for change. Otherwise, stopped directories will continue to be unnotified.

### bool KDirWatch::stopDirScan(const QString &*path*) {#stopDirScan}

Stops scanning the specified path.

The `path` is not deleted from the internal list, it is just skipped. Call this function when you perform an huge operation on this directory (copy/move big files or many files). When finished, call [restartDirScan](kdirwatch.md#restartDirScan)(path).

`path` the path to skip

Returns true if the `path` is being watched, otherwise false

*See also* [restartDirScan](kdirwatch.md#restartDirScan)()

### void KDirWatch::stopScan() {#stopScan}

Stops scanning of all directories in internal list.

The timer is stopped, but the list is not cleared.

## Related Non-Members {#related-non-members}

### QDebug operator\<\<(QDebug *debug*, const KDirWatch &*watch*) {#operator-lt-lt}

Dump debug information about the [KDirWatch::self](kdirwatch.md#self)() instance. This checks for consistency, too.
