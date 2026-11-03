---
title: "KPackage::PackageLoader Class"
description: "Installation and loading of additional content (ex: scripts, images...) as packages.."
---

# KPackage::PackageLoader Class

Installation and loading of additional content (ex: scripts, images...) as packages.. [More...](#details)

- **Header:** `#include <KPackage/PackageLoader>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS Package)`  
  `target_link_libraries(mytarget PRIVATE KF6::Package)`

[List of all members, including inherited members](kpackage-packageloader-members.md)

## Public Functions

- [void addKnownPackageStructure(const QString &packageFormat, KPackage::PackageStructure \*structure)](#addKnownPackageStructure)
- [QList\<KPluginMetaData\> findPackages(const QString &packageFormat, const QString &packageRoot = QString(), std::function\<bool (const KPluginMetaData &)\> filter = std::function\<bool(const KPluginMetaData &)\>())](#findPackages)
- [QList\<KPackage::Package\> listKPackages(const QString &packageFormat, const QString &packageRoot = QString())](#listKPackages) (since 6.0)
- [QList\<KPluginMetaData\> listPackages(const QString &packageFormat, const QString &packageRoot = QString())](#listPackages)
- [QList\<KPluginMetaData\> listPackagesMetadata(const QString &packageFormat, const QString &packageRoot = QString())](#listPackagesMetadata) (since 6.0)
- [KPackage::Package loadPackage(const QString &packageFormat, const QString &packagePath = QString())](#loadPackage)
- [KPackage::PackageStructure \*loadPackageStructure(const QString &packageFormat)](#loadPackageStructure)

## Static Public Members

- [KPackage::PackageLoader \*self()](#self)

## Detailed Description {#details}

This is an abstract base class which defines an interface to which the package loading logic can communicate with a parent application. The plugin loader must be set before any plugins are loaded, otherwise (for safety reasons), the default [PackageLoader](kpackage-packageloader.md) implementation will be used. The reimplemented version should not do more than simply returning a loaded plugin. It should not init() it, and it should not hang on to it.

## Member Function Documentation {#member-function-documentation}

### void PackageLoader::addKnownPackageStructure(const QString &*packageFormat*, KPackage::PackageStructure \**structure*) {#addKnownPackageStructure}

Adds a new known package structure that can be used by the functions to load packages such as [loadPackage](kpackage-packageloader.md#loadPackage), [findPackages](kpackage-packageloader.md#findPackages) etc

`packageFormat` the package format, such as "[KPackage](kpackage.md)/GenericQML"

`structure` the package structure we want to be able to load packages from

### QList\<KPluginMetaData\> PackageLoader::findPackages(const QString &*packageFormat*, const QString &*packageRoot* = QString(), std::function\<bool (const KPluginMetaData &)\> *filter* = std::function\<bool(const KPluginMetaData &)\>()) {#findPackages}

List package of a certain type that match a certain filter function

`packageFormat` the format of the packages to list

`packageRoot` the root folder where the packages are installed. If not specified the default from the packageformat will be taken.

`filter` a filter function that will be called on each package: will return true for the matching ones

Returns metadata for all the matching packages

### \[since 6.0\] QList\<KPackage::Package\> PackageLoader::listKPackages(const QString &*packageFormat*, const QString &*packageRoot* = QString()) {#listKPackages}

List all available packages of a certain type. This should be used in case the package structure modifies the metadata or you need to access the contained files of the package.

`packageFormat` the format of the packages to list

`packageRoot` the root folder where the packages are installed. If not specified the default from the packageformat will be taken.

This function was introduced in Qt 6.0.

### QList\<KPluginMetaData\> PackageLoader::listPackages(const QString &*packageFormat*, const QString &*packageRoot* = QString()) {#listPackages}

List all available packages of a certain type

`packageFormat` the format of the packages to list

`packageRoot` the root folder where the packages are installed. If not specified the default from the packageformat will be taken.

Returns metadata for all the matching packages

### \[since 6.0\] QList\<KPluginMetaData\> PackageLoader::listPackagesMetadata(const QString &*packageFormat*, const QString &*packageRoot* = QString()) {#listPackagesMetadata}

This function was introduced in Qt 6.0.

*See also* [listPackages](kpackage-packageloader.md#listPackages)()

### KPackage::Package PackageLoader::loadPackage(const QString &*packageFormat*, const QString &*packagePath* = QString()) {#loadPackage}

Load a Package plugin.

`packageFormat` the format of the package to load

`packagePath` the package name: the path of the package relative to the packageFormat root path. If not specified it will have to be set manually with [Package::setPath](kpackage-package.md#setPath)() by the caller.

Returns a Package object matching name, or an invalid package on failure

### KPackage::PackageStructure \*PackageLoader::loadPackageStructure(const QString &*packageFormat*) {#loadPackageStructure}

Loads a [PackageStructure](kpackage-packagestructure.md) for a given format. The structure can then be used as paramenter for a Package instance constructor

> **Note:** The returned pointer is managed by [KPackage](kpackage.md), and should never be deleted

`packageFormat` the package format, such as "[KPackage](kpackage.md)/GenericQML"

Returns the structure instance (ownership retained by [KPackage](kpackage.md))

### \[static\] KPackage::PackageLoader \*PackageLoader::self() {#self}

Return the active plugin loader
