---
title: "Purpose::Configuration Class"
description: "This class will be in charge of figuring out the job configuration."
---

# Purpose::Configuration Class

This class will be in charge of figuring out the job configuration. [More...](#details)

- **Header:** `#include <Purpose/Configuration>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS Purpose)`  
  `target_link_libraries(mytarget PRIVATE KF6::Purpose)`
- **Inherits:** [QObject](https://doc.qt.io/qt-6/qobject.html)

[List of all members, including inherited members](purpose-configuration-members.md)

## Properties

- [\[read-only\] configSourceCode : const QUrl](#configSourceCode-prop)
- [data : QJsonObject](#data-prop)
- [\[read-only\] isReady : bool](#isReady-prop)
- [\[read-only\] neededArguments : const QJsonArray](#neededArguments-prop)
- [\[read-only\] pluginName : const QString](#pluginName-prop)
- [\[read-only\] pluginTypeName : const QString](#pluginTypeName-prop)

## Public Functions

- [Configuration(const QJsonObject &inputData, const QString &pluginTypeName, const KPluginMetaData &pluginInformation, QObject \*parent = nullptr)](#Configuration)
- [Configuration(const QJsonObject &inputData, const QString &pluginTypeName, const QJsonObject &pluginType, const KPluginMetaData &pluginInformation, QObject \*parent = nullptr)](#Configuration-1)
- [~Configuration()](#dtor.Configuration)
- [Purpose::Job \*createJob()](#createJob)
- [void setUseSeparateProcess(bool separate)](#setUseSeparateProcess)
- [bool useSeparateProcess() const](#useSeparateProcess)

## Detailed Description {#details}

Once it's figured out, it can proceed to create the job.

The object will be destroyed as soon as the job finishes.

## Property Documentation {#property-documentation}

### \[read-only\] configSourceCode : const QUrl {#configSourceCode-prop}

Specifies the QML source code to be used, to configure the current job.

**Access functions:**

- `QUrl` **configSourceCode**() const

### data : QJsonObject {#data-prop}

Represents the data the job will have available to perform its task.

**Access functions:**

- `QJsonObject` **data**() const
- `void` **setData**(const `QJsonObject` &*data*)

**Notifier signal:**

- `void` **dataChanged**()

### \[read-only\] isReady : bool {#isReady-prop}

Tells whether there's still information to be provided, to be able to run the job.

**Access functions:**

- `bool` **isReady**() const

**Notifier signal:**

- `void` **[dataChanged](purpose-configuration.md#data-prop)**()

### \[read-only\] neededArguments : const QJsonArray {#neededArguments-prop}

Specifies the arguments the config file and the job will be sharing.

**Access functions:**

- `QJsonArray` **neededArguments**() const

### \[read-only\] pluginName : const QString {#pluginName-prop}

Returns the plugin name to display.

**Access functions:**

- `QString` **pluginName**() const

### \[read-only\] pluginTypeName : const QString {#pluginTypeName-prop}

Returns the plugin type name to display.

**Access functions:**

- `QString` **pluginTypeName**() const

## Member Function Documentation {#member-function-documentation}

### Configuration::Configuration(const QJsonObject &*inputData*, const QString &*pluginTypeName*, const KPluginMetaData &*pluginInformation*, QObject \**parent* = nullptr) {#Configuration}

Constructs a new configuration.

### Configuration::Configuration(const QJsonObject &*inputData*, const QString &*pluginTypeName*, const QJsonObject &*pluginType*, const KPluginMetaData &*pluginInformation*, QObject \**parent* = nullptr) {#Configuration-1}

Constructs a new configuration.

### \[override virtual noexcept\] Configuration::~Configuration() {#dtor.Configuration}

Destroys the configuration.

### Purpose::Job \*Configuration::createJob() {#createJob}

Returns the configured job ready to be started.

Before calling it, make sure that all information has been filled by checking [isReady](purpose-configuration.md#isReady-prop)().

### void Configuration::setUseSeparateProcess(bool *separate*) {#setUseSeparateProcess}

`separate` will specify whether the process will be forced to execute in-process or in a separate process.

*See also* [useSeparateProcess](purpose-configuration.md#useSeparateProcess)()

### bool Configuration::useSeparateProcess() const {#useSeparateProcess}

Returns whether the job will be run in the same process.

By default it will be true, unless the environment variable `KDE_PURPOSE_LOCAL_JOBS` is defined.

*See also* [setUseSeparateProcess](purpose-configuration.md#setUseSeparateProcess)()
