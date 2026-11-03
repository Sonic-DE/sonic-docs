---
title: "Syndication::DocumentSource Class"
description: "Represents the source of a syndication document, as read from the downloaded file."
---

# Syndication::DocumentSource Class

Represents the source of a syndication document, as read from the downloaded file. [More...](#details)

- **Header:** `#include <Syndication/DocumentSource>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS Syndication)`  
  `target_link_libraries(mytarget PRIVATE KF6::Syndication)`

[List of all members, including inherited members](syndication-documentsource-members.md)

## Public Functions

- [DocumentSource()](#DocumentSource)
- [DocumentSource(const QByteArray &source, const QString &url)](#DocumentSource-2)
- [DocumentSource(const Syndication::DocumentSource &other)](#DocumentSource-1)
- [QByteArray asByteArray() const](#asByteArray)
- [QDomDocument asDomDocument() const](#asDomDocument)
- [unsigned int hash() const](#hash)
- [unsigned int size() const](#size)
- [QString url() const](#url)
- [Syndication::DocumentSource &DocumentSource::operator=(const Syndication::DocumentSource &other)](#operator-eq)

## Detailed Description {#details}

It provides a (cached) DOM representation of the document, but keeps the raw data available (for (rarely used) non-XML formats like Okay! News).

This way the document can be passed to all available parsers (to find the right one for the source), regardless whether they parse XML formats or non-XML formats, without having every parser to do the XML parsing again.

## Member Function Documentation {#member-function-documentation}

### DocumentSource::DocumentSource() {#DocumentSource}

Creates an empty document source. The raw representation is empty and the DOM representation will be invalid.

### DocumentSource::DocumentSource(const QByteArray &*source*, const QString &*url*) {#DocumentSource-2}

Creates a [DocumentSource](syndication-documentsource.md) object from a raw byte array

`source` the raw source (of the downloaded feed file usually)

`url` the URL/path the source was read from

### DocumentSource::DocumentSource(const Syndication::DocumentSource &*other*) {#DocumentSource-1}

Copy constructor. The d pointer is shared, so this is a cheap operation.

`other` [DocumentSource](syndication-documentsource.md) to copy

### QByteArray DocumentSource::asByteArray() const {#asByteArray}

Returns the feed source as byte array.

### QDomDocument DocumentSource::asDomDocument() const {#asDomDocument}

Returns the feed source as DOM document. The document is parsed only on the first call of this method and then cached.

If the feed source cannot be parsed successfully then the returned DOM node will be null (eg. asDomDocument().isNull() will return true)

Returns the XML representation parsed from the raw source

### unsigned int DocumentSource::hash() const {#hash}

Calculates a hash value for the source array.

This can be used to decide whether the feed has changed since the last fetch. If the hash hasn't changed since the last fetch, the feed wasn't modified with high probability.

Returns the hash calculated from the source, 0 if the source is empty

### unsigned int DocumentSource::size() const {#size}

returns the size the source array in bytes.

See also [QByteArray::size](https://doc.qt.io/qt-6/qbytearray.html#size)()

### QString DocumentSource::url() const {#url}

returns the URL the document source was loaded from

### Syndication::DocumentSource &DocumentSource::operator=(const Syndication::DocumentSource &*other*) {#operator-eq}

Assignment operator. The d pointer is shared, so this is a cheap operation.

`other` [DocumentSource](syndication-documentsource.md) to assign to this instance

Returns reference to this instance
