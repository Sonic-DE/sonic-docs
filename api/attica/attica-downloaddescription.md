---
title: "Attica::DownloadDescription Class"
description: "Represents a download description."
---

# Attica::DownloadDescription Class

Represents a download description. [More...](#details)

- **Header:** `#include <Attica/DownloadDescription>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS Attica)`  
  `target_link_libraries(mytarget PRIVATE KF6::Attica)`

[List of all members, including inherited members](attica-downloaddescription-members.md)

## Public Types

- [enum DownloadDescription::Type](#Type-enum)

## Public Functions

- [DownloadDescription()](#DownloadDescription)
- [QString category() const](#category)
- [QString distributionType() const](#distributionType)
- [QString gpgFingerprint() const](#gpgFingerprint)
- [QString gpgSignature() const](#gpgSignature)
- [bool hasPrice() const](#hasPrice)
- [int id() const](#id)
- [QString link() const](#link)
- [QString name() const](#name)
- [QString packageName() const](#packageName)
- [QString priceAmount() const](#priceAmount)
- [QString priceReason() const](#priceReason)
- [QString repository() const](#repository)
- [void setCategory(const QString &category)](#setCategory)
- [void setDistributionType(const QString &distributionType)](#setDistributionType)
- [void setGpgFingerprint(const QString &fingerprint)](#setGpgFingerprint)
- [void setGpgSignature(const QString &signature)](#setGpgSignature)
- [void setHasPrice(bool hasPrice)](#setHasPrice)
- [void setId(int id)](#setId)
- [void setLink(const QString &link)](#setLink)
- [void setName(const QString &name)](#setName)
- [void setPackageName(const QString &packageName)](#setPackageName)
- [void setPriceAmount(const QString &priceAmount)](#setPriceAmount)
- [void setPriceReason(const QString &priceReason)](#setPriceReason)
- [void setRepository(const QString &repository)](#setRepository)
- [void setSize(uint size)](#setSize)
- [void setTags(const QStringList &tags)](#setTags)
- [void setType(Attica::DownloadDescription::Type type)](#setType)
- [void setVersion(const QString &version)](#setVersion) (since 6.5)
- [uint size() const](#size)
- [QStringList tags() const](#tags)
- [Attica::DownloadDescription::Type type() const](#type)
- [QString version() const](#version) (since 6.5)

## Detailed Description {#details}

## Member Type Documentation {#member-type-documentation}

### enum DownloadDescription::Type {#Type-enum}

| Constant |   |
| --- | --- |
| `Attica::DownloadDescription::FileDownload` | `0` |
| `Attica::DownloadDescription::LinkDownload` | `1` |
| `Attica::DownloadDescription::PackageDownload` | `2` |

## Member Function Documentation {#member-function-documentation}

### DownloadDescription::DownloadDescription() {#DownloadDescription}

### QString DownloadDescription::category() const {#category}

*See also* [setCategory](attica-downloaddescription.md#setCategory)()

### QString DownloadDescription::distributionType() const {#distributionType}

*See also* [setDistributionType](attica-downloaddescription.md#setDistributionType)()

### QString DownloadDescription::gpgFingerprint() const {#gpgFingerprint}

*See also* [setGpgFingerprint](attica-downloaddescription.md#setGpgFingerprint)()

### QString DownloadDescription::gpgSignature() const {#gpgSignature}

*See also* [setGpgSignature](attica-downloaddescription.md#setGpgSignature)()

### bool DownloadDescription::hasPrice() const {#hasPrice}

*See also* [setHasPrice](attica-downloaddescription.md#setHasPrice)()

### int DownloadDescription::id() const {#id}

The id of the description - as one Content can have multiple download descriptions associated. This will simply be 1, 2, ...

*See also* [setId](attica-downloaddescription.md#setId)()

### QString DownloadDescription::link() const {#link}

*See also* [setLink](attica-downloaddescription.md#setLink)()

### QString DownloadDescription::name() const {#name}

*See also* [setName](attica-downloaddescription.md#setName)()

### QString DownloadDescription::packageName() const {#packageName}

*See also* [setPackageName](attica-downloaddescription.md#setPackageName)()

### QString DownloadDescription::priceAmount() const {#priceAmount}

*See also* [setPriceAmount](attica-downloaddescription.md#setPriceAmount)()

### QString DownloadDescription::priceReason() const {#priceReason}

*See also* [setPriceReason](attica-downloaddescription.md#setPriceReason)()

### QString DownloadDescription::repository() const {#repository}

*See also* [setRepository](attica-downloaddescription.md#setRepository)()

### void DownloadDescription::setCategory(const QString &*category*) {#setCategory}

*See also* [category](attica-downloaddescription.md#category)()

### void DownloadDescription::setDistributionType(const QString &*distributionType*) {#setDistributionType}

*See also* [distributionType](attica-downloaddescription.md#distributionType)()

### void DownloadDescription::setGpgFingerprint(const QString &*fingerprint*) {#setGpgFingerprint}

*See also* [gpgFingerprint](attica-downloaddescription.md#gpgFingerprint)()

### void DownloadDescription::setGpgSignature(const QString &*signature*) {#setGpgSignature}

*See also* [gpgSignature](attica-downloaddescription.md#gpgSignature)()

### void DownloadDescription::setHasPrice(bool *hasPrice*) {#setHasPrice}

*See also* [hasPrice](attica-downloaddescription.md#hasPrice)()

### void DownloadDescription::setId(int *id*) {#setId}

*See also* [id](attica-downloaddescription.md#id)()

### void DownloadDescription::setLink(const QString &*link*) {#setLink}

*See also* [link](attica-downloaddescription.md#link)()

### void DownloadDescription::setName(const QString &*name*) {#setName}

*See also* [name](attica-downloaddescription.md#name)()

### void DownloadDescription::setPackageName(const QString &*packageName*) {#setPackageName}

*See also* [packageName](attica-downloaddescription.md#packageName)()

### void DownloadDescription::setPriceAmount(const QString &*priceAmount*) {#setPriceAmount}

*See also* [priceAmount](attica-downloaddescription.md#priceAmount)()

### void DownloadDescription::setPriceReason(const QString &*priceReason*) {#setPriceReason}

*See also* [priceReason](attica-downloaddescription.md#priceReason)()

### void DownloadDescription::setRepository(const QString &*repository*) {#setRepository}

*See also* [repository](attica-downloaddescription.md#repository)()

### void DownloadDescription::setSize(uint *size*) {#setSize}

*See also* [size](attica-downloaddescription.md#size)()

### void DownloadDescription::setTags(const QStringList &*tags*) {#setTags}

Set the list of tags for this download description

*See also* [tags](attica-downloaddescription.md#tags)()

### void DownloadDescription::setType(Attica::DownloadDescription::Type *type*) {#setType}

*See also* [type](attica-downloaddescription.md#type)()

### \[since 6.5\] void DownloadDescription::setVersion(const QString &*version*) {#setVersion}

This function was introduced in Qt 6.5.

*See also* [version](attica-downloaddescription.md#version)()

### uint DownloadDescription::size() const {#size}

*See also* [setSize](attica-downloaddescription.md#setSize)()

### QStringList DownloadDescription::tags() const {#tags}

Get the list of tags for this download description

*See also* [setTags](attica-downloaddescription.md#setTags)()

### Attica::DownloadDescription::Type DownloadDescription::type() const {#type}

*See also* [setType](attica-downloaddescription.md#setType)()

### \[since 6.5\] QString DownloadDescription::version() const {#version}

The download version as set on the remote. May be QString() when not set.

This function was introduced in Qt 6.5.

*See also* [setVersion](attica-downloaddescription.md#setVersion)()
