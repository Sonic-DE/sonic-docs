---
title: "Syndication::DocumentVisitor Class"
description: "Visitor interface, following the Visitor design pattern."
---

# Syndication::DocumentVisitor Class

Visitor interface, following the Visitor design pattern. [More...](#details)

- **Header:** `#include <Syndication/DocumentVisitor>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS Syndication)`  
  `target_link_libraries(mytarget PRIVATE KF6::Syndication)`

[List of all members, including inherited members](syndication-documentvisitor-members.md)

## Public Functions

- [bool visit(Syndication::SpecificDocument \*document)](#visit)
- [bool visitAtomEntryDocument(Syndication::Atom::EntryDocument \*document)](#visitAtomEntryDocument)
- [bool visitAtomFeedDocument(Syndication::Atom::FeedDocument \*document)](#visitAtomFeedDocument)
- [bool visitRDFDocument(Syndication::RDF::Document \*document)](#visitRDFDocument)
- [bool visitRSS2Document(Syndication::RSS2::Document \*document)](#visitRSS2Document)

## Detailed Description {#details}

Use this if you want to process documents and the way how to handle the document depends on it's concrete type (e.g. RSS2::Document, RDF::Document...).

TODO: insert code example

## Member Function Documentation {#member-function-documentation}

### \[virtual\] bool DocumentVisitor::visit(Syndication::SpecificDocument \**document*) {#visit}

Call this method to handle a document. Depending on the concrete type of the document, a specialized visit method is called.

`document` the document to process

Returns whether this visitor handles the type of the document.

### \[virtual\] bool DocumentVisitor::visitAtomEntryDocument(Syndication::Atom::EntryDocument \**document*) {#visitAtomEntryDocument}

Reimplement this method to handle Atom entry documents.

`document` the atom entry document to visit

Returns whether the visitor handled the document.

Reimplementations of this method must return `true`.

### \[virtual\] bool DocumentVisitor::visitAtomFeedDocument(Syndication::Atom::FeedDocument \**document*) {#visitAtomFeedDocument}

Reimplement this method to handle Atom feed documents (most Atom feeds are of this type).

`document` the atom feed document to visit

Returns whether the visitor handled the document.

Reimplementations of this method must return `true`.

### \[virtual\] bool DocumentVisitor::visitRDFDocument(Syndication::RDF::Document \**document*) {#visitRDFDocument}

Reimplement this method to handle RDF (i.e. RSS 1.0) documents.

`document` the RDF document to visit

Returns whether the visitor handled the document.

Reimplementations of this method must return `true`.

### \[virtual\] bool DocumentVisitor::visitRSS2Document(Syndication::RSS2::Document \**document*) {#visitRSS2Document}

Reimplement this method to handle RSS2-like (RSS 0.9x, 2.0) documents.

`document` the RSS2 document to visit

Returns whether the visitor handled the document.

Reimplementations of this method must return `true`.
