---
title: "KFileFilter Class"
description: "Network transparent access to files and data."
---

# KFileFilter Class

Network transparent access to files and data. [More...](#details)

- **Header:** `#include <KFileFilter>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS KIO)`  
  `target_link_libraries(mytarget PRIVATE KF6::KIOCore)`

[List of all members, including inherited members](kfilefilter-members.md)

## Public Functions

- [KFileFilter()](#KFileFilter)
- [KFileFilter(const QString &label, const QStringList &filePatterns, const QStringList &mimePatterns)](#KFileFilter-1)
- [QStringList filePatterns() const](#filePatterns)
- [bool isEmpty() const](#isEmpty)
- [bool isValid() const](#isValid) (since 6.0)
- [QString label() const](#label)
- [QStringList mimePatterns() const](#mimePatterns)
- [QString toFilterString() const](#toFilterString)
- [bool KFileFilter::operator==(const KFileFilter &other) const](#operator-eq-eq)

## Static Public Members

- [KFileFilter fromMimeType(const QString &mimeType)](#fromMimeType)
- [QList\<KFileFilter\> fromMimeTypes(const QStringList &mimeTypes)](#fromMimeTypes) (since 6.0)

## Detailed Description {#details}

Encapsulates rules to filter a list of files. Files can be filtered based on name patterns (e.g. \*.cpp), MIME types, or both. Filters also optionally have a user-facing label.

## Member Function Documentation {#member-function-documentation}

### \[explicit\] KFileFilter::KFileFilter() {#KFileFilter}

Creates an empty filter.

### \[explicit\] KFileFilter::KFileFilter(const QString &*label*, const QStringList &*filePatterns*, const QStringList &*mimePatterns*) {#KFileFilter-1}

Creates a filter with a given label, name patterns, and MIME types.

`label` The user-facing label for this filter.

`filePatterns` A list of file name patterns that should be included, e.g. ("\*.cpp", "\*.cxx").

`mimePatterns` A list of MIME types that should be included, e.g. ("text/plain", "image/png").

### QStringList KFileFilter::filePatterns() const {#filePatterns}

List of file name patterns that are included by this filter.

### \[static\] KFileFilter KFileFilter::fromMimeType(const QString &*mimeType*) {#fromMimeType}

Creates a filter for one MIME type. The user-facing label is automatically determined from the MIME type.

### \[static, since 6.0\] QList\<KFileFilter\> KFileFilter::fromMimeTypes(const QStringList &*mimeTypes*) {#fromMimeTypes}

Creates filters from a list of MIME types. The user-facing label is automatically determined from the MIME type.

This function was introduced in Qt 6.0.

### bool KFileFilter::isEmpty() const {#isEmpty}

Whether the filer is empty, i.e. matches all files.

### \[since 6.0\] bool KFileFilter::isValid() const {#isValid}

Whether the filter is valid.

Creating a filter from an invalid/unknown MIME type will result in an invalid filter.

This function was introduced in Qt 6.0.

### QString KFileFilter::label() const {#label}

The user-facing label for this filter.

If no label is passed on creation one is created based on the patterns.

### QStringList KFileFilter::mimePatterns() const {#mimePatterns}

List of MIME types that are included by this filter;

### QString KFileFilter::toFilterString() const {#toFilterString}

Converts this filter to a string representation

### bool KFileFilter::operator==(const KFileFilter &*other*) const {#operator-eq-eq}

Checks whether two filters are equal.

Filters are considered equal if their file and name patters match. The label is ignored here.
