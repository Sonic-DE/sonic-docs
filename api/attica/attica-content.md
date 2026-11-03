---
title: "Attica::Content Class"
description: "Represents a single content."
---

# Attica::Content Class

Represents a single content. [More...](#details)

- **Header:** `#include <Attica/Content>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS Attica)`  
  `target_link_libraries(mytarget PRIVATE KF6::Attica)`

[List of all members, including inherited members](attica-content-members.md)

## Public Types

- [Content::List](#List-typedef)

## Public Functions

- [Content()](#Content)
- [void addAttribute(const QString &key, const QString &value)](#addAttribute)
- [QString attribute(const QString &key) const](#attribute)
- [QMap\<QString, QString\> attributes() const](#attributes)
- [QString author() const](#author)
- [QString changelog() const](#changelog)
- [QDateTime created() const](#created)
- [QString depend() const](#depend)
- [QString description() const](#description)
- [QUrl detailpage() const](#detailpage)
- [Attica::DownloadDescription downloadUrlDescription(int number) const](#downloadUrlDescription)
- [QList\<Attica::DownloadDescription\> downloadUrlDescriptions() const](#downloadUrlDescriptions)
- [int downloads() const](#downloads)
- [QList\<Attica::HomePageEntry\> homePageEntries()](#homePageEntries)
- [Attica::HomePageEntry homePageEntry(int number) const](#homePageEntry)
- [QList\<Attica::Icon\> icons()](#icons)
- [QList\<Attica::Icon\> icons() const](#icons-1)
- [QString id() const](#id)
- [bool isValid() const](#isValid)
- [QString license() const](#license)
- [QString licenseName() const](#licenseName)
- [QString name() const](#name)
- [int numberOfComments() const](#numberOfComments)
- [QString previewPicture(const QString &number = QStringLiteral("1")) const](#previewPicture)
- [int rating() const](#rating)
- [void setCreated(const QDateTime &created)](#setCreated)
- [void setDownloads(int downloads)](#setDownloads)
- [void setIcons(QList\<Attica::Icon\> icons)](#setIcons)
- [void setId(const QString &id)](#setId)
- [void setName(const QString &name)](#setName)
- [void setNumberOfComments(int numComments)](#setNumberOfComments)
- [void setRating(int rating)](#setRating)
- [void setTags(const QStringList &tags)](#setTags)
- [void setUpdated(const QDateTime &updated)](#setUpdated)
- [void setVideos(QList\<QUrl\> videos)](#setVideos)
- [QString smallPreviewPicture(const QString &number = QStringLiteral("1")) const](#smallPreviewPicture)
- [QString summary() const](#summary)
- [QStringList tags() const](#tags)
- [QDateTime updated() const](#updated)
- [QString version() const](#version)
- [QList\<QUrl\> videos()](#videos)

## Detailed Description {#details}

## Member Type Documentation {#member-type-documentation}

### Content::List {#List-typedef}

## Member Function Documentation {#member-function-documentation}

### Content::Content() {#Content}

Creates an empty Content

### void Content::addAttribute(const QString &*key*, const QString &*value*) {#addAttribute}

Add an attribute that is not included in the basis set of attributes exposed by the Content class. If the attribute already exists it gets overwritten.

`key` the key of the attribute

`value` the value of the attribute

### QString Content::attribute(const QString &*key*) const {#attribute}

Get an attribute that is not included in the basis set of attributes exposed by the Content class.

`key` the key of the attribute

Returns the value of the attribute with the specified key, or an empty string, if the key has not been found

### QMap\<QString, QString\> Content::attributes() const {#attributes}

Get all attributes that are not included in the basis set of attributes exposed by the Content class.

### QString Content::author() const {#author}

### QString Content::changelog() const {#changelog}

### QDateTime Content::created() const {#created}

Returns the date and time the Content has been created.

*See also* [setCreated](attica-content.md#setCreated)()

### QString Content::depend() const {#depend}

### QString Content::description() const {#description}

A description of this content.

### QUrl Content::detailpage() const {#detailpage}

A webpage with the detailed description of this content.

### Attica::DownloadDescription Content::downloadUrlDescription(int *number*) const {#downloadUrlDescription}

Get the details about a download (a content can have multiple links, eg for different distros). This is not very helpful if we don't know the allowed numbers.

### QList\<Attica::DownloadDescription\> Content::downloadUrlDescriptions() const {#downloadUrlDescriptions}

Get all possible downloads. This is slow searching through lots of strings, so beware and don't call it too often.

### int Content::downloads() const {#downloads}

Returns the number of downloads for the Content (how often this has been downloaded from the server).

*See also* [setDownloads](attica-content.md#setDownloads)()

### QList\<Attica::HomePageEntry\> Content::homePageEntries() {#homePageEntries}

Get all home pages for this content. This is slow searching through lots of strings, so beware and don't call it too often.

### Attica::HomePageEntry Content::homePageEntry(int *number*) const {#homePageEntry}

Get the details about a home page (a content can have multiple home pages, blog, bugs, ...). This is not very helpful if we don't know the allowed numbers.

### QList\<Attica::Icon\> Content::icons() {#icons}

Get all icons for this content.

*See also* [setIcons](attica-content.md#setIcons)()

### QList\<Attica::Icon\> Content::icons() const {#icons-1}

Get all icons for this content.

### QString Content::id() const {#id}

Returns the id of the Content.

The id uniquely identifies a Content with the OCS API.

*See also* [setId](attica-content.md#setId)()

### bool Content::isValid() const {#isValid}

Checks whether this Content has an id Returns `true` if an id has been set, `false` otherwise

### QString Content::license() const {#license}

### QString Content::licenseName() const {#licenseName}

### QString Content::name() const {#name}

Returns the name of the Content.

*See also* [setName](attica-content.md#setName)()

### int Content::numberOfComments() const {#numberOfComments}

Returns the number of comments for the Content.

*See also* [setNumberOfComments](attica-content.md#setNumberOfComments)()

### QString Content::previewPicture(const QString &*number* = QStringLiteral("1")) const {#previewPicture}

### int Content::rating() const {#rating}

Returns the rating of the Content, in the range 0-100

*See also* [setRating](attica-content.md#setRating)()

### void Content::setCreated(const QDateTime &*created*) {#setCreated}

Sets the date and time the Content has been created.

`created` the new creation date and time

*See also* [created](attica-content.md#created)()

### void Content::setDownloads(int *downloads*) {#setDownloads}

Sets the number of downloads for the Content.

`downloads` the new number of downloads

*See also* [downloads](attica-content.md#downloads)()

### void Content::setIcons(QList\<Attica::Icon\> *icons*) {#setIcons}

Set list of icons.

`icons` list of icons for this content

*See also* [icons](attica-content.md#icons)()

### void Content::setId(const QString &*id*) {#setId}

Sets the id of the Content.

The id uniquely identifies a Content with the OCS API.

`id` the new id

*See also* [id](attica-content.md#id)()

### void Content::setName(const QString &*name*) {#setName}

Sets the name of the Content.

`name` the new name

*See also* [name](attica-content.md#name)()

### void Content::setNumberOfComments(int *numComments*) {#setNumberOfComments}

Sets the number of comments for the Content.

`numComments` the new number of downloads

*See also* [numberOfComments](attica-content.md#numberOfComments)()

### void Content::setRating(int *rating*) {#setRating}

Sets the rating of the Content.

`rating` the new rating, has to be in the range 0-100

*See also* [rating](attica-content.md#rating)()

### void Content::setTags(const QStringList &*tags*) {#setTags}

Set the list of tags

`tags` list of tags for this content

*See also* [tags](attica-content.md#tags)()

### void Content::setUpdated(const QDateTime &*updated*) {#setUpdated}

Sets the time the Content has been last updated.

`updated` the new date and time of the last update

*See also* [updated](attica-content.md#updated)()

### void Content::setVideos(QList\<QUrl\> *videos*) {#setVideos}

Set list of videos.

`videos` list of videos for this content

*See also* [videos](attica-content.md#videos)()

### QString Content::smallPreviewPicture(const QString &*number* = QStringLiteral("1")) const {#smallPreviewPicture}

### QString Content::summary() const {#summary}

A summary description of this content.

### QStringList Content::tags() const {#tags}

Get all the tags for this content

*See also* [setTags](attica-content.md#setTags)()

### QDateTime Content::updated() const {#updated}

Returns the date and time the Content has been last updated.

*See also* [setUpdated](attica-content.md#setUpdated)()

### QString Content::version() const {#version}

### QList\<QUrl\> Content::videos() {#videos}

Get all videos for this content.

*See also* [setVideos](attica-content.md#setVideos)()
