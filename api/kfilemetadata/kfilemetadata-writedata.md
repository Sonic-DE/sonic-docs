---
title: "KFileMetaData::WriteData Class"
description: "The WriteData class stores all the data to be written to a file."
---

# KFileMetaData::WriteData Class

The [WriteData](kfilemetadata-writedata.md) class stores all the data to be written to a file. [More...](#details)

- **Header:** `#include <FileMetaData/WriteData>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS FileMetaData)`  
  `target_link_libraries(mytarget PRIVATE KF6::FileMetaData)`

[List of all members, including inherited members](kfilemetadata-writedata-members.md)

## Public Functions

- [WriteData(const QString &url, const QString &mimetype)](#WriteData)
- [void add(KFileMetaData::Property::Property property, const QVariant &value)](#add)
- [void addImageData(const QMap\<KFileMetaData::EmbeddedImageData::ImageType, QByteArray\> &images)](#addImageData)
- [QMap\<KFileMetaData::EmbeddedImageData::ImageType, QByteArray\> imageData() const](#imageData)
- [QString inputMimetype() const](#inputMimetype)
- [QString inputUrl() const](#inputUrl)
- [KFileMetaData::PropertyMultiMap properties() const](#properties)
- [bool WriteData::operator==(const KFileMetaData::WriteData &rhs) const](#operator-eq-eq)

## Detailed Description {#details}

## Member Function Documentation {#member-function-documentation}

### WriteData::WriteData(const QString &*url*, const QString &*mimetype*) {#WriteData}

### void WriteData::add(KFileMetaData::Property::Property *property*, const QVariant &*value*) {#add}

### void WriteData::addImageData(const QMap\<KFileMetaData::EmbeddedImageData::ImageType, QByteArray\> &*images*) {#addImageData}

### QMap\<KFileMetaData::EmbeddedImageData::ImageType, QByteArray\> WriteData::imageData() const {#imageData}

### QString WriteData::inputMimetype() const {#inputMimetype}

### QString WriteData::inputUrl() const {#inputUrl}

### KFileMetaData::PropertyMultiMap WriteData::properties() const {#properties}

### bool WriteData::operator==(const KFileMetaData::WriteData &*rhs*) const {#operator-eq-eq}
