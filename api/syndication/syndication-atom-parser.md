---
title: "Syndication::Atom::Parser Class"
description: "parser implementation for Atom 1.0 and 0.3."
---

# Syndication::Atom::Parser Class

parser implementation for Atom 1.0 and 0.3. [More...](#details)

- **Header:** `#include <Syndication/Atom/Parser>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS Syndication)`  
  `target_link_libraries(mytarget PRIVATE KF6::Syndication)`
- **Inherits:** [Syndication::AbstractParser](syndication-abstractparser.md)

[List of all members, including inherited members](syndication-atom-parser-members.md)

## Public Functions

- [Parser()](#Parser)
- [bool accept(const Syndication::DocumentSource &source) const](#accept)
- [QString format() const](#format)
- [Syndication::SpecificDocumentPtr parse(const Syndication::DocumentSource &source) const](#parse)

## Detailed Description {#details}

## Member Function Documentation {#member-function-documentation}

### Parser::Parser() {#Parser}

default constructor

### \[override virtual\] bool Parser::accept(const Syndication::DocumentSource &*source*) const {#accept}

Reimplements: [AbstractParser::accept(const Syndication::DocumentSource &source) const](syndication-abstractparser.md#accept).

returns whether the source looks like an Atom 1.0 or 0.3 document, by checking the root element.

`source` document source to check

### \[override virtual\] QString Parser::format() const {#format}

Reimplements: [AbstractParser::format() const](syndication-abstractparser.md#format).

returns the format string for this parser implementation, which is `"atom"`

Returns `"atom"`

### \[override virtual\] Syndication::SpecificDocumentPtr Parser::parse(const Syndication::DocumentSource &*source*) const {#parse}

Reimplements: [AbstractParser::parse(const Syndication::DocumentSource &source) const](syndication-abstractparser.md#parse).

parses either an [EntryDocument](syndication-atom-entrydocument.md) or a [FeedDocument](syndication-atom-feeddocument.md) from a document source. If the source is not an atom document, an invalid [FeedDocument](syndication-atom-feeddocument.md) is returned.

`source` the document source to parse

*See also* [SpecificDocument::isValid](syndication-specificdocument.md#isValid)()
