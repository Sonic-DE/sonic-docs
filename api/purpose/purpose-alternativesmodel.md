---
title: "Purpose::AlternativesModel Class"
description: "Interface for client applications to share data."
---

# Purpose::AlternativesModel Class

Interface for client applications to share data. [More...](#details)

- **Header:** `#include <Purpose/AlternativesModel>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS Purpose)`  
  `target_link_libraries(mytarget PRIVATE KF6::Purpose)`
- **Inherits:** [QAbstractListModel](https://doc.qt.io/qt-6/qabstractlistmodel.html)

[List of all members, including inherited members](purpose-alternativesmodel-members.md)

## Public Types

- [enum AlternativesModel::Roles](#Roles-enum)

## Properties

- [disabledPlugins : QStringList](#disabledPlugins-prop)
- [inputData : QJsonObject](#inputData-prop)
- [pluginType : QString](#pluginType-prop)

## Public Functions

- [AlternativesModel(QObject \*parent = nullptr)](#AlternativesModel)
- [Purpose::Configuration \*configureJob(int row)](#configureJob)

## Detailed Description {#details}

Lists all the alternatives to share a specified type of data then provides a method to trigger a job.

## Member Type Documentation {#member-type-documentation}

### enum AlternativesModel::Roles {#Roles-enum}

| Constant |   |
| --- | --- |
| `Purpose::AlternativesModel::PluginIdRole` | `Qt::UserRole + 1` |
| `Purpose::AlternativesModel::IconNameRole` | `258` |
| `Purpose::AlternativesModel::ActionDisplayRole` | `259` |

## Property Documentation {#property-documentation}

### disabledPlugins : QStringList {#disabledPlugins-prop}

Provides a list of plugin names to have filtered out.

**Access functions:**

- `QStringList` **disabledPlugins**() const
- `void` **setDisabledPlugins**(const `QStringList` &*pluginIds*)

**Notifier signal:**

- `void` **disabledPluginsChanged**()

### inputData : QJsonObject {#inputData-prop}

Specifies the information that will be given to the plugin once it's started.

> **Note:** some plugins might be filtered out based on this setting

**Access functions:**

- `QJsonObject` **inputData**() const
- `void` **setInputData**(const `QJsonObject` &*input*)

**Notifier signal:**

- `void` **inputDataChanged**()

### pluginType : QString {#pluginType-prop}

Specifies the type of the plugin we want to list.

**Access functions:**

- `QString` **pluginType**() const
- `void` **setPluginType**(const `QString` &*pluginType*)

**Notifier signal:**

- `void` **pluginTypeChanged**()

*See also* [inputData](purpose-alternativesmodel.md#inputData-prop)

## Member Function Documentation {#member-function-documentation}

### \[explicit\] AlternativesModel::AlternativesModel(QObject \**parent* = nullptr) {#AlternativesModel}

Constructs an alternatives model with the given `parent`.

### Purpose::Configuration \*AlternativesModel::configureJob(int *row*) {#configureJob}

This shouldn't require to have the job actually running on the same process as the app.

`row` specifies the alternative to be used.

Returns the configuration instance that will offer the job.
