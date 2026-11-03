---
title: "KPluginMetaData Class"
description: "This class allows easily accessing some standardized values from the JSON metadata that can be embedded into Qt plugins."
---

# KPluginMetaData Class

This class allows easily accessing some standardized values from the JSON metadata that can be embedded into Qt plugins. [More...](#details)

- **Header:** `#include <KPluginMetaData>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS CoreAddons)`  
  `target_link_libraries(mytarget PRIVATE KF6::CoreAddons)`

[List of all members, including inherited members](kpluginmetadata-members.md)

## Public Types

- [enum KPluginMetaData::KPluginMetaDataOption](#KPluginMetaDataOption-enum)

## Properties

- [\[read-only\] authors : const QList\<KAboutPerson\>](#authors-prop)
- [\[read-only\] bugReportUrl : const QString](#bugReportUrl-prop)
- [\[read-only\] category : const QString](#category-prop)
- [\[read-only\] copyrightText : const QString](#copyrightText-prop)
- [\[read-only\] description : const QString](#description-prop)
- [\[read-only\] fileName : const QString](#fileName-prop)
- [\[read-only\] formFactors : const QStringList](#formFactors-prop)
- [\[read-only\] iconName : const QString](#iconName-prop)
- [\[read-only\] isEnabledByDefault : const bool](#isEnabledByDefault-prop)
- [\[read-only\] isHidden : const bool](#isHidden-prop)
- [\[read-only\] isValid : const bool](#isValid-prop)
- [\[read-only\] license : const QString](#license-prop)
- [\[read-only\] licenseText : const QString](#licenseText-prop)
- [\[read-only\] mimeTypes : const QStringList](#mimeTypes-prop)
- [\[read-only\] name : const QString](#name-prop)
- [\[read-only\] otherContributors : const QList\<KAboutPerson\>](#otherContributors-prop)
- [\[read-only\] pluginId : const QString](#pluginId-prop)
- [\[read-only\] rawData : const QJsonObject](#rawData-prop)
- [\[read-only\] translators : const QList\<KAboutPerson\>](#translators-prop)
- [\[read-only\] version : const QString](#version-prop)
- [\[read-only\] website : const QString](#website-prop)

## Public Functions

- [KPluginMetaData()](#KPluginMetaData)
- [KPluginMetaData(const QJsonObject &metaData, const QString &fileName)](#KPluginMetaData-1) (since 6.0)
- [KPluginMetaData(const QPluginLoader &loader, KPluginMetaData::KPluginMetaDataOptions options = {})](#KPluginMetaData-2)
- [KPluginMetaData(const QString &pluginFile, KPluginMetaData::KPluginMetaDataOptions options = {})](#KPluginMetaData-3)
- [QList\<KAboutPerson\> authors() const](#authors)
- [QString bugReportUrl() const](#bugReportUrl)
- [QString category() const](#category)
- [QString copyrightText() const](#copyrightText)
- [QString description() const](#description)
- [QString fileName() const](#fileName)
- [QStringList formFactors() const](#formFactors)
- [QString iconName() const](#iconName)
- [template \<typename T\> bool isEnabled(const T &config) const](#isEnabled)
- [bool isEnabledByDefault() const](#isEnabledByDefault)
- [bool isHidden() const](#isHidden)
- [bool isStaticPlugin() const](#isStaticPlugin)
- [bool isValid() const](#isValid)
- [QString license() const](#license)
- [QString licenseText() const](#licenseText)
- [QStringList mimeTypes() const](#mimeTypes)
- [QString name() const](#name)
- [QList\<KAboutPerson\> otherContributors() const](#otherContributors)
- [QString pluginId() const](#pluginId)
- [QJsonObject rawData() const](#rawData)
- [bool supportsMimeType(const QString &mimeType) const](#supportsMimeType)
- [QList\<KAboutPerson\> translators() const](#translators)
- [QString value(QStringView key, const QString &defaultValue = QString()) const](#value)
- [bool value(QStringView key, bool defaultValue) const](#value-1)
- [QStringList value(QStringView key, const QStringList &defaultValue) const](#value-2)
- [int value(QStringView key, int defaultValue) const](#value-3)
- [QString version() const](#version)
- [QString website() const](#website)
- [bool KPluginMetaData::operator==(const KPluginMetaData &other) const](#operator-eq-eq)

## Static Public Members

- [KPluginMetaData findPluginById(const QString &directory, const QString &pluginId, KPluginMetaData::KPluginMetaDataOptions options = {})](#findPluginById)
- [QList\<KPluginMetaData\> findPlugins(const QString &directory, std::function\<bool (const KPluginMetaData &)\> filter = {}, KPluginMetaData::KPluginMetaDataOptions options = {})](#findPlugins)
- [KPluginMetaData fromJsonFile(const QString &jsonFile)](#fromJsonFile)

## Detailed Description {#details}

Additional plugin-specific metadata can be retrieved by directly reading from the [QJsonObject](https://doc.qt.io/qt-6/qjsonobject.html) returned by [KPluginMetaData::rawData](kpluginmetadata.md#rawData).

For embedded metadata, you should not specify an id manually. Instead the id will be derived from the file basename.

The following keys will be read from an object "KPlugin" inside the metadata JSON:

| Key | Accessor function | JSON Type |
| --- | --- | --- |
| Name | [name](kpluginmetadata.md#name)() | string |
| Description | [description](kpluginmetadata.md#description)() | string |
| Icon | [iconName](kpluginmetadata.md#iconName)() | string |
| Authors | [authors](kpluginmetadata.md#authors)() | object array ([KAboutPerson](kaboutperson.md)) |
| Category | [category](kpluginmetadata.md#category)() | string |
| License | [license](kpluginmetadata.md#license)() | string |
| Copyright | [copyrightText](kpluginmetadata.md#copyrightText)() | string |
| Id | [pluginId](kpluginmetadata.md#pluginId)() | string |
| Version | [version](kpluginmetadata.md#version)() | string |
| Website | [website](kpluginmetadata.md#website)() | string |
| BugReportUrl | [bugReportUrl](kpluginmetadata.md#bugReportUrl)() | string |
| EnabledByDefault | [isEnabledByDefault](kpluginmetadata.md#isEnabledByDefault)() | bool |
| MimeTypes | [mimeTypes](kpluginmetadata.md#mimeTypes)() | string array |
| FormFactors | [formFactors](kpluginmetadata.md#formFactors)() | string array |
| Translators | [translators](kpluginmetadata.md#translators)() | object array ([KAboutPerson](kaboutperson.md)) |
| OtherContributors | [otherContributors](kpluginmetadata.md#otherContributors)() | object array ([KAboutPerson](kaboutperson.md)) |

The Authors, Translators and OtherContributors keys are expected to be list of objects that match the structure expected by [KAboutPerson::fromJSON](kaboutperson.md#fromJSON).

An example metadata json file could look like this:

```cpp
{
  "KPlugin": {
     "Name": "Date and Time",
     "Description": "Date and time by timezone",
     "Icon": "preferences-system-time",
     "Authors": [ { "Name": "Aaron Seigo", "Email": "aseigo@kde.org" } ],
     "Category": "Date and Time",
     "EnabledByDefault": "true",
     "License": "LGPL",
     "Version": "1.0",
     "Website": "https://plasma.kde.org/"
  }
}
```

*See also* [KAboutPerson::fromJSON](kaboutperson.md#fromJSON)()

## Member Type Documentation {#member-type-documentation}

### enum KPluginMetaData::KPluginMetaDataOption {#KPluginMetaDataOption-enum}

**flags KPluginMetaData::KPluginMetaDataOptions**

Options for creating a [KPluginMetaData](kpluginmetadata.md) object.

| Constant | Value | Description |
| --- | --- | --- |
| `KPluginMetaData::AllowEmptyMetaData` | `1` | Plugins with empty metaData are considered valid |
| `KPluginMetaData::CacheMetaData (since Qt 6.0)` | `2` | If [KCoreAddons](kcoreaddons-module.md) should keep metadata in cache. This makes querying the namespace again faster. Consider using this if you need revalidation of plugins |

The `KPluginMetaDataOptions` type is a typedef for `QFlags<KPluginMetaDataOption>. `It stores an OR combination of `KPluginMetaDataOption` values.

## Property Documentation {#property-documentation}

### \[read-only\] authors : const QList\<KAboutPerson\> {#authors-prop}

**Access functions:**

- `QList`\<`KAboutPerson`\> **[authors](kpluginmetadata.md#authors)**() const

### \[read-only\] bugReportUrl : const QString {#bugReportUrl-prop}

**Access functions:**

- `QString` **[bugReportUrl](kpluginmetadata.md#bugReportUrl)**() const

### \[read-only\] category : const QString {#category-prop}

**Access functions:**

- `QString` **[category](kpluginmetadata.md#category)**() const

### \[read-only\] copyrightText : const QString {#copyrightText-prop}

**Access functions:**

- `QString` **[copyrightText](kpluginmetadata.md#copyrightText)**() const

### \[read-only\] description : const QString {#description-prop}

**Access functions:**

- `QString` **[description](kpluginmetadata.md#description)**() const

### \[read-only\] fileName : const QString {#fileName-prop}

**Access functions:**

- `QString` **[fileName](kpluginmetadata.md#fileName)**() const

### \[read-only\] formFactors : const QStringList {#formFactors-prop}

**Access functions:**

- `QStringList` **[formFactors](kpluginmetadata.md#formFactors)**() const

### \[read-only\] iconName : const QString {#iconName-prop}

**Access functions:**

- `QString` **[iconName](kpluginmetadata.md#iconName)**() const

### \[read-only\] isEnabledByDefault : const bool {#isEnabledByDefault-prop}

**Access functions:**

- `bool` **[isEnabledByDefault](kpluginmetadata.md#isEnabledByDefault)**() const

### \[read-only\] isHidden : const bool {#isHidden-prop}

**Access functions:**

- `bool` **[isHidden](kpluginmetadata.md#isHidden)**() const

### \[read-only\] isValid : const bool {#isValid-prop}

**Access functions:**

- `bool` **[isValid](kpluginmetadata.md#isValid)**() const

### \[read-only\] license : const QString {#license-prop}

**Access functions:**

- `QString` **[license](kpluginmetadata.md#license)**() const

### \[read-only\] licenseText : const QString {#licenseText-prop}

**Access functions:**

- `QString` **[licenseText](kpluginmetadata.md#licenseText)**() const

### \[read-only\] mimeTypes : const QStringList {#mimeTypes-prop}

**Access functions:**

- `QStringList` **[mimeTypes](kpluginmetadata.md#mimeTypes)**() const

### \[read-only\] name : const QString {#name-prop}

**Access functions:**

- `QString` **[name](kpluginmetadata.md#name)**() const

### \[read-only\] otherContributors : const QList\<KAboutPerson\> {#otherContributors-prop}

**Access functions:**

- `QList`\<`KAboutPerson`\> **[otherContributors](kpluginmetadata.md#otherContributors)**() const

### \[read-only\] pluginId : const QString {#pluginId-prop}

**Access functions:**

- `QString` **[pluginId](kpluginmetadata.md#pluginId)**() const

### \[read-only\] rawData : const QJsonObject {#rawData-prop}

**Access functions:**

- `QJsonObject` **[rawData](kpluginmetadata.md#rawData)**() const

### \[read-only\] translators : const QList\<KAboutPerson\> {#translators-prop}

**Access functions:**

- `QList`\<`KAboutPerson`\> **[translators](kpluginmetadata.md#translators)**() const

### \[read-only\] version : const QString {#version-prop}

**Access functions:**

- `QString` **[version](kpluginmetadata.md#version)**() const

### \[read-only\] website : const QString {#website-prop}

**Access functions:**

- `QString` **[website](kpluginmetadata.md#website)**() const

## Member Function Documentation {#member-function-documentation}

### KPluginMetaData::KPluginMetaData() {#KPluginMetaData}

Creates an invalid [KPluginMetaData](kpluginmetadata.md) instance

### \[since 6.0\] KPluginMetaData::KPluginMetaData(const QJsonObject &*metaData*, const QString &*fileName*) {#KPluginMetaData-1}

Creates a [KPluginMetaData](kpluginmetadata.md) from a [QJsonObject](https://doc.qt.io/qt-6/qjsonobject.html) holding the metadata and a file name This can be used if the data is not retrieved from a Qt C++ plugin library but from some other source.

`metaData` the JSON metadata to use for this object

`pluginFile` the file that the plugin can be loaded from

This function was introduced in Qt 6.0.

### KPluginMetaData::KPluginMetaData(const QPluginLoader &*loader*, KPluginMetaData::KPluginMetaDataOptions *options* = {}) {#KPluginMetaData-2}

Reads the plugin metadata from a [QPluginLoader](https://doc.qt.io/qt-6/qpluginloader.html) instance. You must call [QPluginLoader::setFileName](https://doc.qt.io/qt-6/qpluginloader.html#fileName-prop)() or use the appropriate constructor on `loader` before calling this.

`options` Whether or not plugins without JSON metadata are considered valid.

### KPluginMetaData::KPluginMetaData(const QString &*pluginFile*, KPluginMetaData::KPluginMetaDataOptions *options* = {}) {#KPluginMetaData-3}

Reads the plugin metadata from a plugin which can be loaded from `file`.

Platform-specific library suffixes may be omitted since `file` will be resolved using the same logic as [QPluginLoader](https://doc.qt.io/qt-6/qpluginloader.html).

`options` Whether or not plugins without JSON metadata are considered valid.

*See also* [QPluginLoader::setFileName](https://doc.qt.io/qt-6/qpluginloader.html#fileName-prop)()

### QList\<KAboutPerson\> KPluginMetaData::authors() const {#authors}

Returns the author(s) of this plugin.

> **Note:** Getter function for property [authors](kpluginmetadata.md#authors-prop).

### QString KPluginMetaData::bugReportUrl() const {#bugReportUrl}

Returns the website where people can report a bug found in this plugin

> **Note:** Getter function for property [bugReportUrl](kpluginmetadata.md#bugReportUrl-prop).

### QString KPluginMetaData::category() const {#category}

Returns the categories of this plugin (e.g. "playlist/skin").

> **Note:** Getter function for property [category](kpluginmetadata.md#category-prop).

### QString KPluginMetaData::copyrightText() const {#copyrightText}

Returns a short copyright statement

> **Note:** Getter function for property [copyrightText](kpluginmetadata.md#copyrightText-prop).

### QString KPluginMetaData::description() const {#description}

Returns a short description of the plugin.

> **Note:** Getter function for property [description](kpluginmetadata.md#description-prop).

### QString KPluginMetaData::fileName() const {#fileName}

Returns the path to the plugin.

When the [KPluginMetaData](kpluginmetadata.md)([QJsonObject](https://doc.qt.io/qt-6/qjsonobject.html), [QString](https://doc.qt.io/qt-6/qstring.html)) constructor is used, the string is not modified. Otherwise, the path is resolved using [QPluginLoader](https://doc.qt.io/qt-6/qpluginloader.html). For static plugins the fileName is the namespace and [pluginId](kpluginmetadata.md#pluginId) concatenated.

> **Note:** It is not guaranteed that this is a valid path to a shared library (i.e. loadable by [QPluginLoader](https://doc.qt.io/qt-6/qpluginloader.html)) since the metadata could also refer to a non-C++ plugin.

> **Note:** Getter function for property [fileName](kpluginmetadata.md#fileName-prop).

### \[static\] KPluginMetaData KPluginMetaData::findPluginById(const QString &*directory*, const QString &*pluginId*, KPluginMetaData::KPluginMetaDataOptions *options* = {}) {#findPluginById}

`directory` The directory to search for plugins. If a relative path is given for `directory`, all entries of [QCoreApplication::libraryPaths](https://doc.qt.io/qt-6/qcoreapplication.html#libraryPaths)() will be checked with `directory` appended as a subdirectory. If an absolute path is given only that directory will be searched.

> **Note:** Check if the returned [KPluginMetaData](kpluginmetadata.md) is valid before continuing to use it.

`pluginId` The Id of the plugin. The id should be the same as the filename, see [KPluginMetaData::pluginId](kpluginmetadata.md#pluginId)()

`options` Whether or not plugins without JSON metadata are considered valid.

### \[static\] QList\<KPluginMetaData\> KPluginMetaData::findPlugins(const QString &*directory*, std::function\<bool (const KPluginMetaData &)\> *filter* = {}, KPluginMetaData::KPluginMetaDataOptions *options* = {}) {#findPlugins}

Find all plugins inside `directory` that satisfy a filter.

`directory` The directory to search for plugins. If a relative path is given for `directory`, all entries of [QCoreApplication::libraryPaths](https://doc.qt.io/qt-6/qcoreapplication.html#libraryPaths)() will be checked with `directory` appended as a subdirectory. If an absolute path is given only that directory will be searched.

`filter` a callback function that returns `true` if the found plugin should be loaded and `false` if it should be skipped. If this argument is omitted all plugins will be loaded.

`options` Whether or not plugins without JSON metadata are considered valid.

Returns all plugins found in `directory` that fulfill the constraints of `filter`

### QStringList KPluginMetaData::formFactors() const {#formFactors}

Returns A string list of formfactors this plugin is useful for, e.g. desktop, handset or mediacenter. The keys for this are not formally defined, though the above-mentioned values should be used when applicable.

> **Note:** Getter function for property [formFactors](kpluginmetadata.md#formFactors-prop).

### \[static\] KPluginMetaData KPluginMetaData::fromJsonFile(const QString &*jsonFile*) {#fromJsonFile}

Load a [KPluginMetaData](kpluginmetadata.md) instance from a .json file. Unlike the constructor with a single file argument, this ensure that only JSON format plugins are loaded and any other type is rejected.

`jsonFile` the .json file to load

### QString KPluginMetaData::iconName() const {#iconName}

Returns the icon name for this plugin

> **Note:** Getter function for property [iconName](kpluginmetadata.md#iconName-prop).

*See also* QIcon::fromTheme()

### template \<typename T\> bool KPluginMetaData::isEnabled(const T &*config*) const {#isEnabled}

Returns `true` if the plugin is enabled in `config`, otherwise returns [isEnabledByDefault](kpluginmetadata.md#isEnabledByDefault)(). This can be used in conjunction with KPluginWidget.

The `config` param should be a KConfigGroup object, because [KCoreAddons](kcoreaddons-module.md) can not depend on KConfig directly, this parameter is a template.

`config` KConfigGroup where the enabled state is stored

### bool KPluginMetaData::isEnabledByDefault() const {#isEnabledByDefault}

Returns whether the plugin should be enabled by default. This is only a recommendation, applications can ignore this value if they want to.

> **Note:** Getter function for property [isEnabledByDefault](kpluginmetadata.md#isEnabledByDefault-prop).

### bool KPluginMetaData::isHidden() const {#isHidden}

Returns whether this object should be hidden

> **Note:** Getter function for property [isHidden](kpluginmetadata.md#isHidden-prop).

### bool KPluginMetaData::isStaticPlugin() const {#isStaticPlugin}

Returns true if the instance represents a static plugin

> **Note:** for loading plugin the plugin independently of it being static/dynamic use [KPluginFactory::loadFactory](kpluginfactory.md#loadFactory) or [KPluginFactory::instantiatePlugin](kpluginfactory.md#instantiatePlugin).

### bool KPluginMetaData::isValid() const {#isValid}

Returns whether this object holds valid information about a plugin.

If this is `true` [pluginId](kpluginmetadata.md#pluginId)() will return a non-empty string.

> **Note:** Getter function for property [isValid](kpluginmetadata.md#isValid-prop).

### QString KPluginMetaData::license() const {#license}

Returns the short license identifier (e.g. LGPL).

See [KAboutLicense::byKeyword](kaboutlicense.md#byKeyword)() for retrieving the full license information

> **Note:** Getter function for property [license](kpluginmetadata.md#license-prop).

### QString KPluginMetaData::licenseText() const {#licenseText}

Returns the text of the license, equivalent to [KAboutLicense::byKeyword](kaboutlicense.md#byKeyword)([license](kpluginmetadata.md#license)()).text()

> **Note:** Getter function for property [licenseText](kpluginmetadata.md#licenseText-prop).

### QStringList KPluginMetaData::mimeTypes() const {#mimeTypes}

Returns a list of MIME types this plugin can handle (e.g. "application/pdf", "image/png", etc.)

> **Note:** Getter function for property [mimeTypes](kpluginmetadata.md#mimeTypes-prop).

### QString KPluginMetaData::name() const {#name}

Returns the user visible name of the plugin.

> **Note:** Getter function for property [name](kpluginmetadata.md#name-prop).

### QList\<KAboutPerson\> KPluginMetaData::otherContributors() const {#otherContributors}

Returns a list of people that contributed to this plugin (other than the authors and translators).

> **Note:** Getter function for property [otherContributors](kpluginmetadata.md#otherContributors-prop).

### QString KPluginMetaData::pluginId() const {#pluginId}

Returns the unique identifier within the namespace of the plugin

For C++ plugins, this ID is derived from the filename. It should not be set in the metadata explicitly.

When using [KPluginMetaData::fromJsonFile](kpluginmetadata.md#fromJsonFile) or [KPluginMetaData](kpluginmetadata.md)([QJsonObject](https://doc.qt.io/qt-6/qjsonobject.html), [QString](https://doc.qt.io/qt-6/qstring.html)), the "Id" of the "KPlugin" object will be used. If unset, it will be derived from the filename.

> **Note:** Getter function for property [pluginId](kpluginmetadata.md#pluginId-prop).

### QJsonObject KPluginMetaData::rawData() const {#rawData}

Returns the full metadata stored inside the plugin file.

> **Note:** Getter function for property [rawData](kpluginmetadata.md#rawData-prop).

### bool KPluginMetaData::supportsMimeType(const QString &*mimeType*) const {#supportsMimeType}

Returns true if this plugin can handle the given mimetype This is more accurate than [mimeTypes](kpluginmetadata.md#mimeTypes)().contains(mimeType) because it also takes MIME type inheritance into account.

### QList\<KAboutPerson\> KPluginMetaData::translators() const {#translators}

Returns the translator(s) of this plugin.

> **Note:** Getter function for property [translators](kpluginmetadata.md#translators-prop).

### QString KPluginMetaData::value(QStringView *key*, const QString &*defaultValue* = QString()) const {#value}

Returns the string value for `key` from the metadata or `defaultValue` if the key does not exist

if [QString](https://doc.qt.io/qt-6/qstring.html) is not the correct type for `key` you should use the other overloads or [KPluginMetaData::rawData](kpluginmetadata.md#rawData)

### bool KPluginMetaData::value(QStringView *key*, bool *defaultValue*) const {#value-1}

This is an overloaded function.

### QStringList KPluginMetaData::value(QStringView *key*, const QStringList &*defaultValue*) const {#value-2}

Returns the value for `key` from the metadata or `defaultValue` if the key does not exist. If the type of `key` is string, a list containing just that string will be returned. If the type is array, the list will contain one entry for each array member.

This is an overloaded function.

### int KPluginMetaData::value(QStringView *key*, int *defaultValue*) const {#value-3}

This is an overloaded function.

### QString KPluginMetaData::version() const {#version}

Returns the version of the plugin.

> **Note:** Getter function for property [version](kpluginmetadata.md#version-prop).

### QString KPluginMetaData::website() const {#website}

Returns the website of the plugin.

> **Note:** Getter function for property [website](kpluginmetadata.md#website-prop).

### bool KPluginMetaData::operator==(const KPluginMetaData &*other*) const {#operator-eq-eq}

## Related Non-Members {#related-non-members}

### \[since 6.0\] QDebug operator\<\<(QDebug *debug*, const KPluginMetaData &*metaData*) {#operator-lt-lt}

This function was introduced in Qt 6.0.
