---
title: "Syndication::Atom::EntryDocument Class"
description: "An Atom 1.0 Entry Document, containing a single Atom entry outside of the context of a feed."
---

# Syndication::Atom::EntryDocument Class

An Atom 1.0 Entry Document, containing a single Atom entry outside of the context of a feed. [More...](#details)

- **Header:** `#include <Syndication/Atom/EntryDocument>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS Syndication)`  
  `target_link_libraries(mytarget PRIVATE KF6::Syndication)`
- **Inherits:** [Syndication::SpecificDocument](syndication-specificdocument.md) and [Syndication::ElementWrapper](syndication-elementwrapper.md)

[List of all members, including inherited members](syndication-atom-entrydocument-members.md)

## Public Functions

- [EntryDocument()](#EntryDocument)
- [EntryDocument(const QDomElement &element)](#EntryDocument-1)
- [bool accept(Syndication::DocumentVisitor \*visitor)](#accept)
- [QString debugInfo() const](#debugInfo)
- [Syndication::Atom::Entry entry() const](#entry)
- [bool isValid() const](#isValid)

## Detailed Description {#details}

## Member Function Documentation {#member-function-documentation}

### EntryDocument::EntryDocument() {#EntryDocument}

default constructor, creates a null document, which is invalid.

*See also* [isValid](syndication-atom-entrydocument.md#isValid)()

### \[explicit\] EntryDocument::EntryDocument(const QDomElement &*element*) {#EntryDocument-1}

creates an Atom Entry Document wrapping an atom:entry element.

`element` a DOM element, should be a atom:entry element (although not enforced), otherwise this object will not parse anything useful

### \[override virtual\] bool EntryDocument::accept(Syndication::DocumentVisitor \**visitor*) {#accept}

Reimplements: [SpecificDocument::accept(Syndication::DocumentVisitor \*visitor)](syndication-specificdocument.md#accept).

Used by visitors for double dispatch. See [DocumentVisitor](syndication-documentvisitor.md) for more information.

`visitor` the visitor calling the method

### \[override virtual\] QString EntryDocument::debugInfo() const {#debugInfo}

Reimplements: [SpecificDocument::debugInfo() const](syndication-specificdocument.md#debugInfo).

returns a description of this entry document for debugging purposes.

### Syndication::Atom::Entry EntryDocument::entry() const {#entry}

returns the single entry described in the source.

### \[override virtual\] bool EntryDocument::isValid() const {#isValid}

Reimplements: [SpecificDocument::isValid() const](syndication-specificdocument.md#isValid).

returns whether this document is valid or not.

Invalid documents do not contain any useful information.
