---
title: "KFileMetaData::MimeUtils Namespace"
description: "The MimeUtils namespace."
---

# KFileMetaData::MimeUtils Namespace

The [MimeUtils](kfilemetadata-mimeutils.md) namespace. [More...](#details)

- Header: MimeUtils
- CMake: find\_package(KF6 REQUIRED COMPONENTS FileMetaData) target\_link\_libraries(mytarget PRIVATE KF6::FileMetaData)

## Detailed Description {#details}

## Function Documentation {#function-documentation}

### QMimeType MimeUtils::strictMimeType(const QString &*filePath*, const QMimeDatabase &*db*) {#strictMimeType}

Returns the MIME type for a file

The function uses both content and filename to determine the [QMimeType](https://doc.qt.io/qt-6/qmimetype.html). In case the extension MIME type is more specific than the content MIME type, and the first inherits the latter, the extension MIME type is preferred. If the extension does not match the content, the content has higher priority. The file must exist and be readable.

*See also* [QMimeDatabase::mimeTypesForFileName](https://doc.qt.io/qt-6/qmimedatabase.html#mimeTypesForFileName), [QMimeType::inherits](https://doc.qt.io/qt-6/qmimetype.html#inherits)
