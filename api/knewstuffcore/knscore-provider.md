---
title: "KNSCore::Provider Class"
description: "Base Provider class. This class is deprecated since 6.9. We strongly advise against using it in new code."
---

# KNSCore::Provider Class

Base Provider class. **This class is deprecated since 6.9. We strongly advise against using it in new code.** [More...](#details)

- **Header:** `#include <KNewStuff/Provider>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS NewStuff)`  
  `target_link_libraries(mytarget PRIVATE KF6::NewStuff)`
- **Inherits:** [QObject](https://doc.qt.io/qt-6/qobject.html)
- **Status:** Deprecated since 6.9

[List of all members, including inherited members](knscore-provider-members.md)  
[Deprecated members](knscore-provider-obsolete.md)

## Public Types

- [enum Provider::Filter](#Filter-enum)
- [enum Provider::SortMode](#SortMode-enum)

## Properties

- [contactEmail : QString](#contactEmail-prop)
- [host : QUrl](#host-prop)
- [supportsSsl : bool](#supportsSsl-prop)
- [version : QString](#version-prop)
- [website : QUrl](#website-prop)

## Public Functions

- [Provider()](#Provider)
- [void becomeFan(const KNSCore::Entry &)](#becomeFan)
- [QString contactEmail() const](#contactEmail)
- [QStringList downloadTagFilter() const](#downloadTagFilter)
- [QUrl host() const](#host)
- [QUrl icon() const](#icon)
- [QString id() const](#id)
- [bool isInitialized() const](#isInitialized)
- [void loadBasics()](#loadBasics)
- [void loadComments(const KNSCore::Entry &, int, int)](#loadComments)
- [void loadEntries(const KNSCore::Provider::SearchRequest &request)](#loadEntries)
- [void loadEntryDetails(const KNSCore::Entry &)](#loadEntryDetails)
- [void loadPayloadLink(const KNSCore::Entry &entry, int linkId)](#loadPayloadLink)
- [void loadPerson(const QString &)](#loadPerson)
- [QString name() const](#name)
- [void setCachedEntries(const KNSCore::Entry::List &cachedEntries)](#setCachedEntries)
- [void setContactEmail(const QString &contactEmail)](#setContactEmail)
- [void setDownloadTagFilter(const QStringList &downloadTagFilter)](#setDownloadTagFilter)
- [void setHost(const QUrl &host)](#setHost)
- [bool setProviderXML(const QDomElement &xmldata)](#setProviderXML)
- [void setSupportsSsl(bool supportsSsl)](#setSupportsSsl)
- [void setTagFilter(const QStringList &tagFilter)](#setTagFilter)
- [void setVersion(const QString &version)](#setVersion)
- [void setWebsite(const QUrl &website)](#setWebsite)
- [bool supportsSsl() const](#supportsSsl)
- [QStringList tagFilter() const](#tagFilter)
- [bool userCanBecomeFan()](#userCanBecomeFan)
- [bool userCanVote()](#userCanVote)
- [QString version() const](#version)
- [void vote(const KNSCore::Entry &, uint)](#vote)
- [QUrl website() const](#website)

## Signals

- [void basicsLoaded()](#basicsLoaded)
- [void categoriesMetadataLoded(const QList\<KNSCore::Provider::CategoryMetadata\> &categories)](#categoriesMetadataLoded)
- [void commentsLoaded(const QList\<std::shared\_ptr\<KNSCore::Comment\>\> comments)](#commentsLoaded)
- [void downloadTagFilterChanged()](#downloadTagFilterChanged)
- [void entryDetailsLoaded(const KNSCore::Entry &)](#entryDetailsLoaded)
- [void loadingFailed(const KNSCore::Provider::SearchRequest &)](#loadingFailed)
- [void loadingFinished(const KNSCore::Provider::SearchRequest &, const KNSCore::Entry::List &)](#loadingFinished)
- [void payloadLinkLoaded(const KNSCore::Entry &)](#payloadLinkLoaded)
- [void personLoaded(const std::shared\_ptr\<KNSCore::Author\> author)](#personLoaded)
- [void providerInitialized(KNSCore::Provider \*)](#providerInitialized)
- [void searchPresetsLoaded(const QList\<KNSCore::Provider::SearchPreset\> &presets)](#searchPresetsLoaded)
- [void signalError(const QString &)](#signalError)
- [void signalErrorCode(KNSCore::ErrorCode::ErrorCode errorCode, const QString &message, const QVariant &metadata)](#signalErrorCode)
- [void signalInformation(const QString &)](#signalInformation)
- [void tagFilterChanged()](#tagFilterChanged)

## Protected Functions

- [void setIcon(const QUrl &icon)](#setIcon)
- [void setName(const QString &name)](#setName)

**This class is deprecated since 6.9. We strongly advise against using it in new code.**

## Detailed Description {#details}

This class provides accessors for the provider object.

> **Note:** This class should not be used directly by the application. This class is the base class and will be instantiated for static website providers.

Use ProviderBase to implement providers (only in-tree supported). Use ProviderCore to manage instances of base.

## Member Type Documentation {#member-type-documentation}

### enum Provider::Filter {#Filter-enum}

KNSCore::Provider::Filter

| Constant |   |
| --- | --- |
| `KNSCore::Provider::None` | `0` |
| `KNSCore::Provider::Installed` | `1` |
| `KNSCore::Provider::Updates` | `2` |
| `KNSCore::Provider::ExactEntryId` | `3` |

### enum Provider::SortMode {#SortMode-enum}

| Constant |   |
| --- | --- |
| `KNSCore::Provider::Newest` | `0` |
| `KNSCore::Provider::Alphabetical` | `1` |
| `KNSCore::Provider::Rating` | `2` |
| `KNSCore::Provider::Downloads` | `3` |

## Property Documentation {#property-documentation}

### contactEmail : QString {#contactEmail-prop}

**Access functions:**

- `QString` **[contactEmail](knscore-provider.md#contactEmail)**() const
- `void` **[setContactEmail](knscore-provider.md#setContactEmail)**(const `QString` &*contactEmail*)

**Notifier signal:**

- `void` **[basicsLoaded](knscore-provider.md#basicsLoaded)**()

### host : QUrl {#host-prop}

**Access functions:**

- `QUrl` **[host](knscore-provider.md#host)**() const
- `void` **[setHost](knscore-provider.md#setHost)**(const `QUrl` &*host*)

**Notifier signal:**

- `void` **[basicsLoaded](knscore-provider.md#basicsLoaded)**()

### supportsSsl : bool {#supportsSsl-prop}

**Access functions:**

- `bool` **[supportsSsl](knscore-provider.md#supportsSsl)**() const
- `void` **[setSupportsSsl](knscore-provider.md#setSupportsSsl)**(`bool` *supportsSsl*)

**Notifier signal:**

- `void` **[basicsLoaded](knscore-provider.md#basicsLoaded)**()

### version : QString {#version-prop}

**Access functions:**

- `QString` **[version](knscore-provider.md#version)**() const
- `void` **[setVersion](knscore-provider.md#setVersion)**(const `QString` &*version*)

**Notifier signal:**

- `void` **[basicsLoaded](knscore-provider.md#basicsLoaded)**()

### website : QUrl {#website-prop}

**Access functions:**

- `QUrl` **[website](knscore-provider.md#website)**() const
- `void` **[setWebsite](knscore-provider.md#setWebsite)**(const `QUrl` &*website*)

**Notifier signal:**

- `void` **[basicsLoaded](knscore-provider.md#basicsLoaded)**()

## Member Function Documentation {#member-function-documentation}

### Provider::Provider() {#Provider}

Constructor.

### \[signal\] void Provider::basicsLoaded() {#basicsLoaded}

Fired when the provider's basic information has been fetched and updated

> **Note:** Notifier signal for properties [contactEmail](knscore-provider.md#contactEmail-prop), [host](knscore-provider.md#host-prop), [supportsSsl](knscore-provider.md#supportsSsl-prop), [version](knscore-provider.md#version-prop), and [website](knscore-provider.md#website-prop).

### \[virtual\] void Provider::becomeFan(*const KNSCore::Entry &*) {#becomeFan}

### \[signal\] void Provider::categoriesMetadataLoded(const QList\<KNSCore::Provider::CategoryMetadata\> &*categories*) {#categoriesMetadataLoded}

### \[signal\] void Provider::commentsLoaded(const QList\<std::shared\_ptr\<KNSCore::Comment\>\> *comments*) {#commentsLoaded}

Fired when new comments have been loaded

`comments` The list of newly loaded comments, in a depth-first order

### QString Provider::contactEmail() const {#contactEmail}

Returns The general contact email for this provider.

> **Note:** Getter function for property [contactEmail](knscore-provider.md#contactEmail-prop).

*See also* [setContactEmail](knscore-provider.md#setContactEmail)()

### QStringList Provider::downloadTagFilter() const {#downloadTagFilter}

Returns the tag filter used for downloads by this provider.

*See also* [EngineBase::setDownloadTagFilter](knscore-enginebase.md#setDownloadTagFilter)

### \[signal\] void Provider::downloadTagFilterChanged() {#downloadTagFilterChanged}

### \[signal\] void Provider::entryDetailsLoaded(*const KNSCore::Entry &*) {#entryDetailsLoaded}

### QUrl Provider::host() const {#host}

> **Note:** Getter function for property [host](knscore-provider.md#host-prop).

*See also* [setHost](knscore-provider.md#setHost)()

### \[virtual\] QUrl Provider::icon() const {#icon}

Returns the icon URL for this provider.

*See also* [setIcon](knscore-provider.md#setIcon)()

### \[pure virtual\] QString Provider::id() const {#id}

A unique Id for this provider (the url in most cases)

### \[pure virtual\] bool Provider::isInitialized() const {#isInitialized}

### \[virtual\] void Provider::loadBasics() {#loadBasics}

Request loading of the basic information for this provider. The engine listens to the [basicsLoaded](knscore-provider.md#basicsLoaded)() signal for the result, which is also the signal the respective properties listen to.

This is fired automatically on the first attempt to read one of the properties which contain this basic information, and you will not need to call it as a user of the class (just listen to the properties, which will update when the information has been fetched).

> **Note:** Implementation detail: All subclasses should connect to this signal and point it at a slot which does the actual work, if they support fetching this basic information (if the information is set during construction, you will not need to worry about this).

*See also* [version](knscore-provider.md#version)(), [website](knscore-provider.md#website)(), [host](knscore-provider.md#host)(), [contactEmail](knscore-provider.md#contactEmail)(), [supportsSsl](knscore-provider.md#supportsSsl)()

### \[virtual\] void Provider::loadComments(*const KNSCore::Entry &*, *int*, *int*) {#loadComments}

Request a loading of comments from this provider. The engine listens to the [commentsLoaded](knscore-provider.md#commentsLoaded)() signal for the result

> **Note:** Implementation detail: All subclasses should connect to this signal and point it at a slot which does the actual work, if they support comments.

*See also* [commentsLoaded](knscore-provider.md#commentsLoaded)

### \[pure virtual\] void Provider::loadEntries(const KNSCore::Provider::SearchRequest &*request*) {#loadEntries}

Loads the given search and return given page

`request` defines the search parameters

> **Note:** the engine connects to [loadingFinished](knscore-provider.md#loadingFinished)() signal to get the result

### \[virtual\] void Provider::loadEntryDetails(*const KNSCore::Entry &*) {#loadEntryDetails}

### \[pure virtual\] void Provider::loadPayloadLink(const KNSCore::Entry &*entry*, int *linkId*) {#loadPayloadLink}

### \[virtual\] void Provider::loadPerson(*const QString &*) {#loadPerson}

Request loading of the details for a specific person with the given username. The engine listens to the [personLoaded](knscore-provider.md#personLoaded)() for the result

> **Note:** Implementation detail: All subclasses should connect to this signal and point it at a slot which does the actual work, if they support comments.

### \[signal\] void Provider::loadingFailed(*const KNSCore::Provider::SearchRequest &*) {#loadingFailed}

### \[signal\] void Provider::loadingFinished(*const KNSCore::Provider::SearchRequest &*, *const KNSCore::Entry::List &*) {#loadingFinished}

### \[virtual\] QString Provider::name() const {#name}

Returns the common name of the provider.

*See also* [setName](knscore-provider.md#setName)()

### \[signal\] void Provider::payloadLinkLoaded(*const KNSCore::Entry &*) {#payloadLinkLoaded}

### \[signal\] void Provider::personLoaded(const std::shared\_ptr\<KNSCore::Author\> *author*) {#personLoaded}

Fired when the details of a person have been loaded

`author` The person we've just loaded data for

### \[signal\] void Provider::providerInitialized(*KNSCore::Provider \**) {#providerInitialized}

### \[signal\] void Provider::searchPresetsLoaded(const QList\<KNSCore::Provider::SearchPreset\> &*presets*) {#searchPresetsLoaded}

Fires when the provider has loaded search `presets`. These represent interesting searches for the user, such as recommendations.

### \[pure virtual\] void Provider::setCachedEntries(const KNSCore::Entry::List &*cachedEntries*) {#setCachedEntries}

### void Provider::setContactEmail(const QString &*contactEmail*) {#setContactEmail}

Sets the general contact email address for this provider.

`contactEmail` The general contact email for this provider

> **Note:** Setter function for property [contactEmail](knscore-provider.md#contactEmail-prop).

*See also* [contactEmail](knscore-provider.md#contactEmail)()

### void Provider::setDownloadTagFilter(const QStringList &*downloadTagFilter*) {#setDownloadTagFilter}

Sets the tag filter used for download items by this provider

`downloadTagFilter` The new list of filters

*See also* [downloadTagFilter](knscore-provider.md#downloadTagFilter)(), [EngineBase::setDownloadTagFilter](knscore-enginebase.md#setDownloadTagFilter)

### void Provider::setHost(const QUrl &*host*) {#setHost}

Sets the host used for this provider to `host`.

> **Note:** Setter function for property [host](knscore-provider.md#host-prop).

*See also* [host](knscore-provider.md#host)()

### \[protected\] void Provider::setIcon(const QUrl &*icon*) {#setIcon}

*See also* [icon](knscore-provider.md#icon)()

### \[protected\] void Provider::setName(const QString &*name*) {#setName}

*See also* [name](knscore-provider.md#name)()

### \[pure virtual\] bool Provider::setProviderXML(const QDomElement &*xmldata*) {#setProviderXML}

Sets the provider `xmldata` to initialize the provider. The Provider needs to have it's ID set in this function and cannot change it from there on.

Returns true if successful, or false if the XML data is invalid

### void Provider::setSupportsSsl(bool *supportsSsl*) {#setSupportsSsl}

Sets whether or not the provider supports SSL connections.

`supportsSsl` True if the server supports SSL connections, false if not

> **Note:** Setter function for property [supportsSsl](knscore-provider.md#supportsSsl-prop).

*See also* [supportsSsl](knscore-provider.md#supportsSsl)()

### void Provider::setTagFilter(const QStringList &*tagFilter*) {#setTagFilter}

Sets the tag filter used for entries by this provider.

`tagFilter` The new list of filters

*See also* [tagFilter](knscore-provider.md#tagFilter)(), [EngineBase::setTagFilter](knscore-enginebase.md#setTagFilter)

### void Provider::setVersion(const QString &*version*) {#setVersion}

Sets the `version`.

> **Note:** Setter function for property [version](knscore-provider.md#version-prop).

*See also* [version](knscore-provider.md#version)()

### void Provider::setWebsite(const QUrl &*website*) {#setWebsite}

Sets the `website` URL.

> **Note:** Setter function for property [website](knscore-provider.md#website-prop).

*See also* [website](knscore-provider.md#website)()

### \[signal\] void Provider::signalError(*const QString &*) {#signalError}

### \[signal\] void Provider::signalErrorCode(KNSCore::ErrorCode::ErrorCode *errorCode*, const QString &*message*, const QVariant &*metadata*) {#signalErrorCode}

### \[signal\] void Provider::signalInformation(*const QString &*) {#signalInformation}

### bool Provider::supportsSsl() const {#supportsSsl}

Returns True if the server supports SSL connections, false if not

> **Note:** Getter function for property [supportsSsl](knscore-provider.md#supportsSsl-prop).

*See also* [setSupportsSsl](knscore-provider.md#setSupportsSsl)()

### QStringList Provider::tagFilter() const {#tagFilter}

Returns the tag filter used for downloads by this provider.

*See also* [EngineBase::setTagFilter](knscore-enginebase.md#setTagFilter)

### \[signal\] void Provider::tagFilterChanged() {#tagFilterChanged}

### \[virtual\] bool Provider::userCanBecomeFan() {#userCanBecomeFan}

### \[virtual\] bool Provider::userCanVote() {#userCanVote}

### QString Provider::version() const {#version}

> **Note:** Getter function for property [version](knscore-provider.md#version-prop).

*See also* [setVersion](knscore-provider.md#setVersion)()

### \[virtual\] void Provider::vote(*const KNSCore::Entry &*, *uint*) {#vote}

### QUrl Provider::website() const {#website}

> **Note:** Getter function for property [website](knscore-provider.md#website-prop).

*See also* [setWebsite](knscore-provider.md#setWebsite)()
