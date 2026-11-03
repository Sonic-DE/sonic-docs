---
title: "KConfigPropertyMap Class"
description: "An object that (optionally) automatically saves changes in a property map to a configuration object (such as a KConfig file)."
---

# KConfigPropertyMap Class

An object that (optionally) automatically saves changes in a property map to a configuration object (such as a [KConfig](../kconfigcore/kconfig.md) file). [More...](#details)

- **Header:** `#include <KConfigPropertyMap>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS Config)`  
  `target_link_libraries(mytarget PRIVATE KF6::ConfigQml)`
- **Inherits:** [QQmlPropertyMap](https://doc.qt.io/qt-6/qqmlpropertymap.html)

[List of all members, including inherited members](kconfigpropertymap-members.md)

## Public Functions

- [KConfigPropertyMap(KCoreConfigSkeleton \*config, QObject \*parent = nullptr)](#KConfigPropertyMap)
- [bool isImmutable(const QString &key) const](#isImmutable)
- [bool isNotify() const](#isNotify)
- [void setNotify(bool notify)](#setNotify)
- [void writeConfig()](#writeConfig)

## Detailed Description {#details}

## Member Function Documentation {#member-function-documentation}

### KConfigPropertyMap::KConfigPropertyMap(KCoreConfigSkeleton \**config*, QObject \**parent* = nullptr) {#KConfigPropertyMap}

### \[invokable\] bool KConfigPropertyMap::isImmutable(const QString &*key*) const {#isImmutable}

Returns whether the value at the given key is immutable.

> **Note:** This function can be invoked via the meta-object system and from QML. See Q\_INVOKABLE.

### bool KConfigPropertyMap::isNotify() const {#isNotify}

Returns whether notifications on config changes are enabled.

Disabled by default.

*See also* [KConfigBase::Notify](../kconfigcore/kconfigbase.md#WriteConfigFlag-enum)

### void KConfigPropertyMap::setNotify(bool *notify*) {#setNotify}

Enables or disables notifications upon config changes.

*See also* [isNotify](kconfigpropertymap.md#isNotify)(), [KConfigBase::Notify](../kconfigcore/kconfigbase.md#WriteConfigFlag-enum)

### \[invokable\] void KConfigPropertyMap::writeConfig() {#writeConfig}

Saves the state of the property map to disk.

> **Note:** This function can be invoked via the meta-object system and from QML. See Q\_INVOKABLE.
