---
title: "Syndication::Feed Class"
description: "This class represents a feed document (\"Channel\" in RSS, \"Feed\" in Atom)."
---

# Syndication::Feed Class

This class represents a feed document ("Channel" in RSS, "Feed" in Atom). [More...](#details)

- **Header:** `#include <Syndication/Feed>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS Syndication)`  
  `target_link_libraries(mytarget PRIVATE KF6::Syndication)`

[List of all members, including inherited members](syndication-feed-members.md)

## Public Functions

- [QMultiMap\<QString, QDomElement\> additionalProperties() const](#additionalProperties)
- [QList\<Syndication::PersonPtr\> authors() const](#authors)
- [QList\<Syndication::CategoryPtr\> categories() const](#categories)
- [QString copyright() const](#copyright)
- [QString debugInfo() const](#debugInfo)
- [QString description() const](#description)
- [Syndication::ImagePtr icon() const](#icon)
- [Syndication::ImagePtr image() const](#image)
- [QList\<Syndication::ItemPtr\> items() const](#items)
- [QString language() const](#language)
- [QString link() const](#link)
- [Syndication::SpecificDocumentPtr specificDocument() const](#specificDocument)
- [QString title() const](#title)

## Detailed Description {#details}

It contains a ordered list of items (e.g., articles) and a description of the feed (title, homepage, etc.). This interface abstracts from format-specific details of e.g. [Atom::FeedDocument](syndication-atom-feeddocument.md) or RSS::Document and provides a format-agnostic, unified view on the document.

This way applications using the syndication library have no need to care about the syndication format jungle at all. If necessary, format details and specialities can be accessed using the [specificDocument](syndication-feed.md#specificDocument)() method.

## Member Function Documentation {#member-function-documentation}

### \[pure virtual\] QMultiMap\<QString, QDomElement\> Feed::additionalProperties() const {#additionalProperties}

returns a list of feed metadata not covered by this class. Can be used e.g. to access format extensions.

The returned map contains key value pairs, where the key is the tag name of the element, namespace prefix are resolved to the corresponding URIs. The value is the XML element as read from the document.

For example, to access the \<itunes:subtitle\> element, use additionalProperties()\["http://www.itunes.com/dtds/podcast-1.0.dtdsubtitle"\].

Currently this is only supported for RSS 0.91..0.94/2.0 and Atom formats, but not for RDF (RSS 0.9 and 1.0).

### \[pure virtual\] QList\<Syndication::PersonPtr\> Feed::authors() const {#authors}

returns a list of persons who created the feed content. If there is a distinction between authors and contributors (Atom), both are added to the list, where authors are added first.

### \[pure virtual\] QList\<Syndication::CategoryPtr\> Feed::categories() const {#categories}

Returns a list of categories this feed is associated with. See Category for more information.

### \[pure virtual\] QString Feed::copyright() const {#copyright}

returns copyright information about the feed

### \[virtual\] QString Feed::debugInfo() const {#debugInfo}

returns a description of the feed for debugging purposes

### \[pure virtual\] QString Feed::description() const {#description}

A description of the feed.

This string may contain HTML markup.(Importantly, occurrences of the characters '\<', '\\n', '&', ''' and '"' are escaped).

### \[pure virtual\] Syndication::ImagePtr Feed::icon() const {#icon}

returns an icon associated with this item.

Returns an icon object, or a null icon (Not a null pointer! I.e., icon()-\>isNull() is `true`) if no image is specified in the feed

### \[pure virtual\] Syndication::ImagePtr Feed::image() const {#image}

Returns an image associated with this item, or a null image (Not a null pointer! I.e., image()-\>isNull() is `true`) if no image is specified in the feed

### \[pure virtual\] QList\<Syndication::ItemPtr\> Feed::items() const {#items}

A list of items, in the order they were parsed from the feed source. (usually reverse chronological order, see also [Item::datePublished](syndication-item.md#datePublished)() for sorting purposes).

### \[pure virtual\] QString Feed::language() const {#language}

The language used in the feed. This is a global setting, which can be overridden by the contained items.

TODO: describe concrete format (language codes)

### \[pure virtual\] QString Feed::link() const {#link}

returns a link pointing to a website associated with this channel. (blog, news site etc.)

### \[pure virtual\] Syndication::SpecificDocumentPtr Feed::specificDocument() const {#specificDocument}

Returns the format-specific document this abstraction wraps.

If you want to access format-specific properties, this can be used, in combination with a [DocumentVisitor](syndication-documentvisitor.md).

### \[pure virtual\] QString Feed::title() const {#title}

The title of the feed.

This string may contain HTML markup.(Importantly, occurrences of the characters '\<', '\\n', '&', ''' and '"' are escaped).

Returns the title, or a null string if none is specified
