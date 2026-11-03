---
title: "KAutoSaveFile Class"
description: "Creates and manages a temporary \"auto-save\" file."
---

# KAutoSaveFile Class

Creates and manages a temporary "auto-save" file. [More...](#details)

- **Header:** `#include <KAutoSaveFile>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS CoreAddons)`  
  `target_link_libraries(mytarget PRIVATE KF6::CoreAddons)`
- **Inherits:** [QFile](https://doc.qt.io/qt-6/qfile.html)

[List of all members, including inherited members](kautosavefile-members.md)

## Public Functions

- [KAutoSaveFile(const QUrl &filename, QObject \*parent = nullptr)](#KAutoSaveFile)
- [KAutoSaveFile(QObject \*parent = nullptr)](#KAutoSaveFile-1)
- [~KAutoSaveFile()](#dtor.KAutoSaveFile)
- [QUrl managedFile() const](#managedFile)
- [bool open(QIODeviceBase::OpenMode openmode)](#open)
- [void releaseLock()](#releaseLock)
- [void setManagedFile(const QUrl &filename)](#setManagedFile)

## Static Public Members

- [QList\<KAutoSaveFile \*\> allStaleFiles(const QString &applicationName = QString())](#allStaleFiles)
- [QList\<KAutoSaveFile \*\> staleFiles(const QUrl &url, const QString &applicationName = QString())](#staleFiles)

## Detailed Description {#details}

Autosave files are temporary files that applications use to store the unsaved data in a file they have open for editing. [KAutoSaveFile](kautosavefile.md) allows you to easily create and manage such files, as well as to recover the unsaved data left over by a crashed or otherwise gone process.

Each [KAutoSaveFile](kautosavefile.md) object is associated with one specific file that the application holds open. [KAutoSaveFile](kautosavefile.md) is also a [QObject](https://doc.qt.io/qt-6/qobject.html), so it can be reparented to the actual opened file object, so as to manage the lifetime of the temporary file.

Typical use consists of:

- verifying whether stale autosave files exist for the opened file
- deciding whether to recover the old, autosaved data
- if not recovering, creating a [KAutoSaveFile](kautosavefile.md) object for the opened file
- during normal execution of the program, periodically save unsaved data into the [KAutoSaveFile](kautosavefile.md) file.

[KAutoSaveFile](kautosavefile.md) holds a lock on the autosave file, so it's safe to delete the file and recreate it later. Because of that, disposing of stale autosave files should be done with [releaseLock](kautosavefile.md#releaseLock)(). No lock is held on the managed file.

Examples: Opening a new file:

```cpp
void Document::open(const QUrl &url)
{
    // check whether autosave files exist:
    const QList<KAutoSaveFile *> staleFiles = KAutoSaveFile::staleFiles(url);
    if (!staleFiles.isEmpty()) {
        if (KMessageBox::questionTwoActions(parent,
                                            "Auto-saved files exist. Do you want to recover them now?",
                                            "File Recovery",
                                            KGuiItem("Recover"), KGuiItem("Do Not recover")) == KMessageBox::PrimaryAction) {
            recoverFiles(staleFiles);
            return;
        } else {
            // remove the stale files
            for (KAutoSaveFile *stale : staleFiles) {
                stale->open(QIODevice::ReadWrite);
                delete stale;
            }
        }
    }

    // create new autosave object
    m_autosave = new KAutoSaveFile(url, this);

    // continue the process of opening file 'url'
    ...
}
```

The function recoverFiles could loop over the list of files and do this:

```cpp
for (KAutoSaveFile *stale : staleFiles) {
    if (!stale->open(QIODevice::ReadWrite)) {
        // show an error message; we could not steal the lockfile
        // maybe another application got to the file before us?
        delete stale;
        continue;
    }
    Document *doc = new Document;
    doc->m_autosave = stale;
    stale->setParent(doc); // reparent

    doc->setUrl(stale->managedFile());
    doc->setContents(stale->readAll());
    doc->setState(Document::Modified); // mark it as modified and unsaved

    documentManager->addDocument(doc);
}
```

If the file is unsaved, periodically write the contents to the save file:

```cpp
if (!m_autosave->isOpen() && !m_autosave->open(QIODevice::ReadWrite)) {
    // show error: could not open the autosave file
}
m_autosave->write(contents());
```

When the user saves the file, the autosaved file is no longer necessary and can be removed or emptied.

```cpp
m_autosave->resize(0);    // leaves the file open
```

```cpp
m_autosave->remove();     // closes the file
```

## Member Function Documentation {#member-function-documentation}

### \[explicit\] KAutoSaveFile::KAutoSaveFile(const QUrl &*filename*, QObject \**parent* = nullptr) {#KAutoSaveFile}

Constructs a [KAutoSaveFile](kautosavefile.md) for file `filename`. The temporary file is not opened or created until actually needed. The file `filename` does not have to exist for [KAutoSaveFile](kautosavefile.md) to be constructed (if it exists, it will not be touched).

`filename` the filename that this [KAutoSaveFile](kautosavefile.md) refers to

`parent` the parent object

### \[explicit\] KAutoSaveFile::KAutoSaveFile(QObject \**parent* = nullptr) {#KAutoSaveFile-1}

Constructs a [KAutoSaveFile](kautosavefile.md) object. Note that you need to call [setManagedFile](kautosavefile.md#setManagedFile)() before calling [open](kautosavefile.md#open)().

`parent` the parent object

This is an overloaded function.

### \[override virtual noexcept\] KAutoSaveFile::~KAutoSaveFile() {#dtor.KAutoSaveFile}

Destroys the [KAutoSaveFile](kautosavefile.md) object, removes the autosave file and drops the lock being held (if any).

### \[static\] QList\<KAutoSaveFile \*\> KAutoSaveFile::allStaleFiles(const QString &*applicationName* = QString()) {#allStaleFiles}

Returns all stale autosave files left behind by crashed or otherwise gone instances of this application.

If not given, the application name is obtained from [QCoreApplication](https://doc.qt.io/qt-6/qcoreapplication.html), so be sure to have set it correctly before calling this function.

See [staleFiles](kautosavefile.md#staleFiles)() for information on the returned objects.

The application owns all returned [KAutoSaveFile](kautosavefile.md) objects and is responsible for deleting them when no longer needed. Remember that deleting the [KAutoSaveFile](kautosavefile.md) will release the file lock and remove the stale autosave file.

### QUrl KAutoSaveFile::managedFile() const {#managedFile}

Retrieves the URL of the file managed by [KAutoSaveFile](kautosavefile.md). This is the same URL that was given to [setManagedFile](kautosavefile.md#setManagedFile)() or the [KAutoSaveFile](kautosavefile.md) constructor.

This is the name of the real file being edited by the application. To get the name of the temporary file where data can be saved, use [fileName](https://doc.qt.io/qt-6/qfile.html#fileName)() (after you have called [open](kautosavefile.md#open)()).

*See also* [setManagedFile](kautosavefile.md#setManagedFile)()

### \[override virtual\] bool KAutoSaveFile::open(QIODeviceBase::OpenMode *openmode*) {#open}

Reimplements: [QFile::open(QIODeviceBase::OpenMode mode)](https://doc.qt.io/qt-6/qfile.html#open).

Opens the autosave file and locks it if it wasn't already locked. The name of the temporary file where data can be saved to will be set by this function and can be retrieved with [fileName](https://doc.qt.io/qt-6/qfile.html#fileName)(). It will not change unless [releaseLock](kautosavefile.md#releaseLock)() is called. No other application will attempt to edit such a file either while the lock is held.

`openmode` the mode that should be used to open the file, probably QIODevice::ReadWrite

Returns `true` if the file could be opened (= locked and created), false if the operation failed

### \[virtual\] void KAutoSaveFile::releaseLock() {#releaseLock}

Closes the autosave file resource and removes the lock file. The file name returned by [fileName](https://doc.qt.io/qt-6/qfile.html#fileName)() will no longer be protected and can be overwritten by another application at any time. To obtain a new lock, call [open](kautosavefile.md#open)() again.

This function calls [remove](https://doc.qt.io/qt-6/qfile.html#remove)(), so the autosave temporary file will be removed too.

### void KAutoSaveFile::setManagedFile(const QUrl &*filename*) {#setManagedFile}

Sets the URL of the file managed by [KAutoSaveFile](kautosavefile.md). This should be the name of the real file being edited by the application. If the file was previously set, this function calls [releaseLock](kautosavefile.md#releaseLock)().

`filename` the filename that this [KAutoSaveFile](kautosavefile.md) refers to

*See also* [managedFile](kautosavefile.md#managedFile)()

### \[static\] QList\<KAutoSaveFile \*\> KAutoSaveFile::staleFiles(const QUrl &*url*, const QString &*applicationName* = QString()) {#staleFiles}

Checks for stale autosave files for the file `url`. Returns a list of autosave files that contain autosaved data left behind by other instances of the application, due to crashing or otherwise uncleanly exiting.

It is the application's job to determine what to do with such unsaved data. Generally, this is done by asking the user if he wants to see the recovered data, and then allowing the user to save if he wants to.

If not given, the application name is obtained from [QCoreApplication](https://doc.qt.io/qt-6/qcoreapplication.html), so be sure to have set it correctly before calling this function.

This function returns a list of unopened [KAutoSaveFile](kautosavefile.md) objects. By calling [open](kautosavefile.md#open)() on them, the application will steal the lock. Subsequent [releaseLock](kautosavefile.md#releaseLock)() or deleting of the object will then erase the stale autosave file.

The application owns all returned [KAutoSaveFile](kautosavefile.md) objects and is responsible for deleting them when no longer needed. Remember that deleting the [KAutoSaveFile](kautosavefile.md) will release the file lock and remove the stale autosave file.
