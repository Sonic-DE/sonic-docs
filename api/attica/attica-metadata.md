---
title: "Attica::Metadata Class"
description: "Status messages from the server."
---

# Attica::Metadata Class

Status messages from the server. [More...](#details)

- **Header:** `#include <Attica/Metadata>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS Attica)`  
  `target_link_libraries(mytarget PRIVATE KF6::Attica)`

[List of all members, including inherited members](attica-metadata-members.md)

## Public Types

- [enum Metadata::Error](#Error-enum)

## Public Functions

- [Metadata()](#Metadata)
- [Attica::Metadata::Error error() const](#error)
- [QList\<QNetworkReply::RawHeaderPair\> headers() const](#headers)
- [int itemsPerPage()](#itemsPerPage)
- [QString message()](#message)
- [QString resultingId()](#resultingId)
- [void setError(Attica::Metadata::Error error)](#setError)
- [void setHeaders(const QList\<QNetworkReply::RawHeaderPair\> &headers)](#setHeaders)
- [void setItemsPerPage(int itemsPerPage)](#setItemsPerPage)
- [void setMessage(const QString &message)](#setMessage)
- [void setResultingId(const QString &id)](#setResultingId)
- [void setStatusCode(int code)](#setStatusCode)
- [void setStatusString(const QString &status)](#setStatusString)
- [void setTotalItems(int items)](#setTotalItems)
- [int statusCode() const](#statusCode)
- [QString statusString() const](#statusString)
- [int totalItems()](#totalItems)

## Detailed Description {#details}

## Member Type Documentation {#member-type-documentation}

### enum Metadata::Error {#Error-enum}

| Constant |   |
| --- | --- |
| `Attica::Metadata::NoError` | `0` |
| `Attica::Metadata::NetworkError` | `1` |
| `Attica::Metadata::OcsError` | `2` |

## Member Function Documentation {#member-function-documentation}

### Metadata::Metadata() {#Metadata}

### Attica::Metadata::Error Metadata::error() const {#error}

Check if the job was successful.

Returns the error state enum returns the type of error (network or ocs)

*See also* [setError](attica-metadata.md#setError)()

### QList\<QNetworkReply::RawHeaderPair\> Metadata::headers() const {#headers}

The http headers for the most recent network action in the case of a network error

Use this to further inspect the error condition if the OCS status code and string is not enough to work out precisely what has happened (for example in case of a HTTP 503 status, which would suggest the service is down for maintenance for an expected duration which might be read from the Retry-After header).

Returns the list of raw headers (equivalent to a QNetworkReply::rawHeaderPairs call)

*See also* [setHeaders](attica-metadata.md#setHeaders)()

### int Metadata::itemsPerPage() {#itemsPerPage}

The number of items per page the server was asked for

*See also* [setItemsPerPage](attica-metadata.md#setItemsPerPage)()

### QString Metadata::message() {#message}

An optional additional message from the server

*See also* [setMessage](attica-metadata.md#setMessage)()

### QString Metadata::resultingId() {#resultingId}

The resulting ID when a [PostJob](attica-postjob.md) created a new item.

*See also* [setResultingId](attica-metadata.md#setResultingId)()

### void Metadata::setError(Attica::Metadata::Error *error*) {#setError}

*See also* [error](attica-metadata.md#error)()

### void Metadata::setHeaders(const QList\<QNetworkReply::RawHeaderPair\> &*headers*) {#setHeaders}

Sets the http headers read by [headers](attica-metadata.md#headers)()

`headers` The new list of raw headers

*See also* [headers](attica-metadata.md#headers)()

### void Metadata::setItemsPerPage(int *itemsPerPage*) {#setItemsPerPage}

*See also* [itemsPerPage](attica-metadata.md#itemsPerPage)()

### void Metadata::setMessage(const QString &*message*) {#setMessage}

*See also* [message](attica-metadata.md#message)()

### void Metadata::setResultingId(const QString &*id*) {#setResultingId}

*See also* [resultingId](attica-metadata.md#resultingId)()

### void Metadata::setStatusCode(int *code*) {#setStatusCode}

*See also* [statusCode](attica-metadata.md#statusCode)()

### void Metadata::setStatusString(const QString &*status*) {#setStatusString}

*See also* [statusString](attica-metadata.md#statusString)()

### void Metadata::setTotalItems(int *items*) {#setTotalItems}

*See also* [totalItems](attica-metadata.md#totalItems)()

### int Metadata::statusCode() const {#statusCode}

The status as integer.

If the error is an OCS error, refer to http://www.freedesktop.org/wiki/Specifications/open-collaboration-services in any other case it is the network return code.

*See also* [setStatusCode](attica-metadata.md#setStatusCode)()

### QString Metadata::statusString() const {#statusString}

The status of the job, for example "Ok"

*See also* [setStatusString](attica-metadata.md#setStatusString)()

### int Metadata::totalItems() {#totalItems}

The number of items returned by this job (only relevant for list jobs)

*See also* [setTotalItems](attica-metadata.md#setTotalItems)()
