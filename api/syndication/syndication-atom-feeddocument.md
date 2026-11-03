---
title: "Syndication::Atom::FeedDocument Class"
description: "An Atom 1.0 Feed Document, containing metadata describing the feed and a number of entries."
---

# Syndication::Atom::FeedDocument Class

An Atom 1.0 Feed Document, containing metadata describing the feed and a number of entries. [More...](#details)

- **Header:** `#include <Syndication/Atom/FeedDocument>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS Syndication)`  
  `target_link_libraries(mytarget PRIVATE KF6::Syndication)`
- **Inherits:** [Syndication::SpecificDocument](syndication-specificdocument.md) and [Syndication::ElementWrapper](syndication-elementwrapper.md)

[List of all members, including inherited members](syndication-atom-feeddocument-members.md)

## Public Functions

- [FeedDocument()](#FeedDocument)
- [FeedDocument(const QDomElement &element)](#FeedDocument-1)
- [bool accept(Syndication::DocumentVisitor \*visitor)](#accept)
- [QList\<Syndication::Atom::Person\> authors() const](#authors)
- [QList\<Syndication::Atom::Category\> categories() const](#categories)
- [QList\<Syndication::Atom::Person\> contributors() const](#contributors)
- [QString debugInfo() const](#debugInfo)
- [QList\<Syndication::Atom::Entry\> entries() const](#entries)
- [Syndication::Atom::Generator generator() const](#generator)
- [QString icon() const](#icon)
- [QString id() const](#id)
- [bool isValid() const](#isValid)
- [QList\<Syndication::Atom::Link\> links() const](#links)
- [QString logo() const](#logo)
- [QString rights() const](#rights)
- [QString subtitle() const](#subtitle)
- [QString title() const](#title)
- [QList\<QDomElement\> unhandledElements() const](#unhandledElements)
- [time\_t updated() const](#updated)

## Detailed Description {#details}

## Member Function Documentation {#member-function-documentation}

### FeedDocument::FeedDocument() {#FeedDocument}

default constructor, creates a null feed, which is invalid.

*See also* [isValid](syndication-atom-feeddocument.md#isValid)()

### \[explicit\] FeedDocument::FeedDocument(const QDomElement &*element*) {#FeedDocument-1}

creates a [FeedDocument](syndication-atom-feeddocument.md) wrapping an atom:feed element.

`element` a DOM element, should be a atom:feed document (although not enforced), otherwise this object will not parse anything useful

### \[override virtual\] bool FeedDocument::accept(Syndication::DocumentVisitor \**visitor*) {#accept}

Reimplements: [SpecificDocument::accept(Syndication::DocumentVisitor \*visitor)](syndication-specificdocument.md#accept).

Used by visitors for double dispatch. See [DocumentVisitor](syndication-documentvisitor.md) for more information.

`visitor` the visitor calling the method

### QList\<Syndication::Atom::Person\> FeedDocument::authors() const {#authors}

a list of persons who are the authors of this feed.

According to the Atom 1.0 spec, a feed must have an author unless all entries in it have one.

### QList\<Syndication::Atom::Category\> FeedDocument::categories() const {#categories}

a list of categories this feed is assigned to (optional)

### QList\<Syndication::Atom::Person\> FeedDocument::contributors() const {#contributors}

a list of persons who contribute to this feed. (optional)

### \[override virtual\] QString FeedDocument::debugInfo() const {#debugInfo}

Reimplements: [SpecificDocument::debugInfo() const](syndication-specificdocument.md#debugInfo).

returns a description of this feed document for debugging purposes.

### QList\<Syndication::Atom::Entry\> FeedDocument::entries() const {#entries}

a list of the entries (items) in this feed.

### Syndication::Atom::Generator FeedDocument::generator() const {#generator}

description of the agent used to generate the feed. See Generator for more information (optional).

Returns description of the generator, or a null Generator object if not specified in the feed.

### QString FeedDocument::icon() const {#icon}

URL of an image serving as a feed icon (optional)

### QString FeedDocument::id() const {#id}

a string that unambiguously identifies the feed (required)

Returns the ID of the feed. As defined in the Atom spec it must be a valid URI (which is neither checked nor enforced by this parser)

### \[override virtual\] bool FeedDocument::isValid() const {#isValid}

Reimplements: [SpecificDocument::isValid() const](syndication-specificdocument.md#isValid).

returns whether this document is valid or not. Invalid documents do not contain any useful information.

### QList\<Syndication::Atom::Link\> FeedDocument::links() const {#links}

a list of links. See Link for more information on link types.

### QString FeedDocument::logo() const {#logo}

URL of an image serving as a feed logo (optional)

### QString FeedDocument::rights() const {#rights}

copyright information (optional)

Returns copyright information for the feed (intended for human readers), or a null string if not specified

### QString FeedDocument::subtitle() const {#subtitle}

description or subtitle of the feed (optional).

Returns subtitle string as HTML, or a null string if not specified in the feed.

### QString FeedDocument::title() const {#title}

feed title (required).

Returns title string as HTML.

### QList\<QDomElement\> FeedDocument::unhandledElements() const {#unhandledElements}

returns all child elements of this feed not covered by this class. This can be used to access additional metadata from Atom extensions.

### time\_t FeedDocument::updated() const {#updated}

The datetime of the last modification of the feed content.

Returns the modification date in seconds since epoch
