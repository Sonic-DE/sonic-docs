---
title: "KQuickManagedConfigModule Class"
description: "The base class for configuration modules using KConfigXT settings. This class was introduced in Qt 6.0."
---

# KQuickManagedConfigModule Class

The base class for configuration modules using KConfigXT settings. This class was introduced in Qt 6.0. [More...](#details)

- **Header:** `#include <KQuickManagedConfigModule>`
- **Since:** Qt 6.0
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS KCMUtilsQuick)`  
  `target_link_libraries(mytarget PRIVATE KF6::KCMUtilsQuick)`
- **Inherits:** [KQuickConfigModule](kquickconfigmodule.md)

[List of all members, including inherited members](kquickmanagedconfigmodule-members.md)

## Public Slots

- [void defaults()](#defaults)
- [void load()](#load)
- [void registerSettings(KCoreConfigSkeleton \*skeleton)](#registerSettings)
- [void save()](#save)
- [void settingsChanged()](#settingsChanged)

## Protected Functions

- [KQuickManagedConfigModule(QObject \*parent, const KPluginMetaData &metaData)](#KQuickManagedConfigModule)

## Detailed Description {#details}

We are assuming here that SettingsObject is a class generated from a kcfg file and that it will be somehow exposed as a constant property to be used from the QML side. It will be automatically discovered by ManagedConfigModule which will update the saveNeeded and defaults inherited properties by itself. Thus by inheriting from this class you shall not try to manage those properties yourselves. By passing in "this" as a parent, we prevent memory leaks and allow [KQuickManagedConfigModule](kquickmanagedconfigmodule.md) to automatically find the created settings object.

The constructor of the ConfigModule then looks like this:

```cpp
YourConfigModule::YourConfigModule(QObject *parent, const KPluginMetaData &metaData)
  : KQuickManagedConfigModule(parent, metaData)
  , m_settingsObject(new SettingsObject(this))
{
}
```

## Member Function Documentation {#member-function-documentation}

### \[explicit protected\] KQuickManagedConfigModule::KQuickManagedConfigModule(QObject \**parent*, const KPluginMetaData &*metaData*) {#KQuickManagedConfigModule}

Base class for all KControlModules.

Creates a new [KQuickManagedConfigModule](kquickmanagedconfigmodule.md) with the given `metaData` as a child of `parent`. Use [KQuickConfigModuleLoader](kquickconfigmoduleloader.md) to instantiate this class.

> **Note:** Do not emit changed signals here, since they are not yet connected to any slot.

### \[override virtual slot\] void KQuickManagedConfigModule::defaults() {#defaults}

Reimplements: [KAbstractConfigModule::defaults()](kabstractconfigmodule.md#defaults).

Sets the configuration to sensible default values.

This method is called when the user clicks the "Default" button. It should set the display to useful values.

By default this will reset to defaults the child setting objects of this module.

### \[override virtual slot\] void KQuickManagedConfigModule::load() {#load}

Reimplements: [KAbstractConfigModule::load()](kabstractconfigmodule.md#load).

Loads the configuration data into the module.

This method is invoked whenever the module should read its configuration (most of the times from a config file) and update the user interface. This happens when the user clicks the "Reset" button in the control center, to undo all of his changes and restore the currently valid settings. It is also called right after construction.

By default this will load the settings from the child setting objects of this module.

### \[protected slot\] void KQuickManagedConfigModule::registerSettings(KCoreConfigSkeleton \**skeleton*) {#registerSettings}

Allows to register manually settings class generated from a kcfg file. Used by derived class when automatic discovery is not possible. After `skeleton` is registered it will automatically call [settingsChanged](kquickmanagedconfigmodule.md#settingsChanged)().

### \[override virtual slot\] void KQuickManagedConfigModule::save() {#save}

Reimplements: [KAbstractConfigModule::save()](kabstractconfigmodule.md#save).

Saves the configuration data.

The save method stores the config information as shown in the user interface in the config files. It is called when the user clicks "Apply" or "Ok".

By default this will save the child setting objects of this module.

### \[protected slot\] void KQuickManagedConfigModule::settingsChanged() {#settingsChanged}

Forces the module to reevaluate the saveNeeded and representsDefault state.

This is required for some modules which might have some settings managed outside of KConfigXT objects.
