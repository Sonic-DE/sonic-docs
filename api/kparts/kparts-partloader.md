---
title: "KParts::PartLoader Namespace"
description: "Helper methods for locating and loading parts. This namespace was introduced in KParts 5.69."
---

# KParts::PartLoader Namespace

Helper methods for locating and loading parts. This namespace was introduced in KParts 5.69. [More...](#details)

- **Header:** `#include <KParts/PartLoader>`
- **Since:** KParts 5.69
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS Parts)`  
  `target_link_libraries(mytarget PRIVATE KF6::Parts)`

## Detailed Description {#details}

This is based upon [KPluginFactory](../kcoreaddons/kpluginfactory.md), but it takes care of querying by mimetype, sorting the available parts by builtin preference and by user preference.

## Function Documentation {#function-documentation}

### template \<typename T\> KPluginFactory::Result\<T\> PartLoader::instantiatePart(const KPluginMetaData &*data*, QWidget \**parentWidget* = nullptr, QObject \**parent* = nullptr, const QVariantList &*args* = {}) {#instantiatePart}

Attempts to create a KPart from the given metadata.

```cpp
if (auto result = KParts::PartLoader::instantiatePart<MyPart>(metaData, parentWidget, parent, args)) {
    // result.plugin is valid and can be accessed
} else {
    // result contains information about the error
}
```

`data` [KPluginMetaData](../kcoreaddons/kpluginmetadata.md) from which the plugin should be loaded

`parentWidget` The parent widget

`parent` The parent object

`args` A list of arguments to be passed to the part

Returns a Result object which contains the plugin instance and potentially error information

### template \<typename T\> KPluginFactory::Result\<T\> PartLoader::instantiatePartForMimeType(const QString &*mimeType*, QWidget \**parentWidget* = nullptr, QObject \**parent* = nullptr, const QVariantList &*args* = {}) {#instantiatePartForMimeType}

Use this method to create a [KParts](kparts-module.md) part. It will try to create an object which inherits `T`.

```cpp
if (auto result = KParts::PartLoader::instantiatePartForMimeType<KParts::ReadOnlyPart>(mimeType, parentWidget, parent, args)) {
    // result.plugin is valid and can be accessed
} else {
    // result contains information about the error
}
```

`T` The interface for which an object should be created. The object will inherit `T`.

`mimeType` The mimetype for which we need a [KParts](kparts-module.md).

`parentWidget` The parent widget for the part's widget.

`parent` The parent of the part.

Returns a Result object which contains the plugin instance and potentially error information

### \[since KParts 6.4\] KParts::PartCapabilities PartLoader::partCapabilities(const KPluginMetaData &*data*) {#partCapabilities}

Parses the associated capabilities from the KPart. This parses the deprecated "ServiceTypes" array of the "KPlugin" object

This function was introduced in KParts 6.4.

### QList\<KPluginMetaData\> PartLoader::partsForMimeType(const QString &*mimeType*) {#partsForMimeType}

Locate all available [KParts](kparts-module.md) using [KPluginMetaData::findPlugins](../kcoreaddons/kpluginmetadata.md#findPlugins) for a mimetype. Returns a list of plugin metadata, sorted by preference. This takes care both of the builtin preference (set by developers) and of user preference (stored in mimeapps.list).

To load a part from one of the [KPluginMetaData](../kcoreaddons/kpluginmetadata.md) instances returned here, use [instantiatePart](kparts-partloader.md#instantiatePart)()
