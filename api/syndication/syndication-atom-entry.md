---
title: "Syndication::Atom::Entry Class"
description: "An Atom entry, equivalent to the \"items\" in the RSS world."
---

# Syndication::Atom::Entry Class

An Atom entry, equivalent to the "items" in the RSS world. [More...](#details)

- **Header:** `#include <Syndication/Atom/Entry>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS Syndication)`  
  `target_link_libraries(mytarget PRIVATE KF6::Syndication)`
- **Inherits:** [Syndication::ElementWrapper](syndication-elementwrapper.md) and [Syndication::SpecificItem](syndication-specificitem.md)

[List of all members, including inherited members](syndication-atom-entry-members.md)

## Public Functions

- [Entry()](#Entry)
- [Entry(const QDomElement &element)](#Entry-1)
- [bool accept(Syndication::SpecificItemVisitor \*visitor)](#accept)
- [QList\<Syndication::Atom::Person\> authors() const](#authors)
- [QList\<Syndication::Atom::Category\> categories() const](#categories)
- [Syndication::Atom::Content content() const](#content)
- [QList\<Syndication::Atom::Person\> contributors() const](#contributors)
- [QString debugInfo() const](#debugInfo)
- [QString id() const](#id)
- [QList\<Syndication::Atom::Link\> links() const](#links)
- [time\_t published() const](#published)
- [QString rights() const](#rights)
- [void setFeedAuthors(const QList\<Syndication::Atom::Person\> &feedAuthors)](#setFeedAuthors)
- [Syndication::Atom::Source source() const](#source)
- [QString summary() const](#summary)
- [QString title() const](#title)
- [QList\<QDomElement\> unhandledElements() const](#unhandledElements)
- [time\_t updated() const](#updated)

## Detailed Description {#details}

## Member Function Documentation {#member-function-documentation}

### Entry::Entry() {#Entry}

creates a null entry object

### \[explicit\] Entry::Entry(const QDomElement &*element*) {#Entry-1}

creates an Entry object wrapping an atom:entry element.

`element` a DOM element, should be a atom:entry element (although not enforced), otherwise this object will not parse anything useful

### \[override virtual\] bool Entry::accept(Syndication::SpecificItemVisitor \**visitor*) {#accept}

Reimplements: [SpecificItem::accept(Syndication::SpecificItemVisitor \*visitor)](syndication-specificitem.md#accept).

Used by visitors for double dispatch. See SpecificVisitor for more information.

`visitor` the visitor calling the method

### QList\<Syndication::Atom::Person\> Entry::authors() const {#authors}

list of persons who are authors of this entry. (required)

If the entry itself does not have explicit author description, its source author description is used. If none of these exist, the list of authors of the containing feed is used. That list is set by [setFeedAuthors](syndication-atom-entry.md#setFeedAuthors)().

### QList\<Syndication::Atom::Category\> Entry::categories() const {#categories}

a list of categories this entry is filed to (optional)

### Syndication::Atom::Content Entry::content() const {#content}

content of the entry (optional) See Content for details

Returns entry content, or a null content object if not specified

### QList\<Syndication::Atom::Person\> Entry::contributors() const {#contributors}

list of persons contributing to this entry (optional)

### QString Entry::debugInfo() const {#debugInfo}

returns a description of this entry for debugging purposes

Returns debug string

### QString Entry::id() const {#id}

ID of the article. (required) The ID must be unique inside this feed. The atom spec defines it as a URI (which is not enforced by this parser)

### QList\<Syndication::Atom::Link\> Entry::links() const {#links}

links pointing to associated web sites and other resources.

Links are optional if the entry provides Content. Otherwise, it must contain at least one link with a `rel` value of `"alternate"`. (see Link).

### time\_t Entry::published() const {#published}

The datetime of the publication of this entry (optional).

Returns the publication date in seconds since epoch

### QString Entry::rights() const {#rights}

copyright information (optional)

Returns copyright information for the entry (intended for human readers), or a null string if not specified

### void Entry::setFeedAuthors(const QList\<Syndication::Atom::Person\> &*feedAuthors*) {#setFeedAuthors}

Sets the list of the containing feed's authors, which will be used as a fallback in [authors](syndication-atom-entry.md#authors)() in case both the entry itself and its source have no explicit author description.

`feedAuthors` the list of feed's authors

### Syndication::Atom::Source Entry::source() const {#source}

source description of the content (optional)

If the content was copied from another feed, this object contains information about the source feed.

Returns source description, or a null object if not specified

### QString Entry::summary() const {#summary}

a short summary, abstract or excerpt of an entry. (optional) This is usually more verbose than [title](syndication-atom-entry.md#title)() and but does not contain the whole content as [content](syndication-atom-entry.md#content)() does.

Returns the summary as HTML, or a null string if not specified

### QString Entry::title() const {#title}

title of the entry (required).

Returns the title as HTML

### QList\<QDomElement\> Entry::unhandledElements() const {#unhandledElements}

returns all child elements of this entry not covered by this class. This can be used to access additional metadata from Atom extensions.

### time\_t Entry::updated() const {#updated}

The datetime of the last modification of this entry (required).

Returns the modification date in seconds since epoch
