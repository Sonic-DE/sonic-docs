---
title: "Syndication::Item Class"
description: "An item from a news feed."
---

# Syndication::Item Class

An item from a news feed. [More...](#details)

- **Header:** `#include <Syndication/Item>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS Syndication)`  
  `target_link_libraries(mytarget PRIVATE KF6::Syndication)`

[List of all members, including inherited members](syndication-item-members.md)

## Public Functions

- [QMultiMap\<QString, QDomElement\> additionalProperties() const](#additionalProperties)
- [QList\<Syndication::PersonPtr\> authors() const](#authors)
- [QList\<Syndication::CategoryPtr\> categories() const](#categories)
- [QString commentPostUri() const](#commentPostUri)
- [int commentsCount() const](#commentsCount)
- [QString commentsFeed() const](#commentsFeed)
- [QString commentsLink() const](#commentsLink)
- [QString content() const](#content)
- [time\_t datePublished() const](#datePublished)
- [time\_t dateUpdated() const](#dateUpdated)
- [QString debugInfo() const](#debugInfo)
- [QString description() const](#description)
- [QList\<Syndication::EnclosurePtr\> enclosures() const](#enclosures)
- [QString id() const](#id)
- [QString language() const](#language)
- [QString link() const](#link)
- [Syndication::SpecificItemPtr specificItem() const](#specificItem)
- [QString title() const](#title)

## Detailed Description {#details}

## Member Function Documentation {#member-function-documentation}

### \[pure virtual\] QMultiMap\<QString, QDomElement\> Item::additionalProperties() const {#additionalProperties}

returns a list of item metadata not covered by this class. Can be used e.g. to access format extensions.

The returned map contains key value pairs, where the key is the tag name of the element, namespace prefix are resolved to the corresponding URIs. The value is the XML element as read from the document.

For example, to access the \<itunes:keywords\> element, use additionalProperties()\["http://www.itunes.com/dtds/podcast-1.0.dtdkeywords"\].

Currently this is only supported for RSS 0.91..0.94/2.0 and Atom formats, but not for RDF (RSS 0.9 and 1.0).

### \[pure virtual\] QList\<Syndication::PersonPtr\> Item::authors() const {#authors}

returns a list of persons who created the item content. If there is a distinction between authors and contributors (Atom), both are added to the list, where authors are added first.

### \[pure virtual\] QList\<Syndication::CategoryPtr\> Item::categories() const {#categories}

returns a list of categories this item is filed in. See Category for more information on categories.

### \[pure virtual\] QString Item::commentPostUri() const {#commentPostUri}

URI that can be used to post comments via an HTTP POST request using the Comment API.

For more details on the Comment API, see http://wellformedweb.org/story/9

Returns URI for posting comments, or a null string if not set

### \[pure virtual\] int Item::commentsCount() const {#commentsCount}

Returns the number of comments associated to this item, or -1 if not specified

### \[pure virtual\] QString Item::commentsFeed() const {#commentsFeed}

URL of feed syndicating comments belonging to this item.

### \[pure virtual\] QString Item::commentsLink() const {#commentsLink}

Link to an HTML site which contains the comments belonging to this item.

### \[pure virtual\] QString Item::content() const {#content}

returns the content of the item. If provided, this is the most comprehensive text content available for this item. If it is empty, use [description](syndication-item.md#description)() (which might also contain complete article content).

This string may contain HTML markup. (Importantly, occurrences of the characters '\<', '\\n', '&', ''' and '"' are escaped).

Returns content string as HTML, or a null string if not set

### \[pure virtual\] time\_t Item::datePublished() const {#datePublished}

returns the date when the item was initially published, as seconds since epoch (Jan 1st 1970), or 0 (epoch) if not set

### \[pure virtual\] time\_t Item::dateUpdated() const {#dateUpdated}

returns the date when the item was modified the last time. If no such date is provided by the feed, this method returns the value of [datePublished](syndication-item.md#datePublished)().

Returns modification date, as seconds since epoch (Jan 1st 1970)

### \[virtual\] QString Item::debugInfo() const {#debugInfo}

returns a description of the item for debugging purposes

### \[pure virtual\] QString Item::description() const {#description}

returns the description of the item.

The description can either be a tag line, a short summary of the item content up to a complete article. If [content](syndication-item.md#content)() is non-empty, it

This string may contain HTML markup. (Importantly, occurrences of the characters '\<', '\\n', '&', ''' and '"' are escaped).

Returns the description as HTML, or a null string if not specified

### \[pure virtual\] QList\<Syndication::EnclosurePtr\> Item::enclosures() const {#enclosures}

returns a list of enclosures describing files available on the net. (often used for audio files, so-called "Podcasts").

### \[pure virtual\] QString Item::id() const {#id}

returns an identifier that identifies the item within its feed. The ID must be unique within its feed. If no ID is provided by the feed source, a hash from title, description and content is returned.

Generated hash IDs start with "hash:".

### \[pure virtual\] QString Item::language() const {#language}

returns the language used in the item's content

TODO: tell about language codes and link them

### \[pure virtual\] QString Item::link() const {#link}

returns a link to the (web) resource described by this item. In most cases, this will be a website containing the full article associated with this item.

### \[pure virtual\] Syndication::SpecificItemPtr Item::specificItem() const {#specificItem}

Returns the format-specific item this object abstracts from.

Use it if you need to access format-specifics that are not covered by this abstraction.

### \[pure virtual\] QString Item::title() const {#title}

The title of the item.

This string may contain HTML markup.(Importantly, occurrences of the characters '\<', '\\n', '&', ''' and '"' are escaped).

Returns the title of the item as HTML, or a null string if not specified
