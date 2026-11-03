---
title: "KPackage::PackageStructure Class"
description: "This class is used to define the filesystem structure of a package type."
---

# KPackage::PackageStructure Class

This class is used to define the filesystem structure of a package type. [More...](#details)

- **Header:** `#include <Package/PackageStructure>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS Package)`  
  `target_link_libraries(mytarget PRIVATE KF6::Package)`
- **Inherits:** [QObject](https://doc.qt.io/qt-6/qobject.html)

[List of all members, including inherited members](kpackage-packagestructure-members.md)

## Public Functions

- [PackageStructure(QObject \*parent = nullptr, const QVariantList &args = QVariantList())](#PackageStructure)
- [void initPackage(KPackage::Package \*package)](#initPackage)
- [void pathChanged(KPackage::Package \*package)](#pathChanged)

## Detailed Description {#details}

A [PackageStructure](kpackage-packagestructure.md) is implemented as a dynamically loaded plugin, in the reimplementation of [initPackage](kpackage-packagestructure.md#initPackage) the allowed fines and directories in the package are set into the package, for instance:

```cpp
package->addFileDefinition("mainscript", QStringLiteral("ui/main.qml"));
package->setDefaultPackageRoot(QStringLiteral("plasma/wallpapers/"));
package->addDirectoryDefinition("images", QStringLiteral("images"));
package->addDirectoryDefinition("theme", QStringLiteral("theme"));
QStringList mimetypes{QStringLiteral("image/svg+xml"), QStringLiteral("image/png"), QStringLiteral("image/jpeg")};
package->setMimeTypes("images", mimetypes);
```

## Member Function Documentation {#member-function-documentation}

### \[explicit\] PackageStructure::PackageStructure(QObject \**parent* = nullptr, const QVariantList &*args* = QVariantList()) {#PackageStructure}

### \[virtual\] void PackageStructure::initPackage(KPackage::Package \**package*) {#initPackage}

Called when a the [PackageStructure](kpackage-packagestructure.md) should initialize a Package with the initial structure. This allows setting paths before setPath is called.

> **Note:** one special value is "metadata" which can be set to the location of KPluginMetaData compatible .json file within the package. If not defined, it is assumed that this file exists under the top level directory of the package.

`package` the Package to set up. The object is empty of all definition when first passed in.

### \[virtual\] void PackageStructure::pathChanged(KPackage::Package \**package*) {#pathChanged}

Called whenever the path changes so that subclasses may take package specific actions.
