---
title: "KPluginModel Class"
description: "A model that provides a list of available plugins and allows to disable/enable them."
---

# KPluginModel Class

A model that provides a list of available plugins and allows to disable/enable them. [More...](#details)

- **Header:** `#include <KPluginModel>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS KCMUtils)`  
  `target_link_libraries(mytarget PRIVATE KCMUtilsCore)`
- **Inherits:** [QAbstractListModel](https://doc.qt.io/qt-6/qabstractlistmodel.html)

[List of all members, including inherited members](kpluginmodel-members.md)

## Public Types

- [enum KPluginModel::Roles](#Roles-enum)

## Public Functions

- [KPluginModel(QObject \*parent = nullptr)](#KPluginModel)
- [void addPlugins(const QList\<KPluginMetaData\> &plugins, const QString &categoryLabel)](#addPlugins)
- [void addUnsortablePlugins(const QList\<KPluginMetaData\> &plugins, const QString &categoryLabel)](#addUnsortablePlugins) (since 6.0)
- [void clear()](#clear)
- [void defaults()](#defaults)
- [KPluginMetaData findConfigForPluginId(const QString &pluginId) const](#findConfigForPluginId)
- [bool isSaveNeeded()](#isSaveNeeded)
- [void load()](#load)
- [void removePlugin(const KPluginMetaData &data)](#removePlugin) (since 6.0)
- [void save()](#save)
- [void setConfig(const KConfigGroup &config)](#setConfig)

## Signals

- [void defaulted(bool isDefaulted)](#defaulted)
- [void isSaveNeededChanged()](#isSaveNeededChanged)

## Detailed Description {#details}

Plugins need to define the `X-KDE-ConfigModule` property for their config modules to be found. The value for this property is the namespace and file name of the KCM for the plugin.

An example value is "kf6/krunner/kcms/kcm\_krunner\_charrunner", "kf6/krunner/kcms" is the namespace and "kcm\_krunner\_charrunner" the file name. The loaded KCMs don't need any embedded JSON metadata.

*See also* [KPluginWidget](kpluginwidget.md)

## Member Type Documentation {#member-type-documentation}

### enum KPluginModel::Roles {#Roles-enum}

| Constant |   |
| --- | --- |
| `KPluginModel::NameRole` | `Qt::DisplayRole` |
| `KPluginModel::IconRole` | `Qt::DecorationRole` |
| `KPluginModel::EnabledRole` | `Qt::CheckStateRole` |
| `KPluginModel::DescriptionRole` | `Qt::UserRole + 1` |
| `KPluginModel::IsChangeableRole` | `258` |
| `KPluginModel::MetaDataRole` | `259` |
| `KPluginModel::ConfigRole` | `260` |
| `KPluginModel::IdRole` | `261` |
| `KPluginModel::EnabledByDefaultRole` | `262` |
| `KPluginModel::SortableRole` | `263` |

## Member Function Documentation {#member-function-documentation}

### \[explicit\] KPluginModel::KPluginModel(QObject \**parent* = nullptr) {#KPluginModel}

### void KPluginModel::addPlugins(const QList\<KPluginMetaData\> &*plugins*, const QString &*categoryLabel*) {#addPlugins}

Appends `plugins` to the model.

This will not replace existing entries.

`plugins` The plugins to be added.

`categoryLabel` A user-visible label for the section the plugins are added to.

### \[since 6.0\] void KPluginModel::addUnsortablePlugins(const QList\<KPluginMetaData\> &*plugins*, const QString &*categoryLabel*) {#addUnsortablePlugins}

Adds `plugins` that should not be sorted automatically based on their name.

This is useful in case your app has a custom sorting mechanism or implements reordering of plugins.

`plugins` The plugins to be added.

`categoryLabel` A user-visible label for the section the plugins are added to.

This function was introduced in Qt 6.0.

### void KPluginModel::clear() {#clear}

Removes all plugins.

### \[signal\] void KPluginModel::defaulted(bool *isDefaulted*) {#defaulted}

Emitted when the enabled state `isDefaulted`, that is, it matches the default changes.

*See also* [defaults](kpluginmodel.md#defaults)

### void KPluginModel::defaults() {#defaults}

Resets the enabled state of the plugins to its defaults.

### KPluginMetaData KPluginModel::findConfigForPluginId(const QString &*pluginId*) const {#findConfigForPluginId}

Returns the [KPluginMetaData](../kcoreaddons/kpluginmetadata.md) object of the plugin's config module with the specified `pluginId`.

If no plugin is found or the plugin does not have a config, the resulting [KPluginMetaData](../kcoreaddons/kpluginmetadata.md) object will be invalid.

### bool KPluginModel::isSaveNeeded() {#isSaveNeeded}

Returns whether there are unsaved changes to the enabled state of the plugins.

### \[signal\] void KPluginModel::isSaveNeededChanged() {#isSaveNeededChanged}

Emitted when [isSaveNeeded](kpluginmodel.md#isSaveNeeded) is changed.

### void KPluginModel::load() {#load}

Loads the enabled state of the plugins from the config group set by [setConfig](kpluginmodel.md#setConfig).

### \[since 6.0\] void KPluginModel::removePlugin(const KPluginMetaData &*data*) {#removePlugin}

Removes a plugin with the specified `data`.

This function was introduced in Qt 6.0.

### void KPluginModel::save() {#save}

Saves the enabled state of the plugins to the config group set by [setConfig](kpluginmodel.md#setConfig).

### void KPluginModel::setConfig(const KConfigGroup &*config*) {#setConfig}

Sets the [KConfigGroup](../kconfigcore/kconfiggroup.md) `config` that is used to load/save the enabled state.
