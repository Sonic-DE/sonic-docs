---
title: "KConfigWatcher Class"
description: "Watches for configuration changes."
---

# KConfigWatcher Class

Watches for configuration changes.

- **Header:** `#include <KConfigWatcher>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS Config)`  
  `target_link_libraries(mytarget PRIVATE KF6::ConfigCore)`
- **Inherits:** [QObject](https://doc.qt.io/qt-6/qobject.html)

## Public Types

- [KConfigWatcher::Ptr](#Ptr-typedef)

## Public Functions

- [KSharedConfig::Ptr config() const](#config)

## Signals

- [void configChanged(const KConfigGroup &group, const QByteArrayList &names)](#configChanged)

## Static Public Members

- [KConfigWatcher::Ptr create(const KSharedConfig::Ptr &config)](#create)

## Detailed Description {#details}

The [configChanged](kconfigwatcher.md#configChanged)(const [KConfigGroup](kconfiggroup.md) &group, const [QByteArrayList](https://doc.qt.io/qt-6/qbytearraylist.html) &names) signal is emitted whenever another client has updated this config file with the [KConfigBase::Notify](kconfigbase.md#WriteConfigFlag-enum) flag.

```cpp
KConfigWatcher::Ptr watcher = KConfigWatcher::create(config);
QObject::connect(watcher.data(), &KConfigWatcher::configChanged, [=](){
    qInfo() << "Some config changed!";
});
// ...
generalGroup.writeEntry("SomeKey", "SomeValue", KConfigBase::Notify);
generalGroup.config()->reparseConfiguration();
```

*See also* [KSharedConfig::Ptr](ksharedconfig.md#Ptr-typedef), [KConfigBase::WriteConfigFlags](kconfigbase.md#WriteConfigFlag-enum), [KConfigSkeletonItem::setWriteFlags](kconfigskeletonitem.md#setWriteFlags)(), [KConfigGroup](kconfiggroup.md)

## Member Type Documentation {#member-type-documentation}

### KConfigWatcher::Ptr {#Ptr-typedef}

## Member Function Documentation {#member-function-documentation}

### KSharedConfig::Ptr KConfigWatcher::config() const {#config}

Returns the config being watched.

### \[signal\] void KConfigWatcher::configChanged(const KConfigGroup &*group*, const QByteArrayList &*names*) {#configChanged}

Emitted when a config `group` has changed, passing the list of `names` that have changed within that group.

The config will be reloaded before this signal is emitted.

### \[static\] KConfigWatcher::Ptr KConfigWatcher::create(const KSharedConfig::Ptr &*config*) {#create}

Instantiate a ConfigWatcher for a given `config`

> **Note:** Any additional config sources should be set before this point.
