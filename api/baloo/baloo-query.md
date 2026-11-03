---
title: "Baloo::Query Class"
description: "The Query class is the central class to query to search for files from the Index."
---

# Baloo::Query Class

The Query class is the central class to query to search for files from the Index. [More...](#details)

- **Header:** `#include <Baloo/Query>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS Baloo)`  
  `target_link_libraries(mytarget PRIVATE KF6::Baloo)`

[List of all members, including inherited members](baloo-query-members.md)

## Public Types

- [enum Query::SortingOption](#SortingOption-enum)

## Public Functions

- [Query()](#Query)
- [void addType(const QString &type)](#addType)
- [void addTypes(const QStringList &typeList)](#addTypes)
- [int dayFilter() const](#dayFilter)
- [Baloo::ResultIterator exec()](#exec)
- [QString includeFolder() const](#includeFolder)
- [uint limit() const](#limit)
- [int monthFilter() const](#monthFilter)
- [uint offset() const](#offset)
- [QString searchString() const](#searchString)
- [void setDateFilter(int year, int month = 0, int day = 0)](#setDateFilter)
- [void setIncludeFolder(const QString &folder)](#setIncludeFolder)
- [void setLimit(uint limit)](#setLimit)
- [void setOffset(uint offset)](#setOffset)
- [void setSearchString(const QString &str)](#setSearchString)
- [void setSortingOption(Baloo::Query::SortingOption option)](#setSortingOption)
- [void setType(const QString &type)](#setType)
- [void setTypes(const QStringList &types)](#setTypes)
- [Baloo::Query::SortingOption sortingOption() const](#sortingOption)
- [QByteArray toJSON()](#toJSON)
- [QUrl toSearchUrl(const QString &title = QString())](#toSearchUrl)
- [QStringList types() const](#types)
- [int yearFilter() const](#yearFilter)

## Static Public Members

- [Baloo::Query fromJSON(const QByteArray &arr)](#fromJSON)
- [Baloo::Query fromSearchUrl(const QUrl &url)](#fromSearchUrl)
- [QString titleFromQueryUrl(const QUrl &url)](#titleFromQueryUrl)

## Detailed Description {#details}

This class has an inbuilt parser which recognizes words along with AND / OR and parenthesis and specific properties. This can be used with the [setSearchString](baloo-query.md#setSearchString) method

Examples:

"Fire" -\> Looks for all files which contain the word "Fire"

"Fire OR water" -\> Looks for files which contain either "Fire" or "Water". The capitalization of the words doesn't matter as that will be ignored internally. However, OR and AND have to be in upper case.

"artist:Coldplay" -\> Look for any files with the artist "Coldplay"

"artist:(Coldplay OR Maroon5) power" -\> Look for files with the artist Coldplay or Maroon5 and the word "power"

"artist:'Noah and the Whale'" -\> Look for files with the artist "Noah and the Whale"

"type:Audio title:Fix" -\> Look for Audio files which contains the title "Fix" in its title.

The Query Parser recognizes a large number of properties. These property names can be looked up in KFileMetaData::Property::Property. The type of the file can mentioned with the property 'type' or 'kind'.

## Member Type Documentation {#member-type-documentation}

### enum Query::SortingOption {#SortingOption-enum}

| Constant | Value | Description |
| --- | --- | --- |
| `Baloo::Query::SortNone` | `0` | The results are returned in the most efficient order. They can be returned in any order. |
| `Baloo::Query::SortAuto` | `1` | The results are returned in the order Baloo decides should be ideal. This criteria is based on the mtime of the file. This is the default sorting mechanism. |

## Member Function Documentation {#member-function-documentation}

### Query::Query() {#Query}

### void Query::addType(const QString &*type*) {#addType}

Add a type to the results of the query.

Every file has a higher level type such as "Audio", "Video", "Image", "Document", etc.

Please note that the types are ANDed together. So searching for "Image" and "Video" will probably never return any results. Have a look at KFileMetaData::TypeInfo for a list of type names.

### void Query::addTypes(const QStringList &*typeList*) {#addTypes}

### int Query::dayFilter() const {#dayFilter}

### Baloo::ResultIterator Query::exec() {#exec}

### \[static\] Baloo::Query Query::fromJSON(const QByteArray &*arr*) {#fromJSON}

### \[static\] Baloo::Query Query::fromSearchUrl(const QUrl &*url*) {#fromSearchUrl}

### QString Query::includeFolder() const {#includeFolder}

*See also* [setIncludeFolder](baloo-query.md#setIncludeFolder)()

### uint Query::limit() const {#limit}

*See also* [setLimit](baloo-query.md#setLimit)()

### int Query::monthFilter() const {#monthFilter}

### uint Query::offset() const {#offset}

*See also* [setOffset](baloo-query.md#setOffset)()

### QString Query::searchString() const {#searchString}

*See also* [setSearchString](baloo-query.md#setSearchString)()

### void Query::setDateFilter(int *year*, int *month* = 0, int *day* = 0) {#setDateFilter}

Filter the results in the specified date range.

The year/month/day may be set to 0 in order to ignore it.

### void Query::setIncludeFolder(const QString &*folder*) {#setIncludeFolder}

Only files in this folder will be returned

*See also* [includeFolder](baloo-query.md#includeFolder)()

### void Query::setLimit(uint *limit*) {#setLimit}

Only a maximum of `limit` results will be returned. By default the value is -1

*See also* [limit](baloo-query.md#limit)()

### void Query::setOffset(uint *offset*) {#setOffset}

*See also* [offset](baloo-query.md#offset)()

### void Query::setSearchString(const QString &*str*) {#setSearchString}

Set some text which should be used to search for Items. This contain a single word or an entire sentence.

*See also* [searchString](baloo-query.md#searchString)()

### void Query::setSortingOption(Baloo::Query::SortingOption *option*) {#setSortingOption}

*See also* [sortingOption](baloo-query.md#sortingOption)()

### void Query::setType(const QString &*type*) {#setType}

### void Query::setTypes(const QStringList &*types*) {#setTypes}

*See also* [types](baloo-query.md#types)()

### Baloo::Query::SortingOption Query::sortingOption() const {#sortingOption}

*See also* [setSortingOption](baloo-query.md#setSortingOption)()

### \[static\] QString Query::titleFromQueryUrl(const QUrl &*url*) {#titleFromQueryUrl}

### QByteArray Query::toJSON() {#toJSON}

### QUrl Query::toSearchUrl(const QString &*title* = QString()) {#toSearchUrl}

### QStringList Query::types() const {#types}

*See also* [setTypes](baloo-query.md#setTypes)()

### int Query::yearFilter() const {#yearFilter}
