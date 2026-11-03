---
title: "KFileMetaData::TypeInfo Class"
description: "The TypeInfo class can be used to obtain a rough type classification for a file."
---

# KFileMetaData::TypeInfo Class

The [TypeInfo](kfilemetadata-typeinfo.md) class can be used to obtain a rough type classification for a file. [More...](#details)

- **Header:** `#include <KFileMetaData/TypeInfo>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS FileMetaData)`  
  `target_link_libraries(mytarget PRIVATE KF6::FileMetaData)`

[List of all members, including inherited members](kfilemetadata-typeinfo-members.md)

## Public Functions

- [TypeInfo()](#TypeInfo)
- [TypeInfo(KFileMetaData::Type::Type type)](#TypeInfo-1)
- [QString displayName() const](#displayName)
- [QString name() const](#name)
- [KFileMetaData::Type::Type type() const](#type)
- [bool TypeInfo::operator==(const KFileMetaData::TypeInfo &rhs) const](#operator-eq-eq)

## Static Public Members

- [QStringList allNames()](#allNames)
- [KFileMetaData::TypeInfo fromName(const QString &name)](#fromName)

## Detailed Description {#details}

It is somewhat related to the MIME "\<type\>/\<subtype\>" classification, but provides additional types, e.g. MIME does not provide a generic "Archive" type.

## Member Function Documentation {#member-function-documentation}

### TypeInfo::TypeInfo() {#TypeInfo}

### TypeInfo::TypeInfo(KFileMetaData::Type::Type *type*) {#TypeInfo-1}

### \[static\] QStringList TypeInfo::allNames() {#allNames}

Get all supported property names

### QString TypeInfo::displayName() const {#displayName}

A user visible translated name for this type

### \[static\] KFileMetaData::TypeInfo TypeInfo::fromName(const QString &*name*) {#fromName}

Construct a [TypeInfo](kfilemetadata-typeinfo.md) from the internal type name. The internal type name is case insensitive

### QString TypeInfo::name() const {#name}

An internal unique name for the type

### KFileMetaData::Type::Type TypeInfo::type() const {#type}

The type identifier

### bool TypeInfo::operator==(const KFileMetaData::TypeInfo &*rhs*) const {#operator-eq-eq}
