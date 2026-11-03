---
title: "KFileMetaData::PropertyInfo Class"
description: "The PropertyInfo class can be used to obtain extra information about any property."
---

# KFileMetaData::PropertyInfo Class

The [PropertyInfo](kfilemetadata-propertyinfo.md) class can be used to obtain extra information about any property. [More...](#details)

- **Header:** `#include <KFileMetaData/PropertyInfo>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS FileMetaData)`  
  `target_link_libraries(mytarget PRIVATE KF6::FileMetaData)`

[List of all members, including inherited members](kfilemetadata-propertyinfo-members.md)

## Public Functions

- [PropertyInfo()](#PropertyInfo)
- [PropertyInfo(KFileMetaData::Property::Property property)](#PropertyInfo-1)
- [QString displayName() const](#displayName)
- [QString formatAsDisplayString(const QVariant &value) const](#formatAsDisplayString)
- [QString name() const](#name)
- [KFileMetaData::Property::Property property() const](#property)
- [bool shouldBeIndexed() const](#shouldBeIndexed)
- [QMetaType::Type valueType() const](#valueType)
- [bool PropertyInfo::operator==(const KFileMetaData::PropertyInfo &rhs) const](#operator-eq-eq)

## Static Public Members

- [QStringList allNames()](#allNames)
- [KFileMetaData::PropertyInfo fromName(const QString &name)](#fromName)

## Detailed Description {#details}

It is commonly used be indexers in order to obtain a translatable name of the property along with additional information such as if the property should be indexed.

## Member Function Documentation {#member-function-documentation}

### PropertyInfo::PropertyInfo() {#PropertyInfo}

### PropertyInfo::PropertyInfo(KFileMetaData::Property::Property *property*) {#PropertyInfo-1}

### \[static\] QStringList PropertyInfo::allNames() {#allNames}

Get the names of all valid, supported properties

Note: [Property::Empty](kfilemetadata-property.md#Property-enum) is not considered a valid property.

### QString PropertyInfo::displayName() const {#displayName}

A user visible name of the property

Note: When the displayName for a given property is used repeatedly the returned value should be cached, as calling this method is fairly expensive, as the returned name is localized.

### QString PropertyInfo::formatAsDisplayString(const QVariant &*value*) const {#formatAsDisplayString}

Returns the value of the property as a [QString](https://doc.qt.io/qt-6/qstring.html) with added formatting, added units if needed, and translated enums.

### \[static\] KFileMetaData::PropertyInfo PropertyInfo::fromName(const QString &*name*) {#fromName}

Construct a [PropertyInfo](kfilemetadata-propertyinfo.md) from the internal property name. The internal property name is case insensitive

### QString PropertyInfo::name() const {#name}

The internal unique name used to refer to the property

### KFileMetaData::Property::Property PropertyInfo::property() const {#property}

The enumeration which represents this property

### bool PropertyInfo::shouldBeIndexed() const {#shouldBeIndexed}

Indicates if this property requires indexing or should just be stored. Eg - [Property::Height](kfilemetadata-property.md#Property-enum) does not need to be part of the global index. When a user searches for 600, they should not get images with that height

This is just a recommendation.

### QMetaType::Type PropertyInfo::valueType() const {#valueType}

The type the value of this property should be. Eg - [Property::Height](kfilemetadata-property.md#Property-enum) should be an integer

### bool PropertyInfo::operator==(const KFileMetaData::PropertyInfo &*rhs*) const {#operator-eq-eq}
