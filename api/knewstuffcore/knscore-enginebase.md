---
title: "KNSCore::EngineBase Class"
description: "KNewStuff engine."
---

# KNSCore::EngineBase Class

KNewStuff engine. [More...](#details)

- **Header:** `#include <EngineBase>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS NewStuff)`  
  `target_link_libraries(mytarget PRIVATE KF6::NewStuff)`
- **Inherits:** [QObject](https://doc.qt.io/qt-6/qobject.html)

[List of all members, including inherited members](knscore-enginebase-members.md)  
[Deprecated members](knscore-enginebase-obsolete.md)

## Public Types

- [\[since 6.1\] enum EngineBase::ContentWarningType](#ContentWarningType-enum)

## Properties

- [\[read-only\] contentWarningType : ContentWarningType](#contentWarningType-prop)
- [\[read-only\] providerIDs : QStringList](#providerIDs-prop)
- [\[read-only\] uploadEnabled : bool](#uploadEnabled-prop)
- [\[read-only\] useLabel : QString](#useLabel-prop)

## Public Functions

- [EngineBase(QObject \*parent = nullptr)](#EngineBase)
- [void addDownloadTagFilter(const QString &filter)](#addDownloadTagFilter)
- [void addTagFilter(const QString &filter)](#addTagFilter)
- [QList\<Attica::Provider \*\> atticaProviders() const](#atticaProviders)
- [void becomeFan(const KNSCore::Entry &entry)](#becomeFan)
- [QStringList categories() const](#categories)
- [QList\<KNSCore::CategoryMetadata\> categoriesMetadata2()](#categoriesMetadata2)
- [KNSCore::EngineBase::ContentWarningType contentWarningType() const](#contentWarningType) (since 6.1)
- [QStringList downloadTagFilter() const](#downloadTagFilter)
- [bool hasAdoptionCommand() const](#hasAdoptionCommand)
- [bool init(const QString &configfile)](#init)
- [QString name() const](#name)
- [QStringList providerIDs() const](#providerIDs)
- [QList\<KNSCore::SearchPreset\> searchPresets2()](#searchPresets2) (since 6.9)
- [void setDownloadTagFilter(const QStringList &filter)](#setDownloadTagFilter)
- [void setTagFilter(const QStringList &filter)](#setTagFilter)
- [QStringList tagFilter() const](#tagFilter)
- [bool uploadEnabled() const](#uploadEnabled)
- [QString useLabel() const](#useLabel)
- [bool userCanBecomeFan(const KNSCore::Entry &entry)](#userCanBecomeFan)
- [bool userCanVote(const KNSCore::Entry &entry)](#userCanVote)
- [void vote(const KNSCore::Entry &entry, uint rating)](#vote)

## Signals

- [void contentWarningTypeChanged()](#contentWarningTypeChanged) (since 6.1)
- [void loadingProvider()](#loadingProvider)
- [void providerAdded(KNSCore::ProviderCore \*provider)](#providerAdded)
- [void signalCategoriesMetadataLoaded(const QList\<KNSCore::CategoryMetadata\> &categories)](#signalCategoriesMetadataLoaded)
- [void signalErrorCode(KNSCore::ErrorCode::ErrorCode errorCode, const QString &message, const QVariant &metadata)](#signalErrorCode)
- [void signalMessage(const QString &message)](#signalMessage)
- [void signalSearchPresetsLoaded(const QList\<KNSCore::SearchPreset\> &presets)](#signalSearchPresetsLoaded-1) (since 6.9)
- [void uploadEnabledChanged()](#uploadEnabledChanged)
- [void useLabelChanged()](#useLabelChanged)

## Static Public Members

- [QStringList availableConfigFiles()](#availableConfigFiles)

## Detailed Description {#details}

An engine keeps track of data which is available locally and remote and offers high-level synchronization calls as well as upload and download primitives using an underlying GHNS protocol.

This is a base class for different engine implementations

## Member Type Documentation {#member-type-documentation}

### \[since 6.1\] enum EngineBase::ContentWarningType {#ContentWarningType-enum}

The ContentWarningType enum

| Constant | Value | Description |
| --- | --- | --- |
| `KNSCore::EngineBase::ContentWarningType::Static` | `0` | Content consists of static assets only. Installation should not pose a security risk. |
| `KNSCore::EngineBase::ContentWarningType::Executables` | `1` | Content may contain scripts or other executable code. Users should be warned to treat it like any other program. |

This enum was introduced in Qt 6.1.

## Property Documentation {#property-documentation}

### \[read-only\] contentWarningType : ContentWarningType {#contentWarningType-prop}

**Access functions:**

- `KNSCore::EngineBase::ContentWarningType` **[contentWarningType](knscore-enginebase.md#contentWarningType)**() const

**Notifier signal:**

- `void` **[contentWarningTypeChanged](knscore-enginebase.md#contentWarningTypeChanged)**()

### \[read-only\] providerIDs : QStringList {#providerIDs-prop}

**Access functions:**

- `QStringList` **[providerIDs](knscore-enginebase.md#providerIDs)**() const

### \[read-only\] uploadEnabled : bool {#uploadEnabled-prop}

Whether or not the configuration says that the providers are expected to support uploading. As it stands, this is used to determine whether or not to show the Upload... action where that is displayed (primarily NewStuff.Page).

**Access functions:**

- `bool` **[uploadEnabled](knscore-enginebase.md#uploadEnabled)**() const

**Notifier signal:**

- `void` **[uploadEnabledChanged](knscore-enginebase.md#uploadEnabledChanged)**()

### \[read-only\] useLabel : QString {#useLabel-prop}

Text that should be displayed for the adoption button, this defaults to "Use"

**Access functions:**

- `QString` **[useLabel](knscore-enginebase.md#useLabel)**() const

**Notifier signal:**

- `void` **[useLabelChanged](knscore-enginebase.md#useLabelChanged)**()

## Member Function Documentation {#member-function-documentation}

### EngineBase::EngineBase(QObject \**parent* = nullptr) {#EngineBase}

### void EngineBase::addDownloadTagFilter(const QString &*filter*) {#addDownloadTagFilter}

Add a single filter entry to the download tag filter. The filter should be in the same form as the filter lines in the list used by setDownloadsTagFilter([QStringList](https://doc.qt.io/qt-6/qstringlist.html))

`filter` The filter in the form of a string

*See also* [setTagFilter](knscore-enginebase.md#setTagFilter), [setDownloadTagFilter](knscore-enginebase.md#setDownloadTagFilter)

### void EngineBase::addTagFilter(const QString &*filter*) {#addTagFilter}

Adds a single filter entry to the entry tag filter. The filter should be in the same form as the filter lines in the list used by [setTagFilter](knscore-enginebase.md#setTagFilter)([QStringList](https://doc.qt.io/qt-6/qstringlist.html))

`filter` The filter in the form of a string

*See also* [setTagFilter](knscore-enginebase.md#setTagFilter)

### QList\<Attica::Provider \*\> EngineBase::atticaProviders() const {#atticaProviders}

Returns the list of attica (OCS) providers this engine is connected to

### \[static\] QStringList EngineBase::availableConfigFiles() {#availableConfigFiles}

List of all available config files. This list will contain no duplicated filenames. The returned file paths are absolute.

### void EngineBase::becomeFan(const KNSCore::Entry &*entry*) {#becomeFan}

This will mark the user who is currently authenticated as a fan of the entry passed to the function.

`entry` The entry the user wants to be a fan of

### QStringList EngineBase::categories() const {#categories}

The list of the server-side names of the categories handled by this engine instance. This corresponds directly to the list of categories in your knsrc file. This is not supposed to be used as user-facing strings - see categoriesMetadata() for that.

Returns The categories which this instance of Engine handles

### QList\<KNSCore::CategoryMetadata\> EngineBase::categoriesMetadata2() {#categoriesMetadata2}

The list of metadata for the categories handled by this engine instance. If you wish to show the categories to the user, this is the data to use. The category name is the string used to set categories for the filter, and also what is returned by both [categories](knscore-enginebase.md#categories)() and categoriesFilter(). The human-readable name is displayName, and the only thing which should be shown to the user.

Returns The metadata for all categories handled by this engine

### \[since 6.1\] KNSCore::EngineBase::ContentWarningType EngineBase::contentWarningType() const {#contentWarningType}

The level of warning that should be presented to the user

> **Note:** Getter function for property [contentWarningType](knscore-enginebase.md#contentWarningType-prop).

This function was introduced in Qt 6.1.

*See also* [ContentWarningType](knscore-enginebase.md#ContentWarningType-enum)

### \[signal, since 6.1\] void EngineBase::contentWarningTypeChanged() {#contentWarningTypeChanged}

Emitted after the initial config load

> **Note:** Notifier signal for property [contentWarningType](knscore-enginebase.md#contentWarningType-prop).

This function was introduced in Qt 6.1.

### QStringList EngineBase::downloadTagFilter() const {#downloadTagFilter}

Returns the current downloadlink tag filter list

*See also* [setDownloadTagFilter](knscore-enginebase.md#setDownloadTagFilter)

### bool EngineBase::hasAdoptionCommand() const {#hasAdoptionCommand}

Whether or not an adoption command exists for this engine

Returns True if an adoption command exists

### \[virtual\] bool EngineBase::init(const QString &*configfile*) {#init}

Initializes the engine. This step is application-specific and relies on an external configuration file, which determines all the details about the initialization.

`configfile` KNewStuff2 configuration file (\*.knsrc)

Returns **true** if any valid configuration was found, **false** otherwise

### \[signal\] void EngineBase::loadingProvider() {#loadingProvider}

### QString EngineBase::name() const {#name}

The name as defined by the knsrc file Returns The name associated with the engine's configuration file

### \[signal\] void EngineBase::providerAdded(KNSCore::ProviderCore \**provider*) {#providerAdded}

### QStringList EngineBase::providerIDs() const {#providerIDs}

The IDs of all providers known by this engine. Use this in combination with provider(const [QString](https://doc.qt.io/qt-6/qstring.html)&) to iterate over all providers. Returns The string IDs of all known providers

> **Note:** Getter function for property [providerIDs](knscore-enginebase.md#providerIDs-prop).

### \[since 6.9\] QList\<KNSCore::SearchPreset\> EngineBase::searchPresets2() {#searchPresets2}

This function was introduced in Qt 6.9.

### void EngineBase::setDownloadTagFilter(const QStringList &*filter*) {#setDownloadTagFilter}

Sets a filter to be applied to the downloads for an entry. The logic is the same as used in [setTagFilter](knscore-enginebase.md#setTagFilter)([QStringList](https://doc.qt.io/qt-6/qstringlist.html)), but vitally, only one downloadlink is required to match the filter for the list to be valid. If you do not wish to show the others in your client, you must hide them yourself.

For an entry to be accepted when a download tag filter is set, it must also be accepted by the entry filter (so, for example, while a list of downloads might be accepted, if the entry has ghns\_excluded set, and the default entry filter is set, the entry will still be filtered out).

In your knsrc file, set DownloadTagFilter to the filter you wish to apply, using the same logic as described for the entry tagfilter.

`filter` The filter in the form of a list of strings

*See also* [downloadTagFilter](knscore-enginebase.md#downloadTagFilter)(), [setTagFilter](knscore-enginebase.md#setTagFilter)

### void EngineBase::setTagFilter(const QStringList &*filter*) {#setTagFilter}

Set a filter for results, which filters out all entries which do not match the filter, as applied to the tags for the entry. This filters only on the tags specified for the entry itself. To filter the downloadlinks, use [setDownloadTagFilter](knscore-enginebase.md#setDownloadTagFilter)([QStringList](https://doc.qt.io/qt-6/qstringlist.html)).

> **Note:** The default filter if one is not set from your knsrc file will filter out entries marked as ghns\_excluded=1. To retain this when setting a custom filter, add "ghns\_excluded!=1" as one of the filters.

> **Note:** Some tags provided by OCS do not supply a value (and are simply passed as a key). These will be interpreted as having the value 1 for filtering purposes. An example of this might be ghns\_excluded, which in reality will generally be passed through ocs as "ghns\_excluded" rather than "ghns\_excluded=1"

> **Note:** As tags are metadata, they are provided in the form of adjectives. They are never supplied as action verbs or instructions (as an example, a good tag to suggest that for example a wallpaper is painted would be "painted" as opposed to "paint", and another example might be that an item should be "excluded" as opposed to "exclude").

== Examples of use == Value for tag "tagname" must be exactly "tagdata": tagname==tagdata

Value for tag "tagname" must be different from "tagdata": tagname!=tagdata

== KNSRC entry == A tag filter line in a .knsrc file, which is a comma separated list of tag/value pairs, might look like:

TagFilter=ghns\_excluded!=1,data\#\#mimetype==application/cbr+zip,data\#\#mimetype==application/cbr+rar which would honour the exclusion and filter out anything that does not include a comic book archive in either zip or rar format in one or more of the download items. Notice in particular that there are two data\#\#mimetype entries. Use this for when a tag may have multiple values.

TagFilter=application\#\#architecture==x86\_64 which would not honour the exclusion, and would filter out all entries which do not mark themselves as having a 64bit application binary in at least one download item.

The value does not current support wildcards. The list should be considered a binary AND operation (that is, all filter entries must match for the data entry to be included in the return data)

`filter` The filter in the form of a list of strings

*See also* [tagFilter](knscore-enginebase.md#tagFilter)(), [setDownloadTagFilter](knscore-enginebase.md#setDownloadTagFilter)

### \[signal\] void EngineBase::signalCategoriesMetadataLoaded(const QList\<KNSCore::CategoryMetadata\> &*categories*) {#signalCategoriesMetadataLoaded}

### \[signal\] void EngineBase::signalErrorCode(KNSCore::ErrorCode::ErrorCode *errorCode*, const QString &*message*, const QVariant &*metadata*) {#signalErrorCode}

Fires in the case of any critical or serious errors, such as network or API problems.

`errorCode` Represents the specific type of error which has occurred

`message` A human-readable message which can be shown to the end user

`metadata` Any additional data which might be helpful to further work out the details of the error (see KNSCore::Entry::ErrorCode for the metadata details)

*See also* [KNSCore::ErrorCode](knscore-errorcode.md)

### \[signal\] void EngineBase::signalMessage(const QString &*message*) {#signalMessage}

Indicates a `message` to be added to the ui's log, or sent to a messagebox

### \[signal, since 6.9\] void EngineBase::signalSearchPresetsLoaded(const QList\<KNSCore::SearchPreset\> &*presets*) {#signalSearchPresetsLoaded-1}

Fires when the engine has loaded search presets. These represent interesting searches for the user, such as recommendations.

> **Note:** This signal is overloaded. To connect to this signal:
>
> ```
> // Connect using qOverload:
> connect(engineBase, qOverload<const QList<KNSCore::SearchPreset> &>(&EngineBase::signalSearchPresetsLoaded),
>         receiver, &ReceiverClass::slot);
>
> // Or using a lambda:
> connect(engineBase, qOverload<const QList<KNSCore::SearchPreset> &>(&EngineBase::signalSearchPresetsLoaded),
>         this, [](const QList<KNSCore::SearchPreset> &presets) { /* handle signalSearchPresetsLoaded */ });
> ```
>
> For more examples and approaches, see [connecting to overloaded signals](https://doc.qt.io/qt-6/signalsandslots.html#connecting-overloaded-signals).

This function was introduced in Qt 6.9.

### QStringList EngineBase::tagFilter() const {#tagFilter}

Returns the current tag filter list

*See also* [setTagFilter](knscore-enginebase.md#setTagFilter)

### bool EngineBase::uploadEnabled() const {#uploadEnabled}

Whether or not the configuration says that the providers are expected to support uploading. Returns True if the providers are expected to support uploading

> **Note:** Getter function for property [uploadEnabled](knscore-enginebase.md#uploadEnabled-prop).

### \[signal\] void EngineBase::uploadEnabledChanged() {#uploadEnabledChanged}

Fired when the [uploadEnabled](knscore-enginebase.md#uploadEnabled) property changes

> **Note:** Notifier signal for property [uploadEnabled](knscore-enginebase.md#uploadEnabled-prop).

### QString EngineBase::useLabel() const {#useLabel}

Text that should be displayed for the adoption button, this defaults to i18n("Use")

> **Note:** Getter function for property [useLabel](knscore-enginebase.md#useLabel-prop).

### \[signal\] void EngineBase::useLabelChanged() {#useLabelChanged}

Signal gets emitted when the [useLabel](knscore-enginebase.md#useLabel) property changes

> **Note:** Notifier signal for property [useLabel](knscore-enginebase.md#useLabel-prop).

### bool EngineBase::userCanBecomeFan(const KNSCore::Entry &*entry*) {#userCanBecomeFan}

Whether or not the user is allowed to become a fan of a particular entry. Not all providers (and consequently entries) support the fan functionality and you can use this function to determine this ability.

`entry` The entry the user might wish to be a fan of

Returns Whether or not it is possible for the user to become a fan of that entry

### bool EngineBase::userCanVote(const KNSCore::Entry &*entry*) {#userCanVote}

Whether or not a user is able to vote on the passed entry.

`entry` The entry to check votability on

Returns True if the user is able to vote on the entry

### void EngineBase::vote(const KNSCore::Entry &*entry*, uint *rating*) {#vote}

Cast a vote on the passed entry.

`entry` The entry to vote on

`rating` A number from 0 to 100, 50 being neutral, 0 being most negative and 100 being most positive.
