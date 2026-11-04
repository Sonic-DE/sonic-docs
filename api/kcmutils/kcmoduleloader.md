---
title: "KCModuleLoader Namespace"
description: "Loads a KCModule."
---

# KCModuleLoader Namespace

Loads a [KCModule](kcmodule.md). [More...](#details)

- **Header:** `#include <KCModuleLoader>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS KCMUtils)`  
  `target_link_libraries(mytarget PRIVATE KF6::KCMUtils)`

## Detailed Description {#details}

In case the provided metadata points to a [KQuickConfigModule](kquickconfigmodule.md), it is wrapped in a [KCModule](kcmodule.md).

## Function Documentation {#function-documentation}

### KCModule \*KCModuleLoader::loadModule(const KPluginMetaData &*metaData*, QWidget \**parent* = nullptr, const QVariantList &*args* = {}, const std::shared\_ptr\<QQmlEngine\> &*engine* = {}) {#loadModule}

Loads a [KCModule](kcmodule.md). If loading fails a KCM which displays an error message is returned.

`metaData` [KPluginMetaData](../kcoreaddons/kpluginmetadata.md) for loading the plugin

`engine` QQmlEngine that will be used for [KQuickConfigModule](kquickconfigmodule.md) classes. If none is set, a internal engine will be created and reused for further modules. In case your app already has an engine, you should pass it in explicitly

Returns a pointer to the loaded [KCModule](kcmodule.md)
