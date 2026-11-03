---
title: "Syndication::Atom::Link Class"
description: "A link, pointing to webpages, media files on the web (\"podcast\"), related content, etc. See rel() for details."
---

# Syndication::Atom::Link Class

A link, pointing to webpages, media files on the web ("podcast"), related content, etc. See [rel](syndication-atom-link.md#rel)() for details. [More...](#details)

- **Header:** `#include <Syndication/Atom/Link>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS Syndication)`  
  `target_link_libraries(mytarget PRIVATE KF6::Syndication)`
- **Inherits:** [Syndication::ElementWrapper](syndication-elementwrapper.md)

[List of all members, including inherited members](syndication-atom-link-members.md)

## Public Functions

- [Link()](#Link)
- [Link(const QDomElement &element)](#Link-1)
- [QString debugInfo() const](#debugInfo)
- [QString href() const](#href)
- [QString hrefLanguage() const](#hrefLanguage)
- [uint length() const](#length)
- [QString rel() const](#rel)
- [QString title() const](#title)
- [QString type() const](#type)

## Detailed Description {#details}

## Member Function Documentation {#member-function-documentation}

### Link::Link() {#Link}

creates a null link object.

### \[explicit\] Link::Link(const QDomElement &*element*) {#Link-1}

creates a Link object wrapping an atom:link element.

`element` a DOM element, should be a atom:link element (although not enforced), otherwise this object will not parse anything useful

### QString Link::debugInfo() const {#debugInfo}

description of the link object for debugging purposes

Returns debug string

### QString Link::href() const {#href}

URL of the referenced resource (required)

### QString Link::hrefLanguage() const {#hrefLanguage}

the language of the linked resource. (optional) If used together with a [rel](syndication-atom-link.md#rel)() value of "alternate", it implies a translated version of the entry.

Returns a language tag as defined in RFC 3066, or a null string if not specified

### uint Link::length() const {#length}

size of the linked resource in bytes. (optional)

Returns file size in bytes, or 0 if not specified

### QString Link::rel() const {#rel}

the relation between the feed/entry and the linked resource.

The value of rel() is usually one of the following:

`"alternate"`: The URL points to an alternate version of the feed/entry. In practice, this is the article described in an entry, or the homepage of the feed.

`"enclosure"`: The link describes an Enclosure. See [Syndication::Enclosure](syndication-enclosure.md) for more information.

`"related"`: links to web resources with related content. E.g., an article discussing KDE might link to the KDE homepage.

`"self"`: "identifies a resource equivalent to the containing element". This is usually the URL of the feed source itself.

`"via"`: The link points to the source of the information contained in the feed/entry

Returns the rel value specified in the feed. Default value is `"alternate"`

### QString Link::title() const {#title}

human-readable information about the link. (optional)

Returns the link title as plain text ("\<", "&" are text, not markup!), or a null string if not specified

### QString Link::type() const {#type}

MIME type of the linked resource. (optional)

Returns MIME type following (e.g., "text/html", "audio/mpeg"), or a null string if not set
