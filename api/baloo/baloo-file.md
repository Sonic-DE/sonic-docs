---
title: "Baloo::File Class"
description: "Provides access to all File Metadata."
---

# Baloo::File Class

Provides access to all File Metadata. [More...](#details)

- **Header:** `#include <Baloo/File>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS Baloo)`  
  `target_link_libraries(mytarget PRIVATE KF6::Baloo)`

[List of all members, including inherited members](baloo-file-members.md)

## Public Functions

- [File()](#File)
- [File(const QString &url)](#File-1)
- [bool load()](#load)
- [bool load(const QString &url)](#load-1)
- [QString path() const](#path)
- [KFileMetaData::PropertyMultiMap properties() const](#properties)
- [QVariant property(KFileMetaData::Property::Property property) const](#property)

## Detailed Description {#details}

The File class acts as a temporary container for all the file metadata.

## Member Function Documentation {#member-function-documentation}

### File::File() {#File}

### File::File(const QString &*url*) {#File-1}

Constructor

`url` the local url of the file

### bool File::load() {#load}

### bool File::load(const QString &*url*) {#load-1}

### QString File::path() const {#path}

The local url of the file

### KFileMetaData::PropertyMultiMap File::properties() const {#properties}

Gives a variant map of the properties that have been extracted from the file by the indexer

### QVariant File::property(KFileMetaData::Property::Property *property*) const {#property}
