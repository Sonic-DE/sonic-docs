---
title: "Syndication C++ Classes"
description: "RSS/Atom parser library."
---

# Syndication C++ Classes

RSS/Atom parser library. [More...](#details)

## Namespaces {#namespaces}

- [Syndication](syndication.md)
- [Syndication::Atom](syndication-atom.md): Atom parser and model classes, representing Atom 1.0 documents.

## Classes {#classes}

- [Syndication::AbstractParser](syndication-abstractparser.md): Interface for all parsers.
- [Syndication::Atom::Content](syndication-atom-content.md): The content element either contains or links the content of an entry.
- [Syndication::Atom::Entry](syndication-atom-entry.md): An Atom entry, equivalent to the "items" in the RSS world.
- [Syndication::Atom::EntryDocument](syndication-atom-entrydocument.md): An Atom 1.0 Entry Document, containing a single Atom entry outside of the context of a feed.
- [Syndication::Atom::FeedDocument](syndication-atom-feeddocument.md): An Atom 1.0 Feed Document, containing metadata describing the feed and a number of entries.
- [Syndication::Atom::Generator](syndication-atom-generator.md): Description of the agent used to generate the feed.
- [Syndication::Atom::Link](syndication-atom-link.md): A link, pointing to webpages, media files on the web ("podcast"), related content, etc. See rel() for details.
- [Syndication::Atom::Parser](syndication-atom-parser.md): parser implementation for Atom 1.0 and 0.3.
- [Syndication::Atom::Source](syndication-atom-source.md): If an entry was copied from another feed, this class contains a description of the source feed.
- [Syndication::Category](syndication-category.md): A category for categorizing items or whole feeds.
- [Syndication::DataRetriever](syndication-dataretriever.md): Abstract baseclass for all data retriever classes.
- [Syndication::DocumentSource](syndication-documentsource.md): Represents the source of a syndication document, as read from the downloaded file.
- [Syndication::DocumentVisitor](syndication-documentvisitor.md): Visitor interface, following the Visitor design pattern.
- [Syndication::ElementWrapper](syndication-elementwrapper.md): A wrapper for XML elements.
- [Syndication::Enclosure](syndication-enclosure.md): An enclosure describes a (media) file available on the net.
- [Syndication::Feed](syndication-feed.md): This class represents a feed document ("Channel" in RSS, "Feed" in Atom).
- [Syndication::Image](syndication-image.md): This class represents an image file on the web.
- [Syndication::Item](syndication-item.md): An item from a news feed.
- [Syndication::Loader](syndication-loader.md): This class is the preferred way of loading feed sources.
- [Syndication::Mapper](syndication-mapper.md): A mapper maps an SpecificDocument to something else.
- [Syndication::ParserCollection](syndication-parsercollection.md): A collection of format-specific parser implementations.
- [Syndication::Person](syndication-person.md): Person objects hold information about a person, such as the author of the content syndicated in the feed.
- [Syndication::SpecificDocument](syndication-specificdocument.md): Document interface for format-specific feed documents as parsed from a document source (see DocumentSource).
- [Syndication::SpecificItem](syndication-specificitem.md): Interface for all format-specific item-like classes, such as RSS2/RDF items, and Atom entries.
- [Syndication::SpecificItemVisitor](syndication-specificitemvisitor.md): Visitor interface, following the Visitor design pattern.

## Detailed Description {#details}

RSS (0.9/1.0, 0.91..2.0) and Atom (0.3 and 1.0) feeds are supported.

Syndication offers a unified, format-agnostic view on the parsed feed, so that the using application does not need to distinguish between feed formats.
