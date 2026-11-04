---
title: "Syndication::Atom Namespace"
description: "Atom parser and model classes, representing Atom 1.0 documents."
---

# Syndication::Atom Namespace

Atom parser and model classes, representing Atom 1.0 documents. [More...](#details)

- **Header:** `#include <Atom>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS Syndication)`  
  `target_link_libraries(mytarget PRIVATE KF6::Syndication)`

## Detailed Description {#details}

(Atom 0.3 documents are converted by the parser)

## Classes {#classes}

### class [Category](syndication-atom-category.md)

A category for categorizing items or whole feeds.

### class [Content](syndication-atom-content.md)

The content element either contains or links the content of an entry.

### class [Entry](syndication-atom-entry.md)

An Atom entry, equivalent to the "items" in the RSS world.

### class [EntryDocument](syndication-atom-entrydocument.md)

An Atom 1.0 Entry Document, containing a single Atom entry outside of the context of a feed.

### class [FeedDocument](syndication-atom-feeddocument.md)

An Atom 1.0 Feed Document, containing metadata describing the feed and a number of entries.

### class [Generator](syndication-atom-generator.md)

Description of the agent used to generate the feed.

### class [Link](syndication-atom-link.md)

A link, pointing to webpages, media files on the web ("podcast"), related content, etc. See [rel](syndication-atom-link.md#rel)() for details.

### class [Parser](syndication-atom-parser.md)

parser implementation for Atom 1.0 and 0.3.

### class [Person](syndication-atom-person.md)

describes a person, with name and optional URI and e-mail address. Used to describe authors and contributors of feeds/entries.

### class [Source](syndication-atom-source.md)

If an entry was copied from another feed, this class contains a description of the source feed.

## Function Documentation {#function-documentation}

### QString Atom::atom0\_3Namespace() {#atom0_3Namespace}

namespace used by Atom 0.3 elements

### QString Atom::atom1Namespace() {#atom1Namespace}

namespace used by Atom 1.0 elements
