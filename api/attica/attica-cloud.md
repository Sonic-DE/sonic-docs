---
title: "Attica::Cloud Class"
description: "Represents a cloud service."
---

# Attica::Cloud Class

Represents a cloud service. [More...](#details)

- **Header:** `#include <Attica/Cloud>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS Attica)`  
  `target_link_libraries(mytarget PRIVATE KF6::Attica)`

[List of all members, including inherited members](attica-cloud-members.md)

## Public Types

- [Cloud::List](#List-typedef)

## Public Functions

- [Cloud()](#Cloud)
- [qulonglong free() const](#free)
- [QUrl icon() const](#icon)
- [QString key() const](#key)
- [QString name() const](#name)
- [qulonglong quota() const](#quota)
- [float relative() const](#relative)
- [void setFree(qulonglong free)](#setFree)
- [void setIcon(const QUrl &icon)](#setIcon)
- [void setKey(const QString &privateKey)](#setKey)
- [void setName(const QString &name)](#setName)
- [void setQuota(qulonglong quota)](#setQuota)
- [void setRelative(float relative)](#setRelative)
- [void setUrl(const QString &url)](#setUrl)
- [void setUsed(qulonglong used)](#setUsed)
- [QString url() const](#url)
- [qulonglong used() const](#used)

## Detailed Description {#details}

## Member Type Documentation {#member-type-documentation}

### Cloud::List {#List-typedef}

## Member Function Documentation {#member-function-documentation}

### Cloud::Cloud() {#Cloud}

Creates an empty Cloud

### qulonglong Cloud::free() const {#free}

Returns the free amount of the Cloud service.

*See also* [setFree](attica-cloud.md#setFree)()

### QUrl Cloud::icon() const {#icon}

Returns the icon of the Cloud service.

*See also* [setIcon](attica-cloud.md#setIcon)()

### QString Cloud::key() const {#key}

Returns the private key of the Cloud service.

*See also* [setKey](attica-cloud.md#setKey)()

### QString Cloud::name() const {#name}

Returns the name of the Cloud service.

*See also* [setName](attica-cloud.md#setName)()

### qulonglong Cloud::quota() const {#quota}

Returns the quota of the Cloud service.

*See also* [setQuota](attica-cloud.md#setQuota)()

### float Cloud::relative() const {#relative}

Returns the relative of the Cloud service.

*See also* [setRelative](attica-cloud.md#setRelative)()

### void Cloud::setFree(qulonglong *free*) {#setFree}

Sets the free amount of the Cloud service

`free` the new free amount

*See also* [free](attica-cloud.md#free)()

### void Cloud::setIcon(const QUrl &*icon*) {#setIcon}

Sets the icon of the Cloud service

`icon` the new icon

*See also* [icon](attica-cloud.md#icon)()

### void Cloud::setKey(const QString &*privateKey*) {#setKey}

Sets the private key of the Cloud service

`privateKey` the new privateKey

*See also* [key](attica-cloud.md#key)()

### void Cloud::setName(const QString &*name*) {#setName}

Sets the name of the Cloud service

`name` the new name

*See also* [name](attica-cloud.md#name)()

### void Cloud::setQuota(qulonglong *quota*) {#setQuota}

Sets the quota of the Cloud service

`quota` the new quota

*See also* [quota](attica-cloud.md#quota)()

### void Cloud::setRelative(float *relative*) {#setRelative}

Sets the relative of the Cloud service

`relative` the new relative

*See also* [relative](attica-cloud.md#relative)()

### void Cloud::setUrl(const QString &*url*) {#setUrl}

Sets the url of the Cloud service

`url` the new url

*See also* [url](attica-cloud.md#url)()

### void Cloud::setUsed(qulonglong *used*) {#setUsed}

Sets the used amount of the Cloud service

`used` the new used amount

*See also* [used](attica-cloud.md#used)()

### QString Cloud::url() const {#url}

Returns the url of the Cloud service.

*See also* [setUrl](attica-cloud.md#setUrl)()

### qulonglong Cloud::used() const {#used}

Returns the used amount of the Cloud service.

*See also* [setUsed](attica-cloud.md#setUsed)()
