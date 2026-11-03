---
title: "Syndication::SpecificDocument Class"
description: "Document interface for format-specific feed documents as parsed from a document source (see DocumentSource)."
---

# Syndication::SpecificDocument Class

Document interface for format-specific feed documents as parsed from a document source (see [DocumentSource](syndication-documentsource.md)). [More...](#details)

- **Header:** `#include <Syndication/SpecificDocument>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS Syndication)`  
  `target_link_libraries(mytarget PRIVATE KF6::Syndication)`
- **Inherited By:** [Syndication::Atom::EntryDocument](syndication-atom-entrydocument.md) and [Syndication::Atom::FeedDocument](syndication-atom-feeddocument.md)

[List of all members, including inherited members](syndication-specificdocument-members.md)

## Public Functions

- [bool accept(Syndication::DocumentVisitor \*visitor)](#accept)
- [QString debugInfo() const](#debugInfo)
- [bool isValid() const](#isValid)

## Detailed Description {#details}

The Document classes from the several syndication formats must implement this interface. It's main purpose is to provide access for document visitors (see [DocumentVisitor](syndication-documentvisitor.md)).

Usually it is not necessary to access the format-specific document at all, use Feed for a format-agnostic interface to all feed documents supported by the library.

## Member Function Documentation {#member-function-documentation}

### \[pure virtual\] bool SpecificDocument::accept(Syndication::DocumentVisitor \**visitor*) {#accept}

This must be implemented for the double dispatch technique (Visitor pattern).

The usual implementation is

```cpp
return visitor->visit(this);
```

See also [DocumentVisitor](syndication-documentvisitor.md).

`visitor` the visitor "visiting" this object

### \[pure virtual\] QString SpecificDocument::debugInfo() const {#debugInfo}

Returns a description of the document for debugging purposes.

### \[pure virtual\] bool SpecificDocument::isValid() const {#isValid}

Returns whether this document is valid or not.

Invalid documents do not contain any useful information.
