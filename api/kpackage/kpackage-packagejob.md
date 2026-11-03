---
title: "KPackage::PackageJob Class"
description: "KJob subclass that allows async install/update/uninstall operations for packages."
---

# KPackage::PackageJob Class

KJob subclass that allows async install/update/uninstall operations for packages. [More...](#details)

- **Header:** `#include <KPackage/PackageJob>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS Package)`  
  `target_link_libraries(mytarget PRIVATE KF6::Package)`

[List of all members, including inherited members](kpackage-packagejob-members.md)

## Public Types

- [enum PackageJob::JobError](#JobError-enum)

## Public Functions

- [KPackage::Package package() const](#package)

## Static Public Members

- [KPackage::PackageJob \*install(const QString &packageFormat, const QString &sourcePackage, const QString &packageRoot = QString())](#install)
- [KPackage::PackageJob \*uninstall(const QString &packageFormat, const QString &pluginId, const QString &packageRoot = QString())](#uninstall)
- [KPackage::PackageJob \*update(const QString &packageFormat, const QString &sourcePackage, const QString &packageRoot = QString())](#update)

## Detailed Description {#details}

## Member Type Documentation {#member-type-documentation}

### enum PackageJob::JobError {#JobError-enum}

Error codes for the install/update/remove jobs

| Constant | Value | Description |
| --- | --- | --- |
| `KPackage::PackageJob::InvalidPackageStructure` | `KJob::UserDefinedError + 1` | Could not find/load the given package structure |
| `KPackage::PackageJob::RootCreationError` | `102` | Cannot create package root directory |
| `KPackage::PackageJob::PackageFileNotFoundError` | `103` | The package file does not exist |
| `KPackage::PackageJob::UnsupportedArchiveFormatError` | `104` | The archive format of the package is not supported |
| `KPackage::PackageJob::PackageOpenError` | `105` | Can't open the package file for reading |
| `KPackage::PackageJob::PluginIdInvalidError` | `106` | The plugin id is not specified in the metadata.json file or contains characters different from letters, digits, dots and underscores |
| `KPackage::PackageJob::UpdatePackageTypeMismatchError` | `107` | A package with this plugin id was already installed, but has a different type in the metadata.json file |
| `KPackage::PackageJob::OldVersionRemovalError` | `108` | Failed to remove the old version of the package during an upgrade |
| `KPackage::PackageJob::NewerVersionAlreadyInstalledError` | `109` | We tried to update, but the same version or a newer one is already installed |
| `KPackage::PackageJob::PackageAlreadyInstalledError` | `110` | The package is already installed and a normal install (not update) was performed |
| `KPackage::PackageJob::PackageMoveError` | `111` | Failure to move a package from the system temporary folder to its final destination |
| `KPackage::PackageJob::PackageCopyError` | `112` | Failure to copy a package folder from somewhere in the filesystem to its final destination |
| `KPackage::PackageJob::PackageUninstallError` | `113` | Failure to uninstall a package |

## Member Function Documentation {#member-function-documentation}

### \[static\] KPackage::PackageJob \*PackageJob::install(const QString &*packageFormat*, const QString &*sourcePackage*, const QString &*packageRoot* = QString()) {#install}

Installs the given package. The returned job is already started

### KPackage::Package PackageJob::package() const {#package}

### \[static\] KPackage::PackageJob \*PackageJob::uninstall(const QString &*packageFormat*, const QString &*pluginId*, const QString &*packageRoot* = QString()) {#uninstall}

Installs the given package. The returned job is already started

### \[static\] KPackage::PackageJob \*PackageJob::update(const QString &*packageFormat*, const QString &*sourcePackage*, const QString &*packageRoot* = QString()) {#update}

Installs the given package. The returned job is already started
