---
title: "KPackage::Package Class"
description: "Object representing an installed package."
---

# KPackage::Package Class

Object representing an installed package. [More...](#details)

- **Header:** `#include <KPackage/Package>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS Package)`  
  `target_link_libraries(mytarget PRIVATE KF6::Package)`

[List of all members, including inherited members](kpackage-package-members.md)

## Public Functions

- [Package(KPackage::PackageStructure \*structure = nullptr)](#Package)
- [void addDirectoryDefinition(const QByteArray &key, const QString &path)](#addDirectoryDefinition)
- [void addFileDefinition(const QByteArray &key, const QString &path)](#addFileDefinition)
- [bool allowExternalPaths() const](#allowExternalPaths)
- [QStringList contentsPrefixPaths() const](#contentsPrefixPaths)
- [QByteArray cryptographicHash(QCryptographicHash::Algorithm algorithm) const](#cryptographicHash)
- [QString defaultPackageRoot() const](#defaultPackageRoot)
- [QList\<QByteArray\> directories() const](#directories)
- [QStringList entryList(const QByteArray &key) const](#entryList)
- [KPackage::Package fallbackPackage() const](#fallbackPackage)
- [QString filePath(const QByteArray &key, const QString &filename = QString()) const](#filePath)
- [QUrl fileUrl(const QByteArray &key, const QString &filename = QString()) const](#fileUrl)
- [QList\<QByteArray\> files() const](#files)
- [bool hasValidStructure() const](#hasValidStructure)
- [bool isRequired(const QByteArray &key) const](#isRequired)
- [bool isValid() const](#isValid)
- [KPluginMetaData metadata() const](#metadata)
- [QStringList mimeTypes(const QByteArray &key) const](#mimeTypes)
- [const QString path() const](#path)
- [void removeDefinition(const QByteArray &key)](#removeDefinition)
- [QList\<QByteArray\> requiredDirectories() const](#requiredDirectories)
- [QList\<QByteArray\> requiredFiles() const](#requiredFiles)
- [void setAllowExternalPaths(bool allow)](#setAllowExternalPaths)
- [void setContentsPrefixPaths(const QStringList &prefixPaths)](#setContentsPrefixPaths)
- [void setDefaultMimeTypes(const QStringList &mimeTypes)](#setDefaultMimeTypes)
- [void setDefaultPackageRoot(const QString &packageRoot)](#setDefaultPackageRoot)
- [void setFallbackPackage(const KPackage::Package &package)](#setFallbackPackage)
- [void setMetadata(const KPluginMetaData &data)](#setMetadata)
- [void setMimeTypes(const QByteArray &key, const QStringList &mimeTypes)](#setMimeTypes)
- [void setPath(const QString &path)](#setPath)
- [void setRequired(const QByteArray &key, bool required)](#setRequired)

## Detailed Description {#details}

Package defines what is in a package and provides easy access to the contents.

To define a package, one might write the following code:

```cpp
Package package;

package.addDirectoryDefinition("images", "pics/");
package.setMimeTypes("images", QStringList{"image/svg", "image/png", "image/jpeg"});

package.addDirectoryDefinition("scripts", "code/");
package.setMimeTypes("scripts", QStringList{"text/\*"});

package.addFileDefinition("mainscript", "code/main.js");
package.setRequired("mainscript", true);
```

One may also choose to create a subclass of [PackageStructure](kpackage-packagestructure.md) and include the setup in the constructor.

Either way, Package creates a self-documenting contract between the packager and the application without exposing package internals such as actual on-disk structure of the package or requiring that all contents be explicitly known ahead of time.

Subclassing [PackageStructure](kpackage-packagestructure.md) does have provide a number of potential const benefits:

- the package can be notified of path changes via the virtual pathChanged() method
- the subclass may implement mechanisms to install and remove packages using the virtual install and uninstall methods
- subclasses can be compiled as plugins for easy re-use

## Member Function Documentation {#member-function-documentation}

### \[explicit\] Package::Package(KPackage::PackageStructure \**structure* = nullptr) {#Package}

Default constructor

`structure` if a null pointer is passed in, this will creates an empty (invalid) Package; otherwise the structure is allowed to set up the Package's initial layout

### void Package::addDirectoryDefinition(const QByteArray &*key*, const QString &*path*) {#addDirectoryDefinition}

Adds a directory to the structure of the package. It is added as a not-required element with no associated [mimeTypes](kpackage-package.md#mimeTypes). If an entry with the given key already exists, the path is added to it as a search alternative.

`key` used as an internal label for this directory

`path` the path within the package for this directory

### void Package::addFileDefinition(const QByteArray &*key*, const QString &*path*) {#addFileDefinition}

Adds a file to the structure of the package. It is added as a not-required element with no associated [mimeTypes](kpackage-package.md#mimeTypes). If an entry with the given key already exists, the path is added to it as a search alternative.

`key` used as an internal label for this file

`path` the path within the package for this file

### bool Package::allowExternalPaths() const {#allowExternalPaths}

Returns true if paths/symlinks outside the package itself should be followed. By default this is set to false for security reasons.

*See also* [setAllowExternalPaths](kpackage-package.md#setAllowExternalPaths)()

### QStringList Package::contentsPrefixPaths() const {#contentsPrefixPaths}

Returns the prefix paths inserted between the base path and content entries, in order of priority. When searching for a file, all paths will be tried in order.

*See also* [setContentsPrefixPaths](kpackage-package.md#setContentsPrefixPaths)()

### QByteArray Package::cryptographicHash(QCryptographicHash::Algorithm *algorithm*) const {#cryptographicHash}

Returns a hash digest of the contents of the package in hexadecimal form

### QString Package::defaultPackageRoot() const {#defaultPackageRoot}

Returns preferred package root. This defaults to kpackage/generic/

*See also* [setDefaultPackageRoot](kpackage-package.md#setDefaultPackageRoot)()

### QList\<QByteArray\> Package::directories() const {#directories}

Returns all directories registered as part of this Package's structure

### QStringList Package::entryList(const QByteArray &*key*) const {#entryList}

Get the list of files of a given type.

`fileType` the type of file to look for, as defined in the package structure. Returns list of files by name, suitable for passing to [filePath](kpackage-package.md#filePath)

### KPackage::Package Package::fallbackPackage() const {#fallbackPackage}

Returns The fallback package root path

*See also* [setFallbackPackage](kpackage-package.md#setFallbackPackage)()

### QString Package::filePath(const QByteArray &*key*, const QString &*filename* = QString()) const {#filePath}

Get the path to a given file based on the key and an optional filename. Example: finding the main script in a scripting package: filePath("mainscript")

Example: finding a specific image in the images directory: filePath("images", "myimage.png")

`key` the key of the file type to look for,

`filename` optional name of the file to locate within the package

Returns path to the file on disk. QString() if not found.

### QUrl Package::fileUrl(const QByteArray &*key*, const QString &*filename* = QString()) const {#fileUrl}

Get the url to a given file based on the key and an optional filename, is the file:// or qrc:// format Example: finding the main script in a scripting package: [filePath](kpackage-package.md#filePath)("mainscript")

Example: finding a specific image in the images directory: [filePath](kpackage-package.md#filePath)("images", "myimage.png")

`key` the key of the file type to look for,

`filename` optional name of the file to locate within the package

Returns path to the file on disk. QUrl() if not found.

### QList\<QByteArray\> Package::files() const {#files}

Returns all files registered as part of this Package's structure

### bool Package::hasValidStructure() const {#hasValidStructure}

Returns `true` if this package has a valid [PackageStructure](kpackage-packagestructure.md) associated with it.

A package may not be valid, but have a valid structure. Useful when dealing with Package objects in a semi-initialized state (e.g. before calling [setPath](kpackage-package.md#setPath)())

### bool Package::isRequired(const QByteArray &*key*) const {#isRequired}

Returns true if the item at path exists and is required

### bool Package::isValid() const {#isValid}

Return `true` if all the required components exist

### KPluginMetaData Package::metadata() const {#metadata}

Returns the package metadata object.

*See also* [setMetadata](kpackage-package.md#setMetadata)()

### QStringList Package::mimeTypes(const QByteArray &*key*) const {#mimeTypes}

Returns the mimeTypes associated with the path, if any

*See also* [setMimeTypes](kpackage-package.md#setMimeTypes)()

### const QString Package::path() const {#path}

Returns the path to the root of this particular package

*See also* [setPath](kpackage-package.md#setPath)()

### void Package::removeDefinition(const QByteArray &*key*) {#removeDefinition}

Removes a definition from the structure of the package.

`key` the internal label of the file or directory to remove

### QList\<QByteArray\> Package::requiredDirectories() const {#requiredDirectories}

Returns all directories registered as part of this Package's required structure

### QList\<QByteArray\> Package::requiredFiles() const {#requiredFiles}

Returns all files registered as part of this Package's required structure

### void Package::setAllowExternalPaths(bool *allow*) {#setAllowExternalPaths}

Sets whether or not external paths/symlinks can be followed by a package

`allow` true if paths/symlinks outside of the package should be followed, false if they should be rejected.

*See also* [allowExternalPaths](kpackage-package.md#allowExternalPaths)()

### void Package::setContentsPrefixPaths(const QStringList &*prefixPaths*) {#setContentsPrefixPaths}

Sets the prefixes that all the contents in this package should appear under. This defaults to "contents/" and is added automatically between the base path and the entries as defined by the package structure. Multiple entries can be added. In this case each file request will be searched in all prefixes in order, and the first found will be returned.

`prefix` paths the directory prefix to use

*See also* [contentsPrefixPaths](kpackage-package.md#contentsPrefixPaths)()

### void Package::setDefaultMimeTypes(const QStringList &*mimeTypes*) {#setDefaultMimeTypes}

Defines the default [mimeTypes](kpackage-package.md#mimeTypes) for any definitions that do not have associated [mimeTypes](kpackage-package.md#mimeTypes). Handy for packages with only one or predominantly one file type.

`mimeTypes` a list of [mimeTypes](kpackage-package.md#mimeTypes)

### void Package::setDefaultPackageRoot(const QString &*packageRoot*) {#setDefaultPackageRoot}

Sets preferred package root.

*See also* [defaultPackageRoot](kpackage-package.md#defaultPackageRoot)()

### void Package::setFallbackPackage(const KPackage::Package &*package*) {#setFallbackPackage}

Sets the fallback package root path If a file won't be found in this package, it will search it in the package with the same structure identified by path It is intended to be used by the packageStructure

`path` package root path

*See also* [fallbackPackage](kpackage-package.md#fallbackPackage)(), [setPath](kpackage-package.md#setPath)

### void Package::setMetadata(const KPluginMetaData &*data*) {#setMetadata}

Sets the metadata for the [KPackage](kpackage.md). This overwrites the current metadata. This should be used in case a kpackage gets loaded by name, based on the path a C++ plugin which has embedded metadata.

*See also* [metadata](kpackage-package.md#metadata)()

### void Package::setMimeTypes(const QByteArray &*key*, const QStringList &*mimeTypes*) {#setMimeTypes}

Define [mimeTypes](kpackage-package.md#mimeTypes) for a given part of the structure The path must already have been added using [addDirectoryDefinition](kpackage-package.md#addDirectoryDefinition) or [addFileDefinition](kpackage-package.md#addFileDefinition).

`key` the entry within the package

`mimeTypes` a list of [mimeTypes](kpackage-package.md#mimeTypes)

*See also* [mimeTypes](kpackage-package.md#mimeTypes)()

### void Package::setPath(const QString &*path*) {#setPath}

Sets the path to the root of this package

`path` an absolute path, or a relative path to the default package root

*See also* [path](kpackage-package.md#path)()

### void Package::setRequired(const QByteArray &*key*, bool *required*) {#setRequired}

Sets whether or not a given part of the structure is required or not. The path must already have been added using [addDirectoryDefinition](kpackage-package.md#addDirectoryDefinition) or [addFileDefinition](kpackage-package.md#addFileDefinition).

`key` the entry within the package

`required` true if this entry is required, false if not

*See also* [isRequired](kpackage-package.md#isRequired)()
