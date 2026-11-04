---
title: "KQuickConfigModuleLoader Namespace"
description: "Utilities for KDE System Settings modules."
---

# KQuickConfigModuleLoader Namespace

Utilities for KDE System Settings modules. [More...](#details)

- **Header:** `#include <KQuickConfigModuleLoader>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS KCMUtilsQuick)`  
  `target_link_libraries(mytarget PRIVATE KF6::KCMUtilsQuick)`

## Detailed Description {#details}

## Function Documentation {#function-documentation}

### KPluginFactory::Result\<KQuickConfigModule\> KQuickConfigModuleLoader::loadModule(const KPluginMetaData &*metaData*, QObject \**parent* = nullptr, const QVariantList &*args* = {}, const std::shared\_ptr\<QQmlEngine\> &*engine* = {}) {#loadModule}

Loads a QML KCM from the given plugin `metaData` as a child of `parent` with the given `args`.

`engine` The QQmlEngine to use. If not set, an internal engine will be created. If your application has an existing engine, this must be passed in.
