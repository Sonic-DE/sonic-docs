---
title: "KFileMetaData::UserMetaData Class"
description: "The UserMetaData class can be used to read and set user meta data of files."
---

# KFileMetaData::UserMetaData Class

The [UserMetaData](kfilemetadata-usermetadata.md) class can be used to read and set user meta data of files. [More...](#details)

- **Header:** `#include <KFileMetaData/UserMetaData>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS FileMetaData)`  
  `target_link_libraries(mytarget PRIVATE KF6::FileMetaData)`

[List of all members, including inherited members](kfilemetadata-usermetadata-members.md)  
[Deprecated members](kfilemetadata-usermetadata-obsolete.md)

## Public Types

- [enum UserMetaData::Attribute](#Attribute-enum)
- [enum UserMetaData::Error](#Error-enum)

## Public Functions

- [UserMetaData(const QString &filePath)](#UserMetaData)
- [QString attribute(const QString &name) const](#attribute-1) (since 6.2)
- [QString filePath() const](#filePath)
- [bool hasAttribute(const QString &name) const](#hasAttribute-1) (since 6.2)
- [bool isSupported() const](#isSupported)
- [QString originEmailMessageId() const](#originEmailMessageId)
- [QString originEmailSender() const](#originEmailSender)
- [QString originEmailSubject() const](#originEmailSubject)
- [QUrl originUrl() const](#originUrl)
- [KFileMetaData::UserMetaData::Attributes queryAttributes(KFileMetaData::UserMetaData::Attributes attributes = Attribute::Any) const](#queryAttributes)
- [int rating() const](#rating)
- [KFileMetaData::UserMetaData::Error setAttribute(const QString &name, const QString &value)](#setAttribute)
- [KFileMetaData::UserMetaData::Error setOriginEmailMessageId(const QString &originEmailMessageId)](#setOriginEmailMessageId)
- [KFileMetaData::UserMetaData::Error setOriginEmailSender(const QString &originEmailSender)](#setOriginEmailSender)
- [KFileMetaData::UserMetaData::Error setOriginEmailSubject(const QString &originEmailSubject)](#setOriginEmailSubject)
- [KFileMetaData::UserMetaData::Error setOriginUrl(const QUrl &originUrl)](#setOriginUrl)
- [KFileMetaData::UserMetaData::Error setRating(int rating)](#setRating)
- [KFileMetaData::UserMetaData::Error setTags(const QStringList &tags)](#setTags)
- [KFileMetaData::UserMetaData::Error setUserComment(const QString &userComment)](#setUserComment)
- [QStringList tags() const](#tags)
- [QString userComment() const](#userComment)

## Detailed Description {#details}

## Member Type Documentation {#member-type-documentation}

### enum UserMetaData::Attribute {#Attribute-enum}

**flags UserMetaData::Attributes**

| Constant |   |
| --- | --- |
| `KFileMetaData::UserMetaData::None` | `0x0` |
| `KFileMetaData::UserMetaData::Any` | `None` |
| `KFileMetaData::UserMetaData::Tags` | `0x1` |
| `KFileMetaData::UserMetaData::Rating` | `0x2` |
| `KFileMetaData::UserMetaData::Comment` | `0x4` |
| `KFileMetaData::UserMetaData::OriginUrl` | `0x8` |
| `KFileMetaData::UserMetaData::OriginEmailSubject` | `0x10` |
| `KFileMetaData::UserMetaData::OriginEmailSender` | `0x20` |
| `KFileMetaData::UserMetaData::OriginEmailMessageId` | `0x40` |
| `KFileMetaData::UserMetaData::Other` | `0xffffff80` |
| `KFileMetaData::UserMetaData::All` | `0xffffffff` |

The `Attributes` type is a typedef for `QFlags<Attribute>. `It stores an OR combination of `Attribute` values.

### enum UserMetaData::Error {#Error-enum}

| Constant | Value | Description |
| --- | --- | --- |
| `KFileMetaData::UserMetaData::NoError` | `0` | i.e. Success |
| `KFileMetaData::UserMetaData::UnknownError (since Qt 6.2)` | `1` | An error that's not currently handled specifically |
| `KFileMetaData::UserMetaData::NotSupported (since Qt 6.2)` | `2` | Underlying filesystem does not provide extended attributes features |
| `KFileMetaData::UserMetaData::NoSpace (since Qt 6.2)` | `3` | There is insufficient space remaining to store the extended attribute |
| `KFileMetaData::UserMetaData::MissingPermission (since Qt 6.2)` | `4` | Process doesn't have write permission to the file or the file is marked append-only |
| `KFileMetaData::UserMetaData::ValueTooBig (since Qt 6.2)` | `5` | The value size exceeds the maximum size allowed per-value (64 kB for Linux VFS |
| `KFileMetaData::UserMetaData::NameToolong (since Qt 6.2)` | `6` | The attribute name is too long (255 bytes for Linux VFS) |

## Member Function Documentation {#member-function-documentation}

### UserMetaData::UserMetaData(const QString &*filePath*) {#UserMetaData}

### \[since 6.2\] QString UserMetaData::attribute(const QString &*name*) const {#attribute-1}

This function was introduced in Qt 6.2.

### QString UserMetaData::filePath() const {#filePath}

### \[since 6.2\] bool UserMetaData::hasAttribute(const QString &*name*) const {#hasAttribute-1}

This function was introduced in Qt 6.2.

### bool UserMetaData::isSupported() const {#isSupported}

### QString UserMetaData::originEmailMessageId() const {#originEmailMessageId}

*See also* [setOriginEmailMessageId](kfilemetadata-usermetadata.md#setOriginEmailMessageId)()

### QString UserMetaData::originEmailSender() const {#originEmailSender}

*See also* [setOriginEmailSender](kfilemetadata-usermetadata.md#setOriginEmailSender)()

### QString UserMetaData::originEmailSubject() const {#originEmailSubject}

*See also* [setOriginEmailSubject](kfilemetadata-usermetadata.md#setOriginEmailSubject)()

### QUrl UserMetaData::originUrl() const {#originUrl}

*See also* [setOriginUrl](kfilemetadata-usermetadata.md#setOriginUrl)()

### KFileMetaData::UserMetaData::Attributes UserMetaData::queryAttributes(KFileMetaData::UserMetaData::Attributes *attributes* = Attribute::Any) const {#queryAttributes}

\* Query list of available attributes \* \* Checks for the availability of the given `attributes`. May return \* a superset of the input value when the file has attributes set \* beyond the requested ones. \* \* If the input attribute mask is [Attribute::Any](kfilemetadata-usermetadata.md#Attribute-enum), either [Attribute::None](kfilemetadata-usermetadata.md#Attribute-enum) \* (the file has no user attributes) or [Attribute::All](kfilemetadata-usermetadata.md#Attribute-enum) (the file has at \* least one attribute set) is returned. \* \*

### int UserMetaData::rating() const {#rating}

*See also* [setRating](kfilemetadata-usermetadata.md#setRating)()

### KFileMetaData::UserMetaData::Error UserMetaData::setAttribute(const QString &*name*, const QString &*value*) {#setAttribute}

*See also* [attribute](kfilemetadata-usermetadata.md#attribute-1)()

### KFileMetaData::UserMetaData::Error UserMetaData::setOriginEmailMessageId(const QString &*originEmailMessageId*) {#setOriginEmailMessageId}

*See also* [originEmailMessageId](kfilemetadata-usermetadata.md#originEmailMessageId)()

### KFileMetaData::UserMetaData::Error UserMetaData::setOriginEmailSender(const QString &*originEmailSender*) {#setOriginEmailSender}

*See also* [originEmailSender](kfilemetadata-usermetadata.md#originEmailSender)()

### KFileMetaData::UserMetaData::Error UserMetaData::setOriginEmailSubject(const QString &*originEmailSubject*) {#setOriginEmailSubject}

*See also* [originEmailSubject](kfilemetadata-usermetadata.md#originEmailSubject)()

### KFileMetaData::UserMetaData::Error UserMetaData::setOriginUrl(const QUrl &*originUrl*) {#setOriginUrl}

*See also* [originUrl](kfilemetadata-usermetadata.md#originUrl)()

### KFileMetaData::UserMetaData::Error UserMetaData::setRating(int *rating*) {#setRating}

*See also* [rating](kfilemetadata-usermetadata.md#rating)()

### KFileMetaData::UserMetaData::Error UserMetaData::setTags(const QStringList &*tags*) {#setTags}

*See also* [tags](kfilemetadata-usermetadata.md#tags)()

### KFileMetaData::UserMetaData::Error UserMetaData::setUserComment(const QString &*userComment*) {#setUserComment}

*See also* [userComment](kfilemetadata-usermetadata.md#userComment)()

### QStringList UserMetaData::tags() const {#tags}

*See also* [setTags](kfilemetadata-usermetadata.md#setTags)()

### QString UserMetaData::userComment() const {#userComment}

*See also* [setUserComment](kfilemetadata-usermetadata.md#setUserComment)()
