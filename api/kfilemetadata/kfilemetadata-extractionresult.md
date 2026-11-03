---
title: "KFileMetaData::ExtractionResult Class"
description: "The ExtractionResult class is where all the data extracted by the indexer is saved."
---

# KFileMetaData::ExtractionResult Class

The [ExtractionResult](kfilemetadata-extractionresult.md) class is where all the data extracted by the indexer is saved. [More...](#details)

- **Header:** `#include <KFileMetaData/ExtractionResult>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS FileMetaData)`  
  `target_link_libraries(mytarget PRIVATE KF6::FileMetaData)`
- **Inherited By:** [KFileMetaData::SimpleExtractionResult](kfilemetadata-simpleextractionresult.md)

[List of all members, including inherited members](kfilemetadata-extractionresult-members.md)

## Public Types

- [enum ExtractionResult::Flag](#Flag-enum)

## Public Functions

- [ExtractionResult(const QString &url, const QString &mimetype = QString(), const KFileMetaData::ExtractionResult::Flags &flags = Flags{ExtractPlainText \| ExtractMetaData})](#ExtractionResult)
- [void add(KFileMetaData::Property::Property property, const QVariant &value)](#add)
- [void addImageData(QMap\<KFileMetaData::EmbeddedImageData::ImageType, QByteArray\> &&images)](#addImageData)
- [void addType(KFileMetaData::Type::Type type)](#addType)
- [void append(const QString &text)](#append)
- [QMap\<KFileMetaData::EmbeddedImageData::ImageType, QByteArray\> imageData() const](#imageData)
- [KFileMetaData::ExtractionResult::Flags inputFlags() const](#inputFlags)
- [QString inputMimetype() const](#inputMimetype)
- [QString inputUrl() const](#inputUrl)

## Detailed Description {#details}

This class acts as a base class which should be derived from and then passed to the relevant plugins.

The derived class needs to implement 3 pure virtual functions through which it receives the extracted data.

## Member Type Documentation {#member-type-documentation}

### enum ExtractionResult::Flag {#Flag-enum}

**flags ExtractionResult::Flags**

| Constant |   |
| --- | --- |
| `KFileMetaData::ExtractionResult::ExtractNothing` | `0` |
| `KFileMetaData::ExtractionResult::ExtractMetaData` | `1` |
| `KFileMetaData::ExtractionResult::ExtractPlainText` | `2` |
| `KFileMetaData::ExtractionResult::ExtractImageData (since Qt 5.76)` | `4` |

The `Flags` type is a typedef for `QFlags<Flag>. `It stores an OR combination of `Flag` values.

## Member Function Documentation {#member-function-documentation}

### ExtractionResult::ExtractionResult(const QString &*url*, const QString &*mimetype* = QString(), const KFileMetaData::ExtractionResult::Flags &*flags* = Flags{ExtractPlainText \| ExtractMetaData}) {#ExtractionResult}

Create an [ExtractionResult](kfilemetadata-extractionresult.md) which can be passed be to Extractors. The extractors use the `url`, `mimetype` and `flags` in order to determine which file the data should be extracted from and which data should be extracted.

### \[pure virtual\] void ExtractionResult::add(KFileMetaData::Property::Property *property*, const QVariant &*value*) {#add}

This function is called by the plugins when they wish to add a key value pair which should be indexed. This function may be called multiple times for the same key.

`property` This specifies a property name. It should be one of the properties from the global list of properties.

`value` The value of the property

### void ExtractionResult::addImageData(QMap\<KFileMetaData::EmbeddedImageData::ImageType, QByteArray\> &&*images*) {#addImageData}

This function is called by the plugins.

`images` The images to add

*See also* [EmbeddedImageData](kfilemetadata-embeddedimagedata.md)

### \[pure virtual\] void ExtractionResult::addType(KFileMetaData::Type::Type *type*) {#addType}

This function is called by the plugins.

A type is a higher level classification of the file. A file can have multiple types, but mostly when it does, those types are related. Eg - Document and Presentation.

Please choose one type from the list of available types

### \[pure virtual\] void ExtractionResult::append(const QString &*text*) {#append}

This function is called by plugins when they wish for some plain text to be indexed without any property. This generally corresponds to the text content in a file

### QMap\<KFileMetaData::EmbeddedImageData::ImageType, QByteArray\> ExtractionResult::imageData() const {#imageData}

Return embedded image data

### KFileMetaData::ExtractionResult::Flags ExtractionResult::inputFlags() const {#inputFlags}

The flags which the extraction plugin should considering following when extracting metadata from the file

### QString ExtractionResult::inputMimetype() const {#inputMimetype}

The input MIME type. This MIME type should correspond with the MIME types supported with the relevant plugin when it is being passed to the Extractor, or be a subtype thereof.

*See also* [ExtractorCollection::fetchExtractors](kfilemetadata-extractorcollection.md#fetchExtractors), ExtractorPlugin::supportedMimeType

### QString ExtractionResult::inputUrl() const {#inputUrl}

The input URL which the plugins will use to locate the file
