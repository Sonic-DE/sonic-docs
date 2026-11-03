---
title: "KCModuleData Class"
description: "A base class that offers information about a KCModule state."
---

# KCModuleData Class

A base class that offers information about a KCModule state. [More...](#details)

- **Header:** `#include <KCModuleData>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS KCMUtils)`  
  `target_link_libraries(mytarget PRIVATE KCMUtilsCore)`
- **Inherits:** [QObject](https://doc.qt.io/qt-6/qobject.html)

[List of all members, including inherited members](kcmoduledata-members.md)

## Public Functions

- [KCModuleData(QObject \*parent = nullptr)](#KCModuleData)
- [QAction \*auxiliaryAction() const](#auxiliaryAction) (since 6.18)
- [bool isDefaults() const](#isDefaults)
- [bool matchesQuery(const QString &query) const](#matchesQuery)
- [void revertToDefaults()](#revertToDefaults)

## Public Slots

- [void autoRegisterSkeletons()](#autoRegisterSkeletons)
- [void registerSkeleton(KCoreConfigSkeleton \*skeleton)](#registerSkeleton)

## Signals

- [void auxiliaryActionChanged(QAction \*action)](#auxiliaryActionChanged) (since 6.18)
- [void loaded()](#loaded)
- [void relevantChanged(bool relevant)](#relevantChanged) (since 6.18)

## Protected Functions

- [void setAuxiliaryAction(QAction \*action)](#setAuxiliaryAction)
- [void setRelevant(bool relevant)](#setRelevant)

## Detailed Description {#details}

## Member Function Documentation {#member-function-documentation}

### \[explicit\] KCModuleData::KCModuleData(QObject \**parent* = nullptr) {#KCModuleData}

### \[protected slot\] void KCModuleData::autoRegisterSkeletons() {#autoRegisterSkeletons}

Automatically register child skeletons.

Call it in your subclass constructor after skeleton creation

### \[since 6.18\] QAction \*KCModuleData::auxiliaryAction() const {#auxiliaryAction}

An auxiliary action associated with this KCM.

This function was introduced in Qt 6.18.

*See also* [setAuxiliaryAction](kcmoduledata.md#setAuxiliaryAction)()

### \[signal, since 6.18\] void KCModuleData::auxiliaryActionChanged(QAction \**action*) {#auxiliaryActionChanged}

Emitted when the auxiliary action changes.

> **Note:** The [QAction](https://doc.qt.io/qt-6/qaction.html) can change its state (e.g. being enabled) without the action object itself being replaced.

This function was introduced in Qt 6.18.

### \[virtual\] bool KCModuleData::isDefaults() const {#isDefaults}

Checks if the configuration is identical to the default one.

Returns `true` if the module configuration is in the default state, `false` otherwise.

### \[signal\] void KCModuleData::loaded() {#loaded}

Emitted when [KCModuleData](kcmoduledata.md) is loaded.

### \[virtual\] bool KCModuleData::matchesQuery(const QString &*query*) const {#matchesQuery}

Returns whether this module matches a given `query`.

The `query` is not expected to be a regex pattern but a full text search.

### \[protected slot\] void KCModuleData::registerSkeleton(KCoreConfigSkeleton \**skeleton*) {#registerSkeleton}

Allow to manually register a `skeleton` class.

Used by a derived class when automatic discovery is not possible.

### \[signal, since 6.18\] void KCModuleData::relevantChanged(bool *relevant*) {#relevantChanged}

Emitted when the relevancy of this KCM changes.

For example, after (un)plugging a relevant device.

This function was introduced in Qt 6.18.

### \[virtual\] void KCModuleData::revertToDefaults() {#revertToDefaults}

Reverts the module to default values and saves them.

### \[protected\] void KCModuleData::setAuxiliaryAction(QAction \**action*) {#setAuxiliaryAction}

Sets an auxiliary action for this KCM.

This can be displayed alongside this KCM in a list of settings and provide quick access to a feature in the KCM without opening it.

For example, a "Pair new device" action or, in case of a checkable action, a Switch to turn on/off a certain feature or device.

*See also* [auxiliaryAction](kcmoduledata.md#auxiliaryAction)()

### \[protected\] void KCModuleData::setRelevant(bool *relevant*) {#setRelevant}

Sets whether this KCM is relevant in the current environment.

This can hide the KCM in a list of settings when it is currently not relevant.

For example to show touchscreen settings only when a touchscreen is present. Default is true.
