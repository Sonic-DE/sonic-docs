---
title: "Syndication::Atom::Source Class"
description: "If an entry was copied from another feed, this class contains a description of the source feed."
---

# Syndication::Atom::Source Class

If an entry was copied from another feed, this class contains a description of the source feed. [More...](#details)

- **Header:** `#include <Syndication/Atom/Source>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS Syndication)`  
  `target_link_libraries(mytarget PRIVATE KF6::Syndication)`
- **Inherits:** [Syndication::ElementWrapper](syndication-elementwrapper.md)

[List of all members, including inherited members](syndication-atom-source-members.md)

## Public Functions

- [Source()](#Source)
- [Source(const QDomElement &element)](#Source-1)
- [QList\<Syndication::Atom::Person\> authors() const](#authors)
- [QList\<Syndication::Atom::Category\> categories() const](#categories)
- [QList\<Syndication::Atom::Person\> contributors() const](#contributors)
- [QString debugInfo() const](#debugInfo)
- [Syndication::Atom::Generator generator() const](#generator)
- [QString icon() const](#icon)
- [QString id() const](#id)
- [QList\<Syndication::Atom::Link\> links() const](#links)
- [QString logo() const](#logo)
- [QString rights() const](#rights)
- [QString subtitle() const](#subtitle)
- [QString title() const](#title)
- [time\_t updated() const](#updated)

## Detailed Description {#details}

## Member Function Documentation {#member-function-documentation}

### Source::Source() {#Source}

creates a null source object

### \[explicit\] Source::Source(const QDomElement &*element*) {#Source-1}

creates a Source object wrapping a atom:source element.

`element` a DOM element, should be a atom:source element (although not enforced), otherwise this object will not parse anything useful

### QList\<Syndication::Atom::Person\> Source::authors() const {#authors}

authors of the original content (optional)

### QList\<Syndication::Atom::Category\> Source::categories() const {#categories}

categories the source feed is assigned to (optional)

### QList\<Syndication::Atom::Person\> Source::contributors() const {#contributors}

contributors to the original content (optional)

### QString Source::debugInfo() const {#debugInfo}

description of this source object for debugging purposes

Returns debug string

### Syndication::Atom::Generator Source::generator() const {#generator}

description of the software which generated the source feed (optional)

### QString Source::icon() const {#icon}

URL of an image serving as a feed icon (optional)

Returns icon URL, or a null string if not specified

### QString Source::id() const {#id}

a string that unambiguously identifies the source feed (optional)

Returns the ID of the source feed, or a null string if not specified.

### QList\<Syndication::Atom::Link\> Source::links() const {#links}

a list of links. See Link for more information on link types.

### QString Source::logo() const {#logo}

URL of an image, the logo of the source feed (optional)

Returns image URL, or a null string if not specified in the feed.

### QString Source::rights() const {#rights}

copyright information (optional)

Returns copyright information for the source, or a null string if not specified

### QString Source::subtitle() const {#subtitle}

description or subtitle of the source feed (optional).

Returns subtitle string as HTML, or a null string if not specified.

### QString Source::title() const {#title}

source feed title (optional).

Returns title string as HTML, or a null string if not specified

### time\_t Source::updated() const {#updated}

The datetime of the last modification of the source feed content. (optional)

Returns the modification date in seconds since epoch
