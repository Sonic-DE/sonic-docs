---
title: "KFileMetaData::Type Namespace"
description: "Library for extracting the text and metadata from a number of different files."
---

# KFileMetaData::Type Namespace

Library for extracting the text and metadata from a number of different files. [More...](#details)

- Header: Type
- CMake: find\_package(KF6 REQUIRED COMPONENTS FileMetaData) target\_link\_libraries(mytarget PRIVATE KF6::FileMetaData)

## Detailed Description {#details}

The Type namespace

## Type Documentation {#type-documentation}

### enum Type::Type {#Type-enum}

A Type represents a way to represent a way to group files based on a higher level view, which the user generally expects.

Every extractor provides a list of types applicable for each file.

| Constant | Value |   |
| --- | --- | --- |
| `KFileMetaData::Type::Empty` | `0` |   |
| `KFileMetaData::Type::Archive` | `1` | A file which contains a compressed collection of other files, e.g. tar, zip, rar, gz. File types which use e.g. zip as an implementation detail - Java JAR files, OpenDocument formats, etc. - are not treated as Archive |
| `KFileMetaData::Type::Audio` | `2` | Used to mark any file which just contains audio. Do not use this type if the file also contains Video |
| `KFileMetaData::Type::Video` | `3` | Any file which contains Video. It may also contain Audio |
| `KFileMetaData::Type::Image` | `4` | Any Image file. This includes both raster and vector formats |
| `KFileMetaData::Type::Document` | `5` | Any file which counts as a document. Documents are generally files which contain rich text, formatting and maybe images, but also just plain text |
| `KFileMetaData::Type::Spreadsheet` | `6` | A SpreadSheet file. This is a specialization of the Document type. Any file which has this type should also have the Document type |
| `KFileMetaData::Type::Presentation` | `7` | A Presentation file. This is a specialization of the Document type. Any file which has this type should also have the Document type |
| `KFileMetaData::Type::Text` | `8` | Any file which contains text data (i.e. not binary data) counts as a Text file. As this also includes various file types which contain data collections (e.g. csv, json) or code (e.g. QML, Makefile), "Document" is typically the more appropriate type |
| `KFileMetaData::Type::Folder` | `9` | A directory or folder |
