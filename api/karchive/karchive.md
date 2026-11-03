---
title: "KArchive Class"
description: "Generic class for reading/writing archives."
---

# KArchive Class

Generic class for reading/writing archives. [More...](#details)

- **Header:** `#include <KArchive>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS Archive)`  
  `target_link_libraries(mytarget PRIVATE KF6::Archive)`
- **Inherited By:** [K7Zip](k7zip.md), [KAr](kar.md), [KRcc](krcc.md), [KTar](ktar.md), and [KZip](kzip.md)

[List of all members, including inherited members](karchive-members.md)

## Public Functions

- [bool addLocalDirectory(const QString &path, const QString &destName)](#addLocalDirectory)
- [bool addLocalFile(const QString &fileName, const QString &destName)](#addLocalFile)
- [bool close()](#close)
- [QIODevice \*device() const](#device)
- [const KArchiveDirectory \*directory() const](#directory)
- [QString errorString() const](#errorString)
- [QString fileName() const](#fileName)
- [bool finishWriting(qint64 size)](#finishWriting)
- [bool isOpen() const](#isOpen)
- [QIODevice::OpenMode mode() const](#mode)
- [bool open(QIODevice::OpenMode mode)](#open)
- [bool prepareWriting(const QString &name, const QString &user, const QString &group, qint64 size, mode\_t perm = 0100644, const QDateTime &atime = QDateTime(), const QDateTime &mtime = QDateTime(), const QDateTime &ctime = QDateTime())](#prepareWriting)
- [bool writeData(QByteArrayView data)](#writeData) (since 6.0)
- [bool writeData(const char \*data, qint64 size)](#writeData-1)
- [bool writeDir(const QString &name, const QString &user = QString(), const QString &group = QString(), mode\_t perm = 040755, const QDateTime &atime = QDateTime(), const QDateTime &mtime = QDateTime(), const QDateTime &ctime = QDateTime())](#writeDir)
- [bool writeFile(const QString &name, QByteArrayView data, mode\_t perm = 0100644, const QString &user = QString(), const QString &group = QString(), const QDateTime &atime = QDateTime(), const QDateTime &mtime = QDateTime(), const QDateTime &ctime = QDateTime())](#writeFile) (since 6.0)
- [bool writeSymLink(const QString &name, const QString &target, const QString &user = QString(), const QString &group = QString(), mode\_t perm = 0120755, const QDateTime &atime = QDateTime(), const QDateTime &mtime = QDateTime(), const QDateTime &ctime = QDateTime())](#writeSymLink)

## Protected Functions

- [KArchive(QIODevice \*dev)](#KArchive)
- [KArchive(const QString &fileName)](#KArchive-1)
- [bool closeArchive()](#closeArchive)
- [bool createDevice(QIODevice::OpenMode mode)](#createDevice)
- [bool doFinishWriting(qint64 size)](#doFinishWriting)
- [bool doPrepareWriting(const QString &name, const QString &user, const QString &group, qint64 size, mode\_t perm, const QDateTime &atime, const QDateTime &mtime, const QDateTime &ctime)](#doPrepareWriting)
- [bool doWriteData(const char \*data, qint64 size)](#doWriteData) (since 6.0)
- [bool doWriteDir(const QString &name, const QString &user, const QString &group, mode\_t perm, const QDateTime &atime, const QDateTime &mtime, const QDateTime &ctime)](#doWriteDir)
- [bool doWriteSymLink(const QString &name, const QString &target, const QString &user, const QString &group, mode\_t perm, const QDateTime &atime, const QDateTime &mtime, const QDateTime &ctime)](#doWriteSymLink)
- [KArchiveDirectory \*findOrCreate(const QString &path)](#findOrCreate)
- [bool openArchive(QIODevice::OpenMode mode)](#openArchive)
- [KArchiveDirectory \*rootDir()](#rootDir)
- [void setDevice(QIODevice \*dev)](#setDevice)
- [void setErrorString(const QString &errorStr)](#setErrorString)
- [void setRootDir(KArchiveDirectory \*rootDir)](#setRootDir)

## Detailed Description {#details}

## Member Function Documentation {#member-function-documentation}

### \[explicit protected\] KArchive::KArchive(QIODevice \**dev*) {#KArchive}

Base constructor (protected since this is a pure virtual class).

`dev` the I/O device where the archive reads its data

Note that this can be a file, but also a data buffer, a compression filter, etc. For a file in writing mode it is better to use the other constructor though, to benefit from the use of [QSaveFile](https://doc.qt.io/qt-6/qsavefile.html) when saving.

### \[explicit protected\] KArchive::KArchive(const QString &*fileName*) {#KArchive-1}

Base constructor (protected since this is a pure virtual class).

`fileName` is a local path (e.g. "/tmp/myfile.ext"), from which the archive will be read from, or into which the archive will be written, depending on the mode given to [open](karchive.md#open)().

### bool KArchive::addLocalDirectory(const QString &*path*, const QString &*destName*) {#addLocalDirectory}

Writes a local directory into the archive, including all its contents, recursively. Calls [addLocalFile](karchive.md#addLocalFile) for each file to be added.

It will also add a `path` that is a symbolic link to a directory. The symbolic link will be dereferenced and the content of the directory it is pointing to added recursively. However, symbolic links \*under\* `path` will be stored as is.

`path` full path to an existing local directory, to be added to the archive.

`destName` the resulting name (or relative path) of the file in the archive.

### bool KArchive::addLocalFile(const QString &*fileName*, const QString &*destName*) {#addLocalFile}

Writes a local file into the archive. The main difference with [writeFile](karchive.md#writeFile), is that this method minimizes memory usage, by not loading the whole file into memory in one go.

If `fileName` is a symbolic link, it will be written as is, i.e. it will not be resolved before.

`fileName` full path to an existing local file, to be added to the archive.

`destName` the resulting name (or relative path) of the file in the archive.

### \[virtual\] bool KArchive::close() {#close}

Closes the archive.

Inherited classes might want to reimplement [closeArchive](karchive.md#closeArchive) instead.

Returns true if close succeeded without problems

*See also* [open](karchive.md#open)

### \[pure virtual protected\] bool KArchive::closeArchive() {#closeArchive}

Closes the archive.

Called by close.

### \[virtual protected\] bool KArchive::createDevice(QIODevice::OpenMode *mode*) {#createDevice}

Can be reimplemented in order to change the creation of the device (when using the [fileName](karchive.md#fileName) constructor). By default this method uses [QSaveFile](https://doc.qt.io/qt-6/qsavefile.html) when saving, and a simple [QFile](https://doc.qt.io/qt-6/qfile.html) on reading.

This method is called by [open](karchive.md#open)().

### QIODevice \*KArchive::device() const {#device}

Returns the underlying device.

*See also* [setDevice](karchive.md#setDevice)()

### const KArchiveDirectory \*KArchive::directory() const {#directory}

If an archive is opened for reading, then the contents of the archive can be accessed via this function. Returns the directory of the archive

### \[pure virtual protected\] bool KArchive::doFinishWriting(qint64 *size*) {#doFinishWriting}

Called after writing the data.

This virtual method must be implemented by subclasses.

`size` the size of the file

*See also* [finishWriting](karchive.md#finishWriting)()

### \[pure virtual protected\] bool KArchive::doPrepareWriting(const QString &*name*, const QString &*user*, const QString &*group*, qint64 *size*, mode\_t *perm*, const QDateTime &*atime*, const QDateTime &*mtime*, const QDateTime &*ctime*) {#doPrepareWriting}

This virtual method must be implemented by subclasses.

Depending on the archive type not all metadata might be used.

`name` the name of the file

`user` the user that owns the file

`group` the group that owns the file

`size` the size of the file

`perm` permissions of the file. Use 0100644 if you don't have any more specific permissions to set.

`atime` time the file was last accessed

`mtime` modification time of the file

`ctime` time of last status change

*See also* [prepareWriting](karchive.md#prepareWriting)

### \[virtual protected, since 6.0\] bool KArchive::doWriteData(const char \**data*, qint64 *size*) {#doWriteData}

Write data into the current file. Called by [writeData](karchive.md#writeData).

`data` a pointer to the data

`size` the size of the chunk

Returns `true` if successful, `false` otherwise

This function was introduced in Qt 6.0.

*See also* [writeData](karchive.md#writeData)

### \[pure virtual protected\] bool KArchive::doWriteDir(const QString &*name*, const QString &*user*, const QString &*group*, mode\_t *perm*, const QDateTime &*atime*, const QDateTime &*mtime*, const QDateTime &*ctime*) {#doWriteDir}

Write a directory to the archive. This virtual method must be implemented by subclasses.

Depending on the archive type not all metadata might be used.

`name` the name of the directory

`user` the user that owns the directory

`group` the group that owns the directory

`perm` permissions of the directory. Use 040755 if you don't have any other information.

`atime` time the file was last accessed

`mtime` modification time of the file

`ctime` time of last status change

*See also* [writeDir](karchive.md#writeDir)

### \[pure virtual protected\] bool KArchive::doWriteSymLink(const QString &*name*, const QString &*target*, const QString &*user*, const QString &*group*, mode\_t *perm*, const QDateTime &*atime*, const QDateTime &*mtime*, const QDateTime &*ctime*) {#doWriteSymLink}

Writes a symbolic link to the archive. This virtual method must be implemented by subclasses.

`name` name of symbolic link

`target` target of symbolic link

`user` the user that owns the directory

`group` the group that owns the directory

`perm` permissions of the directory

`atime` time the file was last accessed

`mtime` modification time of the file

`ctime` time of last status change

*See also* [writeSymLink](karchive.md#writeSymLink)

### QString KArchive::errorString() const {#errorString}

Returns a description of the last error

*See also* [setErrorString](karchive.md#setErrorString)()

### QString KArchive::fileName() const {#fileName}

The name of the archive file, as passed to the constructor that takes a fileName, or an empty string if you used the [QIODevice](https://doc.qt.io/qt-6/qiodevice.html) constructor.

Returns the name of the file, or QString() if unknown

### \[protected\] KArchiveDirectory \*KArchive::findOrCreate(const QString &*path*) {#findOrCreate}

Ensures that `path` exists, create otherwise.

This handles e.g. tar files missing directory entries, like mico-2.3.0.tar.gz :)

`path` the path of the directory

Returns the directory with the given `path`

### bool KArchive::finishWriting(qint64 *size*) {#finishWriting}

Call finishWriting after writing the data.

`size` the size of the file

*See also* [prepareWriting](karchive.md#prepareWriting)()

### bool KArchive::isOpen() const {#isOpen}

Checks whether the archive is open.

Returns true if the archive is opened

### QIODevice::OpenMode KArchive::mode() const {#mode}

Returns the mode in which the archive was opened (QIODevice::ReadOnly or QIODevice::WriteOnly)

*See also* [open](karchive.md#open)()

### \[virtual\] bool KArchive::open(QIODevice::OpenMode *mode*) {#open}

Opens the archive for reading or writing.

Inherited classes might want to reimplement [openArchive](karchive.md#openArchive) instead.

`mode` may be QIODevice::ReadOnly or QIODevice::WriteOnly

*See also* [close](karchive.md#close)

### \[pure virtual protected\] bool KArchive::openArchive(QIODevice::OpenMode *mode*) {#openArchive}

Opens an archive for reading or writing.

Called by open.

`mode` may be QIODevice::ReadOnly or QIODevice::WriteOnly

### bool KArchive::prepareWriting(const QString &*name*, const QString &*user*, const QString &*group*, qint64 *size*, mode\_t *perm* = 0100644, const QDateTime &*atime* = QDateTime(), const QDateTime &*mtime* = QDateTime(), const QDateTime &*ctime* = QDateTime()) {#prepareWriting}

Here's another way of writing a file into an archive: Call prepareWriting(), then call [writeData](karchive.md#writeData)() as many times as wanted then call [finishWriting](karchive.md#finishWriting)( totalSize ). For tar.gz files, you need to know the size before hand, it is needed in the header! For zip files, size isn't used.

This method also allows some file metadata to be set. However, depending on the archive type not all metadata might be regarded.

`name` the name of the file

`user` the user that owns the file

`group` the group that owns the file

`size` the size of the file

`perm` permissions of the file

`atime` time the file was last accessed

`mtime` modification time of the file

`ctime` time of last status change

### \[virtual protected\] KArchiveDirectory \*KArchive::rootDir() {#rootDir}

Retrieves or create the root directory.

The default implementation assumes that [openArchive](karchive.md#openArchive)() did the parsing, so it creates a dummy rootdir if none was set (write mode, or no '/' in the archive).

Reimplement this to provide parsing/listing on demand.

Returns the root directory

*See also* [setRootDir](karchive.md#setRootDir)()

### \[protected\] void KArchive::setDevice(QIODevice \**dev*) {#setDevice}

Can be called by derived classes in order to set the underlying device.

Note that [KArchive](karchive.md) will -not- own the device, it must be deleted by the derived class.

*See also* [device](karchive.md#device)()

### \[protected\] void KArchive::setErrorString(const QString &*errorStr*) {#setErrorString}

Sets error description

`errorStr` error description

*See also* [errorString](karchive.md#errorString)()

### \[protected\] void KArchive::setRootDir(KArchiveDirectory \**rootDir*) {#setRootDir}

Derived classes call setRootDir from [openArchive](karchive.md#openArchive), to set the root directory after parsing an existing archive.

*See also* [rootDir](karchive.md#rootDir)()

### \[since 6.0\] bool KArchive::writeData(QByteArrayView *data*) {#writeData}

Overload for writeData(const char \*, qint64);

This function was introduced in Qt 6.0.

### bool KArchive::writeData(const char \**data*, qint64 *size*) {#writeData-1}

Write data into the current file - to be called after calling [prepareWriting](karchive.md#prepareWriting)

`data` a pointer to the data

`size` the size of the chunk

Returns `true` if successful, `false` otherwise

### bool KArchive::writeDir(const QString &*name*, const QString &*user* = QString(), const QString &*group* = QString(), mode\_t *perm* = 040755, const QDateTime &*atime* = QDateTime(), const QDateTime &*mtime* = QDateTime(), const QDateTime &*ctime* = QDateTime()) {#writeDir}

If an archive is opened for writing then you can add new directories using this function. [KArchive](karchive.md) won't write one directory twice.

This method also allows some file metadata to be set. However, depending on the archive type not all metadata might be regarded.

`name` the name of the directory

`user` the user that owns the directory

`group` the group that owns the directory

`perm` permissions of the directory

`atime` time the file was last accessed

`mtime` modification time of the file

`ctime` time of last status change

### \[since 6.0\] bool KArchive::writeFile(const QString &*name*, QByteArrayView *data*, mode\_t *perm* = 0100644, const QString &*user* = QString(), const QString &*group* = QString(), const QDateTime &*atime* = QDateTime(), const QDateTime &*mtime* = QDateTime(), const QDateTime &*ctime* = QDateTime()) {#writeFile}

Writes a new file into the archive.

The archive must be opened for writing first.

The necessary parent directories are created automatically if needed. For instance, writing "mydir/test1" does not require creating the directory "mydir" first.

This method also allows some file metadata to be set. However, depending on the archive type not all metadata might be written out.

`name` the name of the file

`data` the data to write

`perm` permissions of the file

`user` the user that owns the file

`group` the group that owns the file

`atime` time the file was last accessed

`mtime` modification time of the file

`ctime` time of last status change

This function was introduced in Qt 6.0.

### bool KArchive::writeSymLink(const QString &*name*, const QString &*target*, const QString &*user* = QString(), const QString &*group* = QString(), mode\_t *perm* = 0120755, const QDateTime &*atime* = QDateTime(), const QDateTime &*mtime* = QDateTime(), const QDateTime &*ctime* = QDateTime()) {#writeSymLink}

Writes a symbolic link to the archive if supported. The archive must be opened for writing.

`name` name of symbolic link

`target` target of symbolic link

`user` the user that owns the directory

`group` the group that owns the directory

`perm` permissions of the directory

`atime` time the file was last accessed

`mtime` modification time of the file

`ctime` time of last status change
