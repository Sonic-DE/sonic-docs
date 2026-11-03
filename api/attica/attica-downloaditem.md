---
title: "Attica::DownloadItem Class"
description: "Represents a download item."
---

# Attica::DownloadItem Class

Represents a download item. [More...](#details)

- **Header:** `#include <Attica/DownloadItem>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS Attica)`  
  `target_link_libraries(mytarget PRIVATE KF6::Attica)`

[List of all members, including inherited members](attica-downloaditem-members.md)

## Public Types

- [DownloadItem::List](#List-typedef)

## Public Functions

- [DownloadItem()](#DownloadItem)
- [QString gpgFingerprint() const](#gpgFingerprint)
- [QString gpgSignature() const](#gpgSignature)
- [QString mimeType() const](#mimeType)
- [QString packageName() const](#packageName)
- [QString packageRepository() const](#packageRepository)
- [void setGpgFingerprint(const QString &gpgFingerprint)](#setGpgFingerprint)
- [void setGpgSignature(const QString &gpgSignature)](#setGpgSignature)
- [void setMimeType(const QString &mimeType)](#setMimeType)
- [void setPackageName(const QString &packageName)](#setPackageName)
- [void setPackageRepository(const QString &packageRepository)](#setPackageRepository)
- [void setType(Attica::DownloadDescription::Type type)](#setType)
- [void setUrl(const QUrl &url)](#setUrl)
- [Attica::DownloadDescription::Type type()](#type)
- [QUrl url() const](#url)

## Detailed Description {#details}

## Member Type Documentation {#member-type-documentation}

### DownloadItem::List {#List-typedef}

## Member Function Documentation {#member-function-documentation}

### DownloadItem::DownloadItem() {#DownloadItem}

Creates an empty [DownloadItem](attica-downloaditem.md)

### QString DownloadItem::gpgFingerprint() const {#gpgFingerprint}

*See also* [setGpgFingerprint](attica-downloaditem.md#setGpgFingerprint)()

### QString DownloadItem::gpgSignature() const {#gpgSignature}

*See also* [setGpgSignature](attica-downloaditem.md#setGpgSignature)()

### QString DownloadItem::mimeType() const {#mimeType}

*See also* [setMimeType](attica-downloaditem.md#setMimeType)()

### QString DownloadItem::packageName() const {#packageName}

*See also* [setPackageName](attica-downloaditem.md#setPackageName)()

### QString DownloadItem::packageRepository() const {#packageRepository}

*See also* [setPackageRepository](attica-downloaditem.md#setPackageRepository)()

### void DownloadItem::setGpgFingerprint(const QString &*gpgFingerprint*) {#setGpgFingerprint}

*See also* [gpgFingerprint](attica-downloaditem.md#gpgFingerprint)()

### void DownloadItem::setGpgSignature(const QString &*gpgSignature*) {#setGpgSignature}

*See also* [gpgSignature](attica-downloaditem.md#gpgSignature)()

### void DownloadItem::setMimeType(const QString &*mimeType*) {#setMimeType}

*See also* [mimeType](attica-downloaditem.md#mimeType)()

### void DownloadItem::setPackageName(const QString &*packageName*) {#setPackageName}

*See also* [packageName](attica-downloaditem.md#packageName)()

### void DownloadItem::setPackageRepository(const QString &*packageRepository*) {#setPackageRepository}

*See also* [packageRepository](attica-downloaditem.md#packageRepository)()

### void DownloadItem::setType(Attica::DownloadDescription::Type *type*) {#setType}

*See also* [type](attica-downloaditem.md#type)()

### void DownloadItem::setUrl(const QUrl &*url*) {#setUrl}

*See also* [url](attica-downloaditem.md#url)()

### Attica::DownloadDescription::Type DownloadItem::type() {#type}

*See also* [setType](attica-downloaditem.md#setType)()

### QUrl DownloadItem::url() const {#url}

*See also* [setUrl](attica-downloaditem.md#setUrl)()
