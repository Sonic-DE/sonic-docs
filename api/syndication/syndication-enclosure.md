---
title: "Syndication::Enclosure Class"
description: "An enclosure describes a (media) file available on the net."
---

# Syndication::Enclosure Class

An enclosure describes a (media) file available on the net. [More...](#details)

- **Header:** `#include <Syndication/Enclosure>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS Syndication)`  
  `target_link_libraries(mytarget PRIVATE KF6::Syndication)`

[List of all members, including inherited members](syndication-enclosure-members.md)

## Public Functions

- [QString debugInfo() const](#debugInfo)
- [uint duration() const](#duration)
- [bool isNull() const](#isNull)
- [uint length() const](#length)
- [QString title() const](#title)
- [QString type() const](#type)
- [QString url() const](#url)

## Detailed Description {#details}

Most of the time, enclosures are used for "podcasts", i.e. audio files announced and distributed via syndication.

## Member Function Documentation {#member-function-documentation}

### \[virtual\] QString Enclosure::debugInfo() const {#debugInfo}

description of this enclosure for debugging purposes

### \[pure virtual\] uint Enclosure::duration() const {#duration}

for audio/video files, the duration of the file in seconds

### \[pure virtual\] bool Enclosure::isNull() const {#isNull}

returns whether this enclosure is a null object.

### \[pure virtual\] uint Enclosure::length() const {#length}

returns the length of the linked file in bytes

### \[pure virtual\] QString Enclosure::title() const {#title}

title of the enclosure. This is a human-readable description of the linked file. If available, the title should be used in user interfaces instead of the URL. If no title is set (e.g., RSS2 enclosures don't have titles), use [url](syndication-enclosure.md#url)() as fallback.

### \[pure virtual\] QString Enclosure::type() const {#type}

MIME type of the enclosure.

Examples are "audio/mpeg" for MP3, or "application/pdf" for PDF.

### \[pure virtual\] QString Enclosure::url() const {#url}

The URL of the linked resource (required).
