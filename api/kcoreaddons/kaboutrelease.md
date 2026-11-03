---
title: "KAboutRelease Class"
description: "An individual release note of a program or plugin. This class was introduced in Qt 6.26."
---

# KAboutRelease Class

An individual release note of a program or plugin. This class was introduced in Qt 6.26. [More...](#details)

- **Header:** `#include <KAboutRelease>`
- **Since:** Qt 6.26
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS CoreAddons)`  
  `target_link_libraries(mytarget PRIVATE KF6::CoreAddons)`

[List of all members, including inherited members](kaboutrelease-members.md)

## Properties

- [\[read-only\] date : QDate](#date-prop)
- [\[read-only\] description : QString](#description-prop)
- [\[read-only\] url : QUrl](#url-prop)
- [\[read-only\] version : QString](#version-prop)

## Public Functions

- [QDate date() const](#date)
- [QString description() const](#description)
- [QString untranslatedDescription() const](#untranslatedDescription)
- [QUrl url() const](#url)
- [QString version() const](#version)

## Detailed Description {#details}

This represents an AppStream release note of an individual version.

*See also* [https://www.freedesktop.org/software/appstream/docs/sect-Metadata-Releases.html](https://www.freedesktop.org/software/appstream/docs/sect-Metadata-Releases.html)

## Property Documentation {#property-documentation}

### \[read-only\] date : QDate {#date-prop}

**Access functions:**

- `QDate` **[date](kaboutrelease.md#date)**() const

### \[read-only\] description : QString {#description-prop}

**Access functions:**

- `QString` **[description](kaboutrelease.md#description)**() const

### \[read-only\] url : QUrl {#url-prop}

**Access functions:**

- `QUrl` **[url](kaboutrelease.md#url)**() const

### \[read-only\] version : QString {#version-prop}

**Access functions:**

- `QString` **[version](kaboutrelease.md#version)**() const

## Member Function Documentation {#member-function-documentation}

### QDate KAboutRelease::date() const {#date}

Returns the date on which this version was released.

> **Note:** Getter function for property [date](kaboutrelease.md#date-prop).

### QString KAboutRelease::description() const {#description}

Returns the (translated) release notes.

This is provided as restricted rich text, following what the description tag in AppStream allows. This is suitable for consumption by Qt rich text labels.

> **Note:** Getter function for property [description](kaboutrelease.md#description-prop).

### QString KAboutRelease::untranslatedDescription() const {#untranslatedDescription}

Returns the untranslated release notes.

This is not meant for displaying to users, but for detecting changes since the last display, when display release notes on development versions.

*See also* [description](kaboutrelease.md#description)

### QUrl KAboutRelease::url() const {#url}

Returns a URL to a website with more information about the release.

> **Note:** Getter function for property [url](kaboutrelease.md#url-prop).

### QString KAboutRelease::version() const {#version}

Retursn the version this release note refers to.

> **Note:** Getter function for property [version](kaboutrelease.md#version-prop).
