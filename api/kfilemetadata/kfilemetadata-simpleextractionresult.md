---
title: "KFileMetaData::SimpleExtractionResult Class"
description: "A simple ExtractionResult implementation which stores all the data in memory."
---

# KFileMetaData::SimpleExtractionResult Class

A simple [ExtractionResult](kfilemetadata-extractionresult.md) implementation which stores all the data in memory. [More...](#details)

- **Header:** `#include <KFileMetaData/SimpleExtractionResult>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS FileMetaData)`  
  `target_link_libraries(mytarget PRIVATE KF6::FileMetaData)`
- **Inherits:** [KFileMetaData::ExtractionResult](kfilemetadata-extractionresult.md)

[List of all members, including inherited members](kfilemetadata-simpleextractionresult-members.md)

## Public Functions

- [SimpleExtractionResult(const QString &url, const QString &mimetype = QString(), const KFileMetaData::ExtractionResult::Flags &flags = Flags{ExtractPlainText \| ExtractMetaData})](#SimpleExtractionResult)
- [void add(KFileMetaData::Property::Property property, const QVariant &value)](#add)
- [void addType(KFileMetaData::Type::Type type)](#addType)
- [void append(const QString &text)](#append)
- [KFileMetaData::PropertyMultiMap properties() const](#properties)
- [QString text() const](#text)
- [QList\<KFileMetaData::Type::Type\> types() const](#types)
- [bool SimpleExtractionResult::operator==(const KFileMetaData::SimpleExtractionResult &rhs) const](#operator-eq-eq)

## Detailed Description {#details}

This should ideally not be used in production applications as it holds all of the plain text in memory, and that can get quite large when extracting certain documents.

## Member Function Documentation {#member-function-documentation}

### SimpleExtractionResult::SimpleExtractionResult(const QString &*url*, const QString &*mimetype* = QString(), const KFileMetaData::ExtractionResult::Flags &*flags* = Flags{ExtractPlainText \| ExtractMetaData}) {#SimpleExtractionResult}

### \[override virtual\] void SimpleExtractionResult::add(KFileMetaData::Property::Property *property*, const QVariant &*value*) {#add}

Reimplements: [ExtractionResult::add(KFileMetaData::Property::Property property, const QVariant &value)](kfilemetadata-extractionresult.md#add).

### \[override virtual\] void SimpleExtractionResult::addType(KFileMetaData::Type::Type *type*) {#addType}

Reimplements: [ExtractionResult::addType(KFileMetaData::Type::Type type)](kfilemetadata-extractionresult.md#addType).

### \[override virtual\] void SimpleExtractionResult::append(const QString &*text*) {#append}

Reimplements: [ExtractionResult::append(const QString &text)](kfilemetadata-extractionresult.md#append).

### KFileMetaData::PropertyMultiMap SimpleExtractionResult::properties() const {#properties}

Returns the properties of the extraction result.

### QString SimpleExtractionResult::text() const {#text}

### QList\<KFileMetaData::Type::Type\> SimpleExtractionResult::types() const {#types}

### bool SimpleExtractionResult::operator==(const KFileMetaData::SimpleExtractionResult &*rhs*) const {#operator-eq-eq}
