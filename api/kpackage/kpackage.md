---
title: "KPackage Namespace"
description: "Installation and loading of additional content (ex: scripts, images...) as packages.."
---

# KPackage Namespace

Installation and loading of additional content (ex: scripts, images...) as packages.. [More...](#details)

- Header: KPackage
- CMake: find\_package(KF6 REQUIRED COMPONENTS Package) target\_link\_libraries(mytarget PRIVATE KF6::Package)

## Detailed Description {#details}

## Classes {#classes}

### class [Package](kpackage-package.md)

Object representing an installed package.

### class [PackageJob](kpackage-packagejob.md)

KJob subclass that allows async install/update/uninstall operations for packages.

### class [PackageLoader](kpackage-packageloader.md)

### class [PackageStructure](kpackage-packagestructure.md)

This class is used to define the filesystem structure of a package type.
