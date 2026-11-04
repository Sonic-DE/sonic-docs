---
title: "KProtocolInfo::ExtraField Struct"
description: "Network transparent access to files and data."
---

# KProtocolInfo::ExtraField Struct

Network transparent access to files and data. [More...](#details)

- **Header:** `#include <ExtraField>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS KIO)`  
  `target_link_libraries(mytarget PRIVATE KF6::KIOCore)`

[List of all members, including inherited members](kprotocolinfo-extrafield-members.md)

## Public Types

- [enum ExtraField::Type](#Type-enum)

## Detailed Description {#details}

Definition of an extra field in the UDS entries, returned by a listDir operation.

The name is the name of the column, translated.

The type name comes from [QMetaType::name](https://doc.qt.io/qt-6/qmetatype.html#name)() Currently supported types: "[QString](https://doc.qt.io/qt-6/qstring.html)", "[QDateTime](https://doc.qt.io/qt-6/qdatetime.html)" (ISO-8601 format)

## Member Type Documentation {#member-type-documentation}

### enum ExtraField::Type {#Type-enum}

| Constant |   |
| --- | --- |
| `KProtocolInfo::ExtraField::String` | `QMetaType::QString` |
| `KProtocolInfo::ExtraField::DateTime` | `QMetaType::QDateTime` |
| `KProtocolInfo::ExtraField::Invalid` | `QMetaType::UnknownType` |
