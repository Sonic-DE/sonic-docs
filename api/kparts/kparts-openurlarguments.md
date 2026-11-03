---
title: "KParts::OpenUrlArguments Class"
description: "OpenUrlArguments is the set of arguments that specify how a URL should be opened by KParts::ReadOnlyPart::openUrl()."
---

# KParts::OpenUrlArguments Class

[OpenUrlArguments](kparts-openurlarguments.md) is the set of arguments that specify how a URL should be opened by KParts::ReadOnlyPart::openUrl(). [More...](#details)

- **Header:** `#include <KParts/OpenUrlArguments>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS Parts)`  
  `target_link_libraries(mytarget PRIVATE KF6::Parts)`

[List of all members, including inherited members](kparts-openurlarguments-members.md)

## Public Functions

- [OpenUrlArguments()](#OpenUrlArguments)
- [bool actionRequestedByUser() const](#actionRequestedByUser)
- [QMap\<QString, QString\> &metaData()](#metaData)
- [const QMap\<QString, QString\> &metaData() const](#metaData-1)
- [QString mimeType() const](#mimeType)
- [bool reload() const](#reload)
- [void setActionRequestedByUser(bool userRequested)](#setActionRequestedByUser)
- [void setMimeType(const QString &mime)](#setMimeType)
- [void setReload(bool b)](#setReload)
- [void setXOffset(int x)](#setXOffset)
- [void setYOffset(int y)](#setYOffset)
- [int xOffset() const](#xOffset)
- [int yOffset() const](#yOffset)

## Detailed Description {#details}

For instance [reload](kparts-openurlarguments.md#reload)() indicates that the url should be loaded from the network even if it matches the current url of the part.

All setter methods in this class are for the class that calls openUrl (usually the hosting application), all the getter methods are for the part.

## Member Function Documentation {#member-function-documentation}

### OpenUrlArguments::OpenUrlArguments() {#OpenUrlArguments}

### bool OpenUrlArguments::actionRequestedByUser() const {#actionRequestedByUser}

True if the user requested that the URL be opened. False if the URL should be opened due to an external event, like javascript popups or automatic redirections. This is true by default

*See also* [setActionRequestedByUser](kparts-openurlarguments.md#setActionRequestedByUser)()

### QMap\<QString, QString\> &OpenUrlArguments::metaData() {#metaData}

Meta-data to associate with the KIO operation that will be used to open the URL.

This method can be used to add or retrieve metadata.

*See also* [KIO::TransferJob](../kiocore/kio-transferjob.md)

### const QMap\<QString, QString\> &OpenUrlArguments::metaData() const {#metaData-1}

### QString OpenUrlArguments::mimeType() const {#mimeType}

The mimetype to use when opening the url, when known by the calling application.

*See also* [setMimeType](kparts-openurlarguments.md#setMimeType)()

### bool OpenUrlArguments::reload() const {#reload}

Returns true to indicate that the part should reload the URL, i.e. the cache shouldn't be used (forced reload).

*See also* [setReload](kparts-openurlarguments.md#setReload)()

### void OpenUrlArguments::setActionRequestedByUser(bool *userRequested*) {#setActionRequestedByUser}

*See also* [actionRequestedByUser](kparts-openurlarguments.md#actionRequestedByUser)()

### void OpenUrlArguments::setMimeType(const QString &*mime*) {#setMimeType}

*See also* [mimeType](kparts-openurlarguments.md#mimeType)()

### void OpenUrlArguments::setReload(bool *b*) {#setReload}

Indicates that the url should be loaded from the network even if it matches the current url of the part.

*See also* [reload](kparts-openurlarguments.md#reload)()

### void OpenUrlArguments::setXOffset(int *x*) {#setXOffset}

*See also* [xOffset](kparts-openurlarguments.md#xOffset)()

### void OpenUrlArguments::setYOffset(int *y*) {#setYOffset}

*See also* [yOffset](kparts-openurlarguments.md#yOffset)()

### int OpenUrlArguments::xOffset() const {#xOffset}

xOffset is the horizontal scrolling of the part's widget (in case it's a scrollview). This is saved into the history and restored when going back in the history.

*See also* [setXOffset](kparts-openurlarguments.md#setXOffset)()

### int OpenUrlArguments::yOffset() const {#yOffset}

yOffset is the vertical scrolling of the part's widget (in case it's a scrollview). This is saved into the history and restored when going back in the history.

*See also* [setYOffset](kparts-openurlarguments.md#setYOffset)()
