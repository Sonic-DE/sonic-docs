---
title: "Syndication::SpecificItemVisitor Class"
description: "Visitor interface, following the Visitor design pattern."
---

# Syndication::SpecificItemVisitor Class

Visitor interface, following the Visitor design pattern. [More...](#details)

- **Header:** `#include <Syndication/SpecificItemVisitor>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS Syndication)`  
  `target_link_libraries(mytarget PRIVATE KF6::Syndication)`

[List of all members, including inherited members](syndication-specificitemvisitor-members.md)

## Public Functions

- [bool visit(Syndication::SpecificItem \*item)](#visit)
- [bool visitAtomEntry(Syndication::Atom::Entry \*item)](#visitAtomEntry)
- [bool visitRDFItem(Syndication::RDF::Item \*item)](#visitRDFItem)
- [bool visitRSS2Item(Syndication::RSS2::Item \*item)](#visitRSS2Item)

## Detailed Description {#details}

Use this if you want to process items and the way how to handle the items depends on it's concrete type (e.g. RSS2::Item, RDF::Item...).

TODO: insert code example

## Member Function Documentation {#member-function-documentation}

### \[virtual\] bool SpecificItemVisitor::visit(Syndication::SpecificItem \**item*) {#visit}

call this method to handle an item. Depending on the concrete type of the item, a specialized visit method is called.

`item` the item to process

Returns whether this visitor handles the type of the item

### \[virtual\] bool SpecificItemVisitor::visitAtomEntry(Syndication::Atom::Entry \**item*) {#visitAtomEntry}

reimplement this method to handle Atom entries.

`item` the Atom entry to visit

Returns whether the visitor handled the entry.

Reimplementations of this method must return `true`.

### \[virtual\] bool SpecificItemVisitor::visitRDFItem(Syndication::RDF::Item \**item*) {#visitRDFItem}

reimplement this method to handle RDF items.

`item` the RDF item to visit

Returns whether the visitor handled the item.

Reimplementations of this method must return `true`.

### \[virtual\] bool SpecificItemVisitor::visitRSS2Item(Syndication::RSS2::Item \**item*) {#visitRSS2Item}

reimplement this method to handle RSS2 items.

`item` the RSS2 item to visit

Returns whether the visitor handled the item.

Reimplementations of this method must return `true`.
