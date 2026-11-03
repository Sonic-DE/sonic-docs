---
title: "KConfig Class"
description: "The central class of the KDE configuration data system."
---

# KConfig Class

The central class of the KDE configuration data system.

- **Header:** `#include <KConfig>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS Config)`  
  `target_link_libraries(mytarget PRIVATE KF6::ConfigCore)`
- **Inherits:** [KConfigBase](kconfigbase.md)
- **Inherited By:** [KDesktopFile](kdesktopfile.md) and [KSharedConfig](ksharedconfig.md)

## Public Types

- [enum KConfig::OpenFlag](#OpenFlag-enum)

## Public Functions

- [KConfig(const std::shared\_ptr\<QIODevice\> &device, KConfig::OpenFlags mode = SimpleConfig)](#KConfig) (since 6.23)
- [KConfig(const QString &file = QString(), KConfig::OpenFlags mode = FullConfig, QStandardPaths::StandardLocation type = QStandardPaths::GenericConfigLocation)](#KConfig-1)
- [void addConfigSources(const QStringList &sources)](#addConfigSources)
- [QStringList additionalConfigSources() const](#additionalConfigSources)
- [void checkUpdate(const QString &id, const QString &updateFile)](#checkUpdate)
- [void copyFrom(const KConfig &config) const](#copyFrom) (since 6.23)
- [KConfig \*copyTo(const QString &file, KConfig \*config = nullptr) const](#copyTo)
- [QMap\<QString, QString\> entryMap(const QString &aGroup = QString()) const](#entryMap)
- [bool isConfigWritable(bool warnUser)](#isConfigWritable)
- [bool isDirty() const](#isDirty)
- [QString locale() const](#locale)
- [QStandardPaths::StandardLocation locationType() const](#locationType)
- [QString name() const](#name)
- [KConfig::OpenFlags openFlags() const](#openFlags)
- [bool readDefaults() const](#readDefaults)
- [void reparseConfiguration()](#reparseConfiguration)
- [bool setLocale(const QString &aLocale)](#setLocale)
- [void setReadDefaults(bool b)](#setReadDefaults)

## Static Public Members

- [QString mainConfigName()](#mainConfigName)
- [void setMainConfigName(const QString &str)](#setMainConfigName)

## Detailed Description {#details}

In general it is recommended to use [KSharedConfig](ksharedconfig.md) instead of creating multiple instances of [KConfig](kconfig.md) to avoid the overhead of separate objects or concerns about synchronizing writes to disk even if the configuration object is updated from multiple code paths. [KSharedConfig](ksharedconfig.md) provides a set of open methods as counterparts for the [KConfig](kconfig.md) constructors.

Load a specific configuration file:

```cpp
KConfig config("/etc/kderc");
```

Load the configuration for an application stored in `~/.config/appname/appnamerc`:

```cpp
KConfig config("appnamerc", KConfig::SimpleConfig, QStandardPaths::AppConfigLocation);
```

The `appname` should match the name set via [QCoreApplication::setApplicationName](https://doc.qt.io/qt-6/qcoreapplication.html#applicationName-prop) or the component argument of KAboutData::KAboutData.

Load the configuration for an application `~/.config/appnamerc`:

```cpp
KConfig config("appnamerc");
```

Load the user-specific data files for an application in `~/.local/share/appname/appnamerc`:

```cpp
KConfig config("appnamerc", KConfig::NoGlobals, QStandardPaths::AppDataLocation);
```

*See also* [KSharedConfig](ksharedconfig.md), [KConfigGroup](kconfiggroup.md), [Introduction to KConfig](https://develop.kde.org/docs/features/configuration/introduction/)

## Member Type Documentation {#member-type-documentation}

### enum KConfig::OpenFlag {#OpenFlag-enum}

**flags KConfig::OpenFlags**

Determines how the system-wide and user's global settings will affect the reading of the configuration.

If CascadeConfig is selected, system-wide configuration sources are used to provide defaults for the settings accessed through this object, or possibly to override those settings in certain cases.

If IncludeGlobals is selected, the kdeglobals configuration is used as additional configuration sources to provide defaults. Additionally selecting CascadeConfig will result in the system-wide kdeglobals sources also getting included.

Note that the main configuration source overrides the cascaded sources, which override those provided to [addConfigSources](kconfig.md#addConfigSources)(), which override the global sources. The exception is that if a key or group is marked as being immutable, it will not be overridden.

Note that all values other than IncludeGlobals and CascadeConfig are convenience definitions for the basic mode. Do not combine them with anything.

| Constant | Value | Description |
| --- | --- | --- |
| `KConfig::IncludeGlobals` | `0x01` | Blend kdeglobals into the config object. |
| `KConfig::CascadeConfig` | `0x02` | Cascade to system-wide config files. |
| `KConfig::SimpleConfig` | `0x00` | Just a single config file. |
| `KConfig::NoCascade` | `IncludeGlobals` | Include user's globals, but omit system settings. |
| `KConfig::NoGlobals` | `CascadeConfig` | Cascade to system settings, but omit user's globals. |
| `KConfig::FullConfig` | `IncludeGlobals | CascadeConfig` | Fully-fledged config, including globals and cascading to system settings. |

The `OpenFlags` type is a typedef for `QFlags<OpenFlag>. `It stores an OR combination of `OpenFlag` values.

## Member Function Documentation {#member-function-documentation}

### \[explicit, since 6.23\] KConfig::KConfig(const std::shared\_ptr\<QIODevice\> &*device*, KConfig::OpenFlags *mode* = SimpleConfig) {#KConfig}

Creates a [KConfig](kconfig.md) object to manipulate a configuration stored in `device`.

The `device` storing the configuration must already be opened and have the required [QIODeviceBase::OpenMode](https://doc.qt.io/qt-6/qiodevicebase.html#OpenModeFlag-enum).

The `mode` determines whether the user or global settings will be allowed to influence the values returned by this object. Defaults to [SimpleConfig](kconfig.md#OpenFlag-enum) contrary to the other constructor.

This function was introduced in Qt 6.23.

### \[explicit\] KConfig::KConfig(const QString &*file* = QString(), KConfig::OpenFlags *mode* = FullConfig, QStandardPaths::StandardLocation *type* = QStandardPaths::GenericConfigLocation) {#KConfig-1}

Creates a [KConfig](kconfig.md) object to manipulate a configuration file for the current application.

If an absolute path is specified for `file`, that file will be used as the store for the configuration settings. If a non-absolute path is provided, the file will be looked for in the standard directory specified by type. If no path is provided, a default configuration file will be used based on the name of the main application component.

The `mode` determines whether the user or global settings will be allowed to influence the values returned by this object.

> **Note:** You probably want to use [KSharedConfig::openConfig](ksharedconfig.md#openConfig)() instead.

If an empty string is passed to the `file` and [SimpleConfig](kconfig.md#OpenFlag-enum) is passed for the [OpenFlags](kconfig.md#OpenFlag-enum), then an in-memory [KConfig](kconfig.md) object is created that will not write out to file or require any file in the filesystem at all.

*See also* [KConfig::OpenFlags](kconfig-index.md), [KSharedConfig::openConfig](ksharedconfig.md#openConfig)()

### void KConfig::addConfigSources(const QStringList &*sources*) {#addConfigSources}

Adds the list of configuration `sources` to the merge stack.

Currently only files are accepted as configuration `sources`.

The first entry in `sources` is treated as the most general and will be overridden by the second entry. The settings in the final entry in `sources` will override all the other sources provided in the list.

The settings in `sources` will also be overridden by the sources provided by any previous calls to addConfigSources().

The settings in the global configuration sources will be overridden by the sources provided to this method (see [IncludeGlobals](kconfig.md#OpenFlag-enum)).

All the sources provided to any call to this method will be overridden by any files that cascade from the source provided to the constructor (see [CascadeConfig](kconfig.md#OpenFlag-enum)), which will in turn be overridden by the source provided to the constructor.

Note that only the most specific file, namely the file provided to the constructor, will be written to by this object.

The state is automatically updated by this method, so there is no need to call [reparseConfiguration](kconfig.md#reparseConfiguration)().

*See also* [KConfig::OpenFlags](kconfig-index.md)

### QStringList KConfig::additionalConfigSources() const {#additionalConfigSources}

Returns a list of the additional configuration sources used in this object.

### void KConfig::checkUpdate(const QString &*id*, const QString &*updateFile*) {#checkUpdate}

Ensures that the configuration file contains a certain update.

If the configuration file does not contain the update `id` as contained in `updateFile`, kconf\_update is run to update the configuration file.

If you install config update files with critical fixes you may wish to use this method to verify that a critical update has indeed been performed to catch the case where a user restores an old config file from backup that has not been updated yet.

### \[since 6.23\] void KConfig::copyFrom(const KConfig &*config*) const {#copyFrom}

Copies all entries from the passed `config` object to this config.

This function was introduced in Qt 6.23.

### KConfig \*KConfig::copyTo(const QString &*file*, KConfig \**config* = nullptr) const {#copyTo}

Copies all entries form this config object to `file`.

If `config` is set, copies the data of this object to `config`.

If `config` is not set, creates a new [KConfig](kconfig.md) object.

The configuration will not actually be saved to `file` until the returned object is destroyed, or [sync](kconfigbase.md#sync)() is called on it.

```cpp
KConfig *newConfig = config.copyTo("newconfrc");
newConfig->sync();
```

> **Note:** Do not forget to delete the returned [KConfig](kconfig.md) object if `config` was nullptr.

### QMap\<QString, QString\> KConfig::entryMap(const QString &*aGroup* = QString()) const {#entryMap}

Returns a map (tree) of entries in `aGroup`, indexed by key.

The entries are all returned as strings.

The returned map may be empty if the group is empty or not found.

### bool KConfig::isConfigWritable(bool *warnUser*) {#isConfigWritable}

Returns whether the configuration can be written to.

If `warnUser` is true and the configuration cannot be written to (this method returns `false`), a warning message box will be shown to the user telling them to contact their system administrator to get the problem fixed.

The most likely cause for this method returning `false` is that the user does not have write permission for the configuration file.

### bool KConfig::isDirty() const {#isDirty}

Returns `true` if sync has any changes to write out.

### QString KConfig::locale() const {#locale}

Returns the current locale.

*See also* [setLocale](kconfig.md#setLocale)()

### QStandardPaths::StandardLocation KConfig::locationType() const {#locationType}

Returns the standard location enum passed to the constructor.

Used by [KSharedConfig](ksharedconfig.md).

### \[static\] QString KConfig::mainConfigName() {#mainConfigName}

Get the name of application config file.

*See also* [setMainConfigName](kconfig.md#setMainConfigName)()

### QString KConfig::name() const {#name}

Returns the filename used to store the configuration.

### KConfig::OpenFlags KConfig::openFlags() const {#openFlags}

Returns the flags this object was opened with.

### bool KConfig::readDefaults() const {#readDefaults}

Returns `true` if the system-wide defaults will be read instead of the user's settings.

*See also* [setReadDefaults](kconfig.md#setReadDefaults)()

### void KConfig::reparseConfiguration() {#reparseConfiguration}

Updates the state of this object to match the persistent storage. Note that if this object has pending changes, this method will call [sync](kconfigbase.md#sync)() first so as not to lose those changes.

### bool KConfig::setLocale(const QString &*aLocale*) {#setLocale}

Sets the locale to `aLocale`.

The global locale is used by default.

> **Note:** If set to an empty string, no locale will be matched. This effectively disables reading translated entries.

Returns `true` if locale was changed, `false` if the call had no effect (that is, `aLocale` was already the current locale for this object).

*See also* [locale](kconfig.md#locale)()

### \[static\] void KConfig::setMainConfigName(const QString &*str*) {#setMainConfigName}

Sets the name of the application config file with the given string `str`.

*See also* [mainConfigName](kconfig.md#mainConfigName)()

### void KConfig::setReadDefaults(bool *b*) {#setReadDefaults}

When `b` is set, all readEntry calls return the system-wide (default) values instead of the user's settings.

This is off by default.

*See also* [readDefaults](kconfig.md#readDefaults)()

## Obsolete Members for KConfig {#obsolete}

**The following members of class [KConfig](kconfig.md) are deprecated.** We strongly advise against using them in new code.

### Obsolete Member Function Documentation {#obsolete-member-function-documentation}

#### \[deprecated in 6.3\] KConfig::KConfig(const QString &*file*, const QString &*backend*, QStandardPaths::StandardLocation *type* = QStandardPaths::GenericConfigLocation) {#KConfig-2}

This function is deprecated since 6.3. We strongly advise against using it in new code.

Creates a [KConfig](kconfig.md) object at the given `file` using the specified `backend`, with an optional `type` of configuration file. If the backend cannot be found or loaded, then the standard configuration parser is used as a fallback. Use other constructor
