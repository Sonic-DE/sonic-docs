---
title: "KSharedConfig Class"
description: "KConfig variant using shared memory."
---

# KSharedConfig Class

[KConfig](kconfig.md) variant using shared memory. [More...](#details)

- **Header:** `#include <KSharedConfig>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS Config)`  
  `target_link_libraries(mytarget PRIVATE KF6::ConfigCore)`
- **Inherits:** [KConfig](kconfig.md) and [QSharedData](https://doc.qt.io/qt-6/qshareddata.html)

[List of all members, including inherited members](ksharedconfig-members.md)

## Public Types

- [KSharedConfig::Ptr](#Ptr-typedef)

## Static Public Members

- [KSharedConfig::Ptr openConfig(const QString &fileName = QString(), KConfig::OpenFlags mode = FullConfig, QStandardPaths::StandardLocation type = QStandardPaths::GenericConfigLocation)](#openConfig)
- [KSharedConfig::Ptr openStateConfig(const QString &fileName = QString())](#openStateConfig)

## Detailed Description {#details}

[KSharedConfig](ksharedconfig.md) provides a shared (reference counted) variant of [KConfig](kconfig.md). This allows you to use/manipulate the same configuration files from different places in your code without worrying about accidentally overwriting changes.

The [openConfig](ksharedconfig.md#openConfig)() method is threadsafe: every thread gets a separate repository of shared [KConfig](kconfig.md) objects. This means, however, that you'll be responsible for synchronizing the instances of [KConfig](kconfig.md) for the same filename between threads, using [KConfig::reparseConfiguration](kconfig.md#reparseConfiguration)() after a manual change notification, just like you have to do between processes.

Load a specific configuration file:

```cpp
KSharedConfigPtr config = KSharedConfig::openConfig("/etc/kderc");
```

Load the configuration for an application stored in `~/.config/appname/appnamerc`:

```cpp
KSharedConfigPtr config = KSharedConfig::openConfig("appnamerc", KConfig::SimpleConfig, QStandardPaths::AppConfigLocation);
```

The `appname` should match the name set via [QCoreApplication::setApplicationName](https://doc.qt.io/qt-6/qcoreapplication.html#applicationName-prop) or the component argument of KAboutData::KAboutData.

Load the configuration for an application `~/.config/appnamerc`:

```cpp
KSharedConfigPtr config = KSharedConfig::openConfig("appnamerc");
```

Load the user-specific data files for an application in `~/.local/share/appname/appnamerc`:

```cpp
KSharedConfigPtr config = KSharedConfig::openConfig("appnamerc", KConfig::NoGlobals, QStandardPaths::AppDataLocation);
```

*See also* [KSharedConfig](ksharedconfig.md), [KConfigGroup](kconfiggroup.md), [Introduction to KConfig](https://develop.kde.org/docs/features/configuration/introduction/)

## Member Type Documentation {#member-type-documentation}

### KSharedConfig::Ptr {#Ptr-typedef}

A pointer to a [KSharedConfig](ksharedconfig.md) object.

## Member Function Documentation {#member-function-documentation}

### \[static\] KSharedConfig::Ptr KSharedConfig::openConfig(const QString &*fileName* = QString(), KConfig::OpenFlags *mode* = FullConfig, QStandardPaths::StandardLocation *type* = QStandardPaths::GenericConfigLocation) {#openConfig}

Creates a [KSharedConfig](ksharedconfig.md) object to manipulate a configuration file.

If an absolute path is specified for `fileName`, that file will be used as the store for the configuration settings. If a non-absolute path is provided, the file will be looked for in the standard directory specified by `type`. If no path is provided, a default configuration file will be used based on the name of the main application component as defined in [QCoreApplication::setApplicationName](https://doc.qt.io/qt-6/qcoreapplication.html#applicationName-prop) or the component name of KAboutData::KAboutData, plus rc. For example: "appnamerc".

The `mode` determines whether the user or global settings will be allowed to influence the values returned by this object.

*See also* [KConfig](kconfig-index.md), [KConfig::OpenFlags](kconfig-index.md), [QStandardPaths](https://doc.qt.io/qt-6/qstandardpaths.html)

### \[static\] KSharedConfig::Ptr KSharedConfig::openStateConfig(const QString &*fileName* = QString()) {#openStateConfig}

Creates a [KSharedConfig](ksharedconfig.md) object to manipulate a configuration file suitable for storing state information. Use this for storing information that is changing frequently and should not be saved by configuration backup utilities.

If an absolute path is specified for `fileName`, that file will be used as the store for the configuration settings. If a non-absolute path is provided, the file will be looked for in the standard state directory ([QStandardPaths::GenericStateLocation](https://doc.qt.io/qt-6/qstandardpaths.html#StandardLocation-enum)). If no path is provided, a default configuration file will be used based on the name of the main application component as defined in [QCoreApplication::setApplicationName](https://doc.qt.io/qt-6/qcoreapplication.html#applicationName-prop) or the component name of KAboutData::KAboutData, plus rc. For example: "appnamerc".

*See also* [KConfig](kconfig-index.md)

## Related Non-Members {#related-non-members}

### KSharedConfigPtr {#KSharedConfigPtr-typedef}
