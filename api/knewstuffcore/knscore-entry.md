---
title: "KNSCore::Entry Class"
description: "KNewStuff data entry container."
---

# KNSCore::Entry Class

KNewStuff data entry container. [More...](#details)

- **Header:** `#include <Entry>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS NewStuff)`  
  `target_link_libraries(mytarget PRIVATE KF6::NewStuff)`

[List of all members, including inherited members](knscore-entry-members.md)

## Public Types

- [enum Entry::EntryEvent](#EntryEvent-enum)
- [enum Entry::EntryType](#EntryType-enum)
- [enum Entry::PreviewType](#PreviewType-enum)
- [enum Entry::Source](#Source-enum)
- [enum Entry::Status](#Status-enum)

## Properties

- [\[read-only\] author : KNSCore::Author](#author-prop)
- [\[read-only\] donationLink : QString](#donationLink-prop)
- [\[read-only\] downloadCount : int](#downloadCount-prop)
- [\[read-only\] downloadLinks : QList\<KNSCore::Entry::DownloadLinkInformation\>](#downloadLinks-prop)
- [\[read-only\] entryType : KNSCore::Entry::EntryType](#entryType-prop)
- [\[read-only\] homepage : QUrl](#homepage-prop)
- [\[read-only\] name : QString](#name-prop)
- [\[read-only\] numberOfComments : int](#numberOfComments-prop)
- [\[read-only\] providerId : QString](#providerId-prop)
- [\[read-only\] rating : int](#rating-prop)
- [\[read-only\] shortSummary : QString](#shortSummary-prop)
- [\[read-only\] status : KNSCore::Entry::Status](#status-prop)
- [\[read-only\] summary : QString](#summary-prop)
- [\[read-only\] uniqueId : QString](#uniqueId-prop)

## Public Functions

- [Entry()](#Entry)
- [~Entry()](#dtor.Entry)
- [void appendDownloadLinkInformation(const KNSCore::Entry::DownloadLinkInformation &info)](#appendDownloadLinkInformation)
- [KNSCore::Author author() const](#author)
- [QString category() const](#category)
- [QString changelog() const](#changelog)
- [void clearDownloadLinkInformation()](#clearDownloadLinkInformation)
- [QString donationLink() const](#donationLink)
- [int downloadCount() const](#downloadCount)
- [int downloadLinkCount() const](#downloadLinkCount)
- [QList\<KNSCore::Entry::DownloadLinkInformation\> downloadLinkInformationList() const](#downloadLinkInformationList)
- [KNSCore::Entry::EntryType entryType() const](#entryType)
- [QUrl homepage() const](#homepage)
- [QStringList installedFiles() const](#installedFiles)
- [QString knowledgebaseLink() const](#knowledgebaseLink)
- [QString license() const](#license)
- [QString name() const](#name)
- [int numberFans() const](#numberFans)
- [int numberKnowledgebaseEntries() const](#numberKnowledgebaseEntries)
- [int numberOfComments() const](#numberOfComments)
- [QString payload() const](#payload)
- [QImage previewImage(KNSCore::Entry::PreviewType type = PreviewSmall1) const](#previewImage)
- [QString previewUrl(KNSCore::Entry::PreviewType type = PreviewSmall1) const](#previewUrl)
- [QString providerId() const](#providerId)
- [int rating() const](#rating)
- [QDate releaseDate() const](#releaseDate)
- [void setAuthor(const KNSCore::Author &author)](#setAuthor)
- [void setCategory(const QString &category)](#setCategory)
- [void setChangelog(const QString &changelog)](#setChangelog)
- [void setDonationLink(const QString &link)](#setDonationLink)
- [void setEntryType(KNSCore::Entry::EntryType type)](#setEntryType)
- [bool setEntryXML(QXmlStreamReader &reader)](#setEntryXML)
- [void setHomepage(const QUrl &page)](#setHomepage)
- [void setInstalledFiles(const QStringList &files)](#setInstalledFiles)
- [void setKnowledgebaseLink(const QString &link)](#setKnowledgebaseLink)
- [void setLicense(const QString &license)](#setLicense)
- [void setName(const QString &name)](#setName)
- [void setNumberFans(int fans)](#setNumberFans)
- [void setNumberKnowledgebaseEntries(int num)](#setNumberKnowledgebaseEntries)
- [void setPayload(const QString &url)](#setPayload)
- [void setPreviewImage(const QImage &image, KNSCore::Entry::PreviewType type = PreviewSmall1)](#setPreviewImage)
- [void setPreviewUrl(const QString &url, KNSCore::Entry::PreviewType type = PreviewSmall1)](#setPreviewUrl)
- [void setProviderId(const QString &id)](#setProviderId)
- [void setReleaseDate(const QDate &releasedate)](#setReleaseDate)
- [void setShortSummary(const QString &summary)](#setShortSummary)
- [void setSource(KNSCore::Entry::Source source)](#setSource)
- [void setStatus(KNSCore::Entry::Status status)](#setStatus)
- [void setSummary(const QString &summary)](#setSummary)
- [void setTags(const QStringList &tags)](#setTags)
- [void setUniqueId(const QString &id)](#setUniqueId)
- [void setUpdateReleaseDate(const QDate &releasedate)](#setUpdateReleaseDate)
- [void setUpdateVersion(const QString &version)](#setUpdateVersion)
- [void setVersion(const QString &version)](#setVersion)
- [QString shortSummary() const](#shortSummary)
- [KNSCore::Entry::Source source() const](#source)
- [KNSCore::Entry::Status status() const](#status)
- [QString summary() const](#summary)
- [QStringList tags() const](#tags)
- [QStringList uninstalledFiles() const](#uninstalledFiles)
- [QString uniqueId() const](#uniqueId)
- [QDate updateReleaseDate() const](#updateReleaseDate)
- [QString updateVersion() const](#updateVersion)
- [QString version() const](#version)

## Detailed Description {#details}

This class provides accessor methods to the data objects as used by KNewStuff.

Maintainer: Jeremy Whiting (jpwhiting@kde.org)

## Member Type Documentation {#member-type-documentation}

### enum Entry::EntryEvent {#EntryEvent-enum}

| Constant | Value | Description |
| --- | --- | --- |
| `KNSCore::Entry::UnknownEvent` | `0` | A generic event, not generally used. |
| `KNSCore::Entry::StatusChangedEvent` | `1` | Used when an event's status is set (use [Entry::status](knscore-entry.md#status)() to get the new status). |
| `KNSCore::Entry::AdoptedEvent` | `2` | Used when an entry has been successfully adopted (use this to determine whether a call to Engine::adoptEntry() succeeded). |
| `KNSCore::Entry::DetailsLoadedEvent` | `3` | Used when more details have been added to an existing entry (such as the full description), and the UI should be updated. |

### enum Entry::EntryType {#EntryType-enum}

Represents whether the current entry is an actual catalog entry, or an entry that represents a set of entries.

| Constant | Value | Description |
| --- | --- | --- |
| `KNSCore::Entry::CatalogEntry` | `0` | These are the main entries that KNewStuff can get the details about and download links for. |
| `KNSCore::Entry::GroupEntry` | `1` | These are entries whose payload is another feed. Currently only used by the OPDS provider. |

### enum Entry::PreviewType {#PreviewType-enum}

Defines the entry's preview image type.

| Constant |   |
| --- | --- |
| `KNSCore::Entry::PreviewSmall1` | `0` |
| `KNSCore::Entry::PreviewSmall2` | `1` |
| `KNSCore::Entry::PreviewSmall3` | `2` |
| `KNSCore::Entry::PreviewBig1` | `3` |
| `KNSCore::Entry::PreviewBig2` | `4` |
| `KNSCore::Entry::PreviewBig3` | `5` |

*See also* [previewImage](knscore-entry.md#previewImage), [previewUrl](knscore-entry.md#previewUrl), [setPreviewImage](knscore-entry.md#setPreviewImage), [setPreviewUrl](knscore-entry.md#setPreviewUrl)

### enum Entry::Source {#Source-enum}

Source of the entry.

An entry's data is coming from either cache, or an online provider. This helps the engine know which data to use when merging cached entries with online entry data.

| Constant |   |
| --- | --- |
| `KNSCore::Entry::Cache` | `0` |
| `KNSCore::Entry::Online` | `1` |
| `KNSCore::Entry::Registry` | `2` |

*See also* [setSource](knscore-entry.md#setSource), [source](knscore-entry.md#source)

### enum Entry::Status {#Status-enum}

Status of the entry.

An entry will be downloadable from the provider's site prior to the download. Once downloaded and installed, it will be either installed or updateable, implying an out-of-date installation. Finally, the entry can be deleted and hence show up as downloadable again.

Entries not taking part in this cycle, for example those in upload, have an invalid status.

| Constant |   |
| --- | --- |
| `KNSCore::Entry::Invalid` | `0` |
| `KNSCore::Entry::Downloadable` | `1` |
| `KNSCore::Entry::Installed` | `2` |
| `KNSCore::Entry::Updateable` | `3` |
| `KNSCore::Entry::Deleted` | `4` |
| `KNSCore::Entry::Installing` | `5` |
| `KNSCore::Entry::Updating` | `6` |

*See also* [setStatus](knscore-entry.md#setStatus), [status](knscore-entry.md#status)

## Property Documentation {#property-documentation}

### \[read-only\] author : KNSCore::Author {#author-prop}

**Access functions:**

- `KNSCore::Author` **[author](knscore-entry.md#author)**() const

### \[read-only\] donationLink : QString {#donationLink-prop}

**Access functions:**

- `QString` **[donationLink](knscore-entry.md#donationLink)**() const

### \[read-only\] downloadCount : int {#downloadCount-prop}

**Access functions:**

- `int` **[downloadCount](knscore-entry.md#downloadCount)**() const

### \[read-only\] downloadLinks : QList\<KNSCore::Entry::DownloadLinkInformation\> {#downloadLinks-prop}

**Access functions:**

- `QList`\<`KNSCore::Entry::DownloadLinkInformation`\> **[downloadLinkInformationList](knscore-entry.md#downloadLinkInformationList)**() const

### \[read-only\] entryType : KNSCore::Entry::EntryType {#entryType-prop}

**Access functions:**

- `KNSCore::Entry::EntryType` **[entryType](knscore-entry.md#entryType)**() const

### \[read-only\] homepage : QUrl {#homepage-prop}

**Access functions:**

- `QUrl` **[homepage](knscore-entry.md#homepage)**() const

### \[read-only\] name : QString {#name-prop}

**Access functions:**

- `QString` **[name](knscore-entry.md#name)**() const

### \[read-only\] numberOfComments : int {#numberOfComments-prop}

**Access functions:**

- `int` **[numberOfComments](knscore-entry.md#numberOfComments)**() const

### \[read-only\] providerId : QString {#providerId-prop}

**Access functions:**

- `QString` **[providerId](knscore-entry.md#providerId)**() const

### \[read-only\] rating : int {#rating-prop}

**Access functions:**

- `int` **[rating](knscore-entry.md#rating)**() const

### \[read-only\] shortSummary : QString {#shortSummary-prop}

**Access functions:**

- `QString` **[shortSummary](knscore-entry.md#shortSummary)**() const

### \[read-only\] status : KNSCore::Entry::Status {#status-prop}

**Access functions:**

- `KNSCore::Entry::Status` **[status](knscore-entry.md#status)**() const

### \[read-only\] summary : QString {#summary-prop}

**Access functions:**

- `QString` **[summary](knscore-entry.md#summary)**() const

### \[read-only\] uniqueId : QString {#uniqueId-prop}

**Access functions:**

- `QString` **[uniqueId](knscore-entry.md#uniqueId)**() const

## Member Function Documentation {#member-function-documentation}

### Entry::Entry() {#Entry}

Constructor.

### \[noexcept\] Entry::~Entry() {#dtor.Entry}

Destructor.

### void Entry::appendDownloadLinkInformation(const KNSCore::Entry::DownloadLinkInformation &*info*) {#appendDownloadLinkInformation}

Adds a new download option to this entry.

`info` is the new download option

*See also* [clearDownloadLinkInformation](knscore-entry.md#clearDownloadLinkInformation), [downloadLinkInformationList](knscore-entry.md#downloadLinkInformationList)

### KNSCore::Author Entry::author() const {#author}

Returns the author of the object.

> **Note:** Getter function for property [author](knscore-entry.md#author-prop).

*See also* [setAuthor](knscore-entry.md#setAuthor)()

### QString Entry::category() const {#category}

Returns the category of the data object. This is the category's name or ID (as opposed to displayName).

*See also* [setCategory](knscore-entry.md#setCategory)(), [KNSCore::Provider::CategoryMetadata](knscore-provider-categorymetadata.md), KNSCore::EngineBase::categories()

### QString Entry::changelog() const {#changelog}

Returns the user written changelog.

*See also* [setChangelog](knscore-entry.md#setChangelog)()

### void Entry::clearDownloadLinkInformation() {#clearDownloadLinkInformation}

Removes all download options from this entry

*See also* [appendDownloadLinkInformation](knscore-entry.md#appendDownloadLinkInformation), [downloadLinkInformationList](knscore-entry.md#downloadLinkInformationList)

### QString Entry::donationLink() const {#donationLink}

Returns a string representing the URL for a website where the user can donate to the author of this entry.

> **Note:** Getter function for property [donationLink](knscore-entry.md#donationLink-prop).

*See also* [setDonationLink](knscore-entry.md#setDonationLink)()

### int Entry::downloadCount() const {#downloadCount}

Returns the download count for the object, which has been determined by its hosting sites and thus might change over time.

> **Note:** Getter function for property [downloadCount](knscore-entry.md#downloadCount-prop).

### int Entry::downloadLinkCount() const {#downloadLinkCount}

Returns the number of available download options for this entry.

*See also* [downloadLinkInformationList](knscore-entry.md#downloadLinkInformationList)

### QList\<KNSCore::Entry::DownloadLinkInformation\> Entry::downloadLinkInformationList() const {#downloadLinkInformationList}

Returns a list of downloadable data for this entry.

> **Note:** Getter function for property [downloadLinks](knscore-entry.md#downloadLinks-prop).

*See also* [appendDownloadLinkInformation](knscore-entry.md#appendDownloadLinkInformation), [DownloadLinkInformation](knscore-entry-downloadlinkinformation.md)

### KNSCore::Entry::EntryType Entry::entryType() const {#entryType}

Returns the entry's type.

> **Note:** Getter function for property [entryType](knscore-entry.md#entryType-prop).

*See also* [setEntryType](knscore-entry.md#setEntryType)()

### QUrl Entry::homepage() const {#homepage}

A link to a website containing information about this entry

Returns The URL representing the entry's website

> **Note:** Getter function for property [homepage](knscore-entry.md#homepage-prop).

*See also* [setHomepage](knscore-entry.md#setHomepage)()

### QStringList Entry::installedFiles() const {#installedFiles}

Returns the locally installed files.

*See also* [setInstalledFiles](knscore-entry.md#setInstalledFiles)()

### QString Entry::knowledgebaseLink() const {#knowledgebaseLink}

Returns the link for the knowledgebase for this entry.

*See also* [setKnowledgebaseLink](knscore-entry.md#setKnowledgebaseLink)()

### QString Entry::license() const {#license}

Returns the license name of the object.

*See also* [setLicense](knscore-entry.md#setLicense)()

### QString Entry::name() const {#name}

Returns the name of the data object (potentially translated).

> **Note:** Getter function for property [name](knscore-entry.md#name-prop).

*See also* [setName](knscore-entry.md#setName)()

### int Entry::numberFans() const {#numberFans}

Returns how many people have marked themselves as fans of this entry.

*See also* [setNumberFans](knscore-entry.md#setNumberFans)(), [KNSCore::EngineBase::becomeFan](knscore-enginebase.md#becomeFan)

### int Entry::numberKnowledgebaseEntries() const {#numberKnowledgebaseEntries}

Returns the number of entries in the knowledgebase for this entry.

*See also* [setNumberKnowledgebaseEntries](knscore-entry.md#setNumberKnowledgebaseEntries)()

### int Entry::numberOfComments() const {#numberOfComments}

Returns the number of comments against the asset.

> **Note:** Getter function for property [numberOfComments](knscore-entry.md#numberOfComments-prop).

### QString Entry::payload() const {#payload}

Returns the object's filename.

*See also* [setPayload](knscore-entry.md#setPayload)()

### QImage Entry::previewImage(KNSCore::Entry::PreviewType *type* = PreviewSmall1) const {#previewImage}

Returns the entry's preview image of the specified type.

`type` is the desired preview image type

> **Note:** This will not be loaded automatically, instead use Engine to load the actual images.

*See also* [setPreviewImage](knscore-entry.md#setPreviewImage)()

### QString Entry::previewUrl(KNSCore::Entry::PreviewType *type* = PreviewSmall1) const {#previewUrl}

Returns the file name of an image containing a preview of the object.

`type` is the desired preview image type

*See also* [setPreviewUrl](knscore-entry.md#setPreviewUrl)()

### QString Entry::providerId() const {#providerId}

Returns the id of the provider this entry belongs to.

> **Note:** Getter function for property [providerId](knscore-entry.md#providerId-prop).

*See also* [setProviderId](knscore-entry.md#setProviderId)()

### int Entry::rating() const {#rating}

Returns the rating for the object, which has been determined by its users and thus might change over time.

> **Note:** Getter function for property [rating](knscore-entry.md#rating-prop).

### QDate Entry::releaseDate() const {#releaseDate}

Returns the object's release date.

*See also* [setReleaseDate](knscore-entry.md#setReleaseDate)()

### void Entry::setAuthor(const KNSCore::Author &*author*) {#setAuthor}

Sets the `author` of the object.

*See also* [author](knscore-entry.md#author)()

### void Entry::setCategory(const QString &*category*) {#setCategory}

Sets the data `category`, e.g. "KWin Scripts" or "Plasma Theme".

*See also* [category](knscore-entry.md#category)()

### void Entry::setChangelog(const QString &*changelog*) {#setChangelog}

Sets the user written `changelog`.

*See also* [changelog](knscore-entry.md#changelog)()

### void Entry::setDonationLink(const QString &*link*) {#setDonationLink}

Sets a string representation of the URL for the donation website for this entry.

> **Note:** This is not checked for validity, the caller must do this.

`link` is the string version of the URL for the entry's donation website

*See also* [donationLink](knscore-entry.md#donationLink)()

### void Entry::setEntryType(KNSCore::Entry::EntryType *type*) {#setEntryType}

Sets the entry's `type`.

*See also* [entryType](knscore-entry.md#entryType)()

### bool Entry::setEntryXML(QXmlStreamReader &*reader*) {#setEntryXML}

Sets the XML for the entry.

This method parses the xml and sets the private members accordingly used to deserialize data loaded from provider.

`reader` defines where to read the XML string from

Returns whether or not setting the values was successful

### void Entry::setHomepage(const QUrl &*page*) {#setHomepage}

Set a link to a website containing information about this entry

`page` The URL representing the entry's website

*See also* [homepage](knscore-entry.md#homepage)()

### void Entry::setInstalledFiles(const QStringList &*files*) {#setInstalledFiles}

Sets the files that have been installed by the install command.

`files` is the list of local file names

*See also* [installedFiles](knscore-entry.md#installedFiles)()

### void Entry::setKnowledgebaseLink(const QString &*link*) {#setKnowledgebaseLink}

Set the link for the knowledgebase.

> **Note:** This is not checked for validity, the caller must do this.

`link` is the string version of the URL for the knowledgebase

*See also* [knowledgebaseLink](knscore-entry.md#knowledgebaseLink)()

### void Entry::setLicense(const QString &*license*) {#setLicense}

Sets the `license` (abbreviation) applicable to the object.

*See also* [license](knscore-entry.md#license)()

### void Entry::setName(const QString &*name*) {#setName}

Sets the `name` for this data object.

*See also* [name](knscore-entry.md#name)()

### void Entry::setNumberFans(int *fans*) {#setNumberFans}

Sets how many people are fans.

> **Note:** This is purely informational. To become a fan, call the KNSCore::Engine::becomeFan function.

`fans` The number of fans this entry has

*See also* [numberFans](knscore-entry.md#numberFans)(), [KNSCore::EngineBase::becomeFan](knscore-enginebase.md#becomeFan)

### void Entry::setNumberKnowledgebaseEntries(int *num*) {#setNumberKnowledgebaseEntries}

Sets the number of knowledgebase entries for this entry.

`num` is the number of entries

*See also* [numberKnowledgebaseEntries](knscore-entry.md#numberKnowledgebaseEntries)()

### void Entry::setPayload(const QString &*url*) {#setPayload}

Sets the object's filename to `url`.

*See also* [payload](knscore-entry.md#payload)()

### void Entry::setPreviewImage(const QImage &*image*, KNSCore::Entry::PreviewType *type* = PreviewSmall1) {#setPreviewImage}

Sets the entry's preview image for the specified preview type.

`image` is the image URL

`type` is the preview image type

*See also* [previewImage](knscore-entry.md#previewImage)()

### void Entry::setPreviewUrl(const QString &*url*, KNSCore::Entry::PreviewType *type* = PreviewSmall1) {#setPreviewUrl}

Sets the object's preview image file, if available.

`url` is the URL of the preview image file

`type` is the preview image type

*See also* [previewUrl](knscore-entry.md#previewUrl)()

### void Entry::setProviderId(const QString &*id*) {#setProviderId}

Sets the `id` of the provider this entry belongs to.

*See also* [providerId](knscore-entry.md#providerId)()

### void Entry::setReleaseDate(const QDate &*releasedate*) {#setReleaseDate}

Sets the release date to `releasedate`.

*See also* [releaseDate](knscore-entry.md#releaseDate)()

### void Entry::setShortSummary(const QString &*summary*) {#setShortSummary}

Sets a short `summary` of what the object is all about (should be very short)

*See also* [shortSummary](knscore-entry.md#shortSummary)()

### void Entry::setSource(KNSCore::Entry::Source *source*) {#setSource}

Sets the `source` of this entry.

*See also* [source](knscore-entry.md#source)()

### void Entry::setStatus(KNSCore::Entry::Status *status*) {#setStatus}

Sets the entry's status. If no status is set, the default will be Invalid.

Note that while this enum is currently found in KNS3::Entry, it will be moved to this class once the binary compatibility lock is lifted for Frameworks 6. For now, you should read any reference to the KNS3::Entry::Status enumerator as [KNSCore::Entry::Status](knscore-entry.md#Status-enum)

`status` New status of the entry

*See also* [status](knscore-entry.md#status)()

### void Entry::setSummary(const QString &*summary*) {#setSummary}

Sets a `summary` (which can potentially be very long)

*See also* [summary](knscore-entry.md#summary)()

### void Entry::setTags(const QStringList &*tags*) {#setTags}

Sets the tags for the content item.

`tags` is a string list containing the tags for this entry

*See also* [tags](knscore-entry.md#tags)()

### void Entry::setUniqueId(const QString &*id*) {#setUniqueId}

Set the object's unique ID. This must be unique to the provider.

`id` The unique ID of this entry as unique to this provider

*See also* [uniqueId](knscore-entry.md#uniqueId)(), [KNSCore::Provider](knscore-provider.md)

### void Entry::setUpdateReleaseDate(const QDate &*releasedate*) {#setUpdateReleaseDate}

Sets the release date that is available as update to `releasedate`.

*See also* [updateReleaseDate](knscore-entry.md#updateReleaseDate)()

### void Entry::setUpdateVersion(const QString &*version*) {#setUpdateVersion}

Sets the `version` number that is available as update.

*See also* [updateVersion](knscore-entry.md#updateVersion)()

### void Entry::setVersion(const QString &*version*) {#setVersion}

Sets the `version` number.

*See also* [version](knscore-entry.md#version)()

### QString Entry::shortSummary() const {#shortSummary}

Returns a short description of what the object is all about (should be very short).

> **Note:** Getter function for property [shortSummary](knscore-entry.md#shortSummary-prop).

*See also* [setShortSummary](knscore-entry.md#setShortSummary)()

### KNSCore::Entry::Source Entry::source() const {#source}

Returns the source of this entry.

*See also* [setSource](knscore-entry.md#setSource)()

### KNSCore::Entry::Status Entry::status() const {#status}

Returns the entry's status.

> **Note:** Getter function for property [status](knscore-entry.md#status-prop).

*See also* [setStatus](knscore-entry.md#setStatus)()

### QString Entry::summary() const {#summary}

Returns a (potentially very long) description of the object.

> **Note:** Getter function for property [summary](knscore-entry.md#summary-prop).

*See also* [setSummary](knscore-entry.md#setSummary)()

### QStringList Entry::tags() const {#tags}

Returns the set of tags assigned specifically to this content item. This does not include tags for the download links. To get those, you must concatenate the lists yourself.

*See also* [setTags](knscore-entry.md#setTags)(), [downloadLinkInformationList](knscore-entry.md#downloadLinkInformationList)(), [KNSCore::Entry::DownloadLinkInformation](knscore-entry-downloadlinkinformation.md), [EngineBase::setTagFilter](knscore-enginebase.md#setTagFilter)

### QStringList Entry::uninstalledFiles() const {#uninstalledFiles}

Returns the locally uninstalled files.

### QString Entry::uniqueId() const {#uniqueId}

Get the object's unique ID. This will be unique to the provider. This is not intended as user-facing information - though it can be useful for certain purposes, this is supposed to only be used for keeping track of the entry.

Returns The unique ID of this entry

> **Note:** Getter function for property [uniqueId](knscore-entry.md#uniqueId-prop).

*See also* [setUniqueId](knscore-entry.md#setUniqueId)()

### QDate Entry::updateReleaseDate() const {#updateReleaseDate}

Returns the date of the newer version that is available as update.

*See also* [setUpdateReleaseDate](knscore-entry.md#setUpdateReleaseDate)()

### QString Entry::updateVersion() const {#updateVersion}

Returns the version string of the object that is available as update.

*See also* [setUpdateVersion](knscore-entry.md#setUpdateVersion)()

### QString Entry::version() const {#version}

Returns the version number string of the object.

*See also* [setVersion](knscore-entry.md#setVersion)()
