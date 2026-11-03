---
title: "Baloo::IndexerConfig Class"
description: "This class allows it to access the current config, to read and modify it."
---

# Baloo::IndexerConfig Class

This class allows it to access the current config, to read and modify it. [More...](#details)

- **Header:** `#include <Baloo/IndexerConfig>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS Baloo)`  
  `target_link_libraries(mytarget PRIVATE KF6::Baloo)`

[List of all members, including inherited members](baloo-indexerconfig-members.md)  
[Deprecated members](baloo-indexerconfig-obsolete.md)

## Public Functions

- [IndexerConfig()](#IndexerConfig)
- [bool canBeSearched(const QString &folder) const](#canBeSearched)
- [QStringList excludeFilters() const](#excludeFilters)
- [QStringList excludeFolders() const](#excludeFolders)
- [QStringList excludeMimetypes() const](#excludeMimetypes)
- [bool fileIndexingEnabled() const](#fileIndexingEnabled)
- [QStringList includeFolders() const](#includeFolders)
- [bool indexHidden() const](#indexHidden)
- [bool onlyBasicIndexing() const](#onlyBasicIndexing)
- [void setExcludeFilters(const QStringList &excludeFilters)](#setExcludeFilters)
- [void setExcludeFolders(const QStringList &excludeFolders)](#setExcludeFolders)
- [void setExcludeMimetypes(const QStringList &excludeMimetypes)](#setExcludeMimetypes)
- [void setFileIndexingEnabled(bool enabled) const](#setFileIndexingEnabled)
- [void setIncludeFolders(const QStringList &includeFolders)](#setIncludeFolders)
- [void setIndexHidden(bool value) const](#setIndexHidden)
- [void setOnlyBasicIndexing(bool value)](#setOnlyBasicIndexing)

## Detailed Description {#details}

It is not meant as a means to infer the current state of the Indexer or the DB. The DB is updated asynchronously, and changes of the config will not be reflected immediately.

## Member Function Documentation {#member-function-documentation}

### IndexerConfig::IndexerConfig() {#IndexerConfig}

### bool IndexerConfig::canBeSearched(const QString &*folder*) const {#canBeSearched}

Check if `folder` can be searched.

`folder` can be searched if itself or one of its descendants is indexed.

Example: if ~/foo is not indexed and ~/foo/bar is indexed then ~/foo can be searched.

Returns `true` if the `folder` can be searched.

### QStringList IndexerConfig::excludeFilters() const {#excludeFilters}

*See also* [setExcludeFilters](baloo-indexerconfig.md#setExcludeFilters)()

### QStringList IndexerConfig::excludeFolders() const {#excludeFolders}

Folders that are excluded from indexing.

(Descendant folders of an excluded folder can be added and they will be indexed.)

*See also* [setExcludeFolders](baloo-indexerconfig.md#setExcludeFolders)()

### QStringList IndexerConfig::excludeMimetypes() const {#excludeMimetypes}

*See also* [setExcludeMimetypes](baloo-indexerconfig.md#setExcludeMimetypes)()

### bool IndexerConfig::fileIndexingEnabled() const {#fileIndexingEnabled}

*See also* [setFileIndexingEnabled](baloo-indexerconfig.md#setFileIndexingEnabled)()

### QStringList IndexerConfig::includeFolders() const {#includeFolders}

Folders to search for files to index and analyze.

*See also* [setIncludeFolders](baloo-indexerconfig.md#setIncludeFolders)()

### bool IndexerConfig::indexHidden() const {#indexHidden}

*See also* [setIndexHidden](baloo-indexerconfig.md#setIndexHidden)()

### bool IndexerConfig::onlyBasicIndexing() const {#onlyBasicIndexing}

*See also* [setOnlyBasicIndexing](baloo-indexerconfig.md#setOnlyBasicIndexing)()

### void IndexerConfig::setExcludeFilters(const QStringList &*excludeFilters*) {#setExcludeFilters}

*See also* [excludeFilters](baloo-indexerconfig.md#excludeFilters)()

### void IndexerConfig::setExcludeFolders(const QStringList &*excludeFolders*) {#setExcludeFolders}

*See also* [excludeFolders](baloo-indexerconfig.md#excludeFolders)()

### void IndexerConfig::setExcludeMimetypes(const QStringList &*excludeMimetypes*) {#setExcludeMimetypes}

*See also* [excludeMimetypes](baloo-indexerconfig.md#excludeMimetypes)()

### void IndexerConfig::setFileIndexingEnabled(bool *enabled*) const {#setFileIndexingEnabled}

*See also* [fileIndexingEnabled](baloo-indexerconfig.md#fileIndexingEnabled)()

### void IndexerConfig::setIncludeFolders(const QStringList &*includeFolders*) {#setIncludeFolders}

*See also* [includeFolders](baloo-indexerconfig.md#includeFolders)()

### void IndexerConfig::setIndexHidden(bool *value*) const {#setIndexHidden}

*See also* [indexHidden](baloo-indexerconfig.md#indexHidden)()

### void IndexerConfig::setOnlyBasicIndexing(bool *value*) {#setOnlyBasicIndexing}

*See also* [onlyBasicIndexing](baloo-indexerconfig.md#onlyBasicIndexing)()
