---
title: "Syndication::AbstractParser Class"
description: "Interface for all parsers."
---

# Syndication::AbstractParser Class

Interface for all parsers. [More...](#details)

- **Header:** `#include <Syndication/AbstractParser>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS Syndication)`  
  `target_link_libraries(mytarget PRIVATE KF6::Syndication)`
- **Inherited By:** [Syndication::Atom::Parser](syndication-atom-parser.md)

[List of all members, including inherited members](syndication-abstractparser-members.md)

## Public Functions

- [bool accept(const Syndication::DocumentSource &source) const](#accept)
- [QString format() const](#format)
- [Syndication::SpecificDocumentPtr parse(const Syndication::DocumentSource &source) const](#parse)

## Detailed Description {#details}

The parsers for the various formats must implement this interface and register themselves at the ParserRegistry.

## Member Function Documentation {#member-function-documentation}

### \[pure virtual\] bool AbstractParser::accept(const Syndication::DocumentSource &*source*) const {#accept}

Lets the parser check if it can parse the passed source.

Parser implementations should do a \_quick\_ check for the file format (i.e. check for feed format and version number in the root element) to find out if the source is in a supported format. They should \_not\_ completely parse the document to test for full compliance to the format specification.

`source` the document source to be checked

Returns whether `source` seems to be in a format supported by the parser

### \[pure virtual\] QString AbstractParser::format() const {#format}

Returns the name of the format supported by this parser.

Returns a string like "rss2", "atom" or "rdf"

### \[pure virtual\] Syndication::SpecificDocumentPtr AbstractParser::parse(const Syndication::DocumentSource &*source*) const {#parse}

Lets the parser parse a document source.

The parser returns a valid document instance if successful, or an invalid one if not.

`source` The document source to be parsed

Returns a newly created document parsed from `source`

*See also* [SpecificDocument::isValid](syndication-specificdocument.md#isValid)()
