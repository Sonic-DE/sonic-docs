---
title: "KFileMetaData Namespace"
description: "Library for extracting the text and metadata from a number of different files."
---

# KFileMetaData Namespace

Library for extracting the text and metadata from a number of different files. [More...](#details)

- Header: KFileMetaData/Types
- CMake: find\_package(KF6 REQUIRED COMPONENTS FileMetaData) target\_link\_libraries(mytarget PRIVATE KF6::FileMetaData)

## Detailed Description {#details}

The [KFileMetaData](kfilemetadata-module.md) namespace

## Namespaces {#namespaces}

### namespace KFileMetaData::MimeUtils

### namespace KFileMetaData::Property

### namespace KFileMetaData::Type

The Type namespace

## Classes {#classes}

### class [EmbeddedImageData](kfilemetadata-embeddedimagedata.md)

[EmbeddedImageData](kfilemetadata-embeddedimagedata.md) defines enums for different image types that can be extracted from the metadata of e.g. music files.

### class [ExtractionResult](kfilemetadata-extractionresult.md)

The [ExtractionResult](kfilemetadata-extractionresult.md) class is where all the data extracted by the indexer is saved.

### class [Extractor](kfilemetadata-extractor.md)

The Extractor class is used to extract data from a file.

### class [ExtractorCollection](kfilemetadata-extractorcollection.md)

The [ExtractorCollection](kfilemetadata-extractorcollection.md) is a helper class which internally loads all the extractor plugins.

### class [ExtractorPlugin](kfilemetadata-extractorplugin.md)

The [ExtractorPlugin](kfilemetadata-extractorplugin.md) is the base class for all file metadata extractors.

### class [PropertyInfo](kfilemetadata-propertyinfo.md)

The [PropertyInfo](kfilemetadata-propertyinfo.md) class can be used to obtain extra information about any property.

### class [SimpleExtractionResult](kfilemetadata-simpleextractionresult.md)

A simple [ExtractionResult](kfilemetadata-extractionresult.md) implementation which stores all the data in memory.

### class [TypeInfo](kfilemetadata-typeinfo.md)

The [TypeInfo](kfilemetadata-typeinfo.md) class can be used to obtain a rough type classification for a file.

### class [UserMetaData](kfilemetadata-usermetadata.md)

The [UserMetaData](kfilemetadata-usermetadata.md) class can be used to read and set user meta data of files.

### class [WriteData](kfilemetadata-writedata.md)

The [WriteData](kfilemetadata-writedata.md) class stores all the data to be written to a file.

### class [Writer](kfilemetadata-writer.md)

The Writer class is used to write data to a file.

### class [WriterCollection](kfilemetadata-writercollection.md)

The [WriterCollection](kfilemetadata-writercollection.md) is a helper class which internally loads all the writer plugins.

### class [WriterPlugin](kfilemetadata-writerplugin.md)

The [WriterPlugin](kfilemetadata-writerplugin.md) is the base class for all file metadata writers.
