---
title: "Syndication::Atom::Category Class"
description: "A category for categorizing items or whole feeds."
---

# Syndication::Atom::Category Class

A category for categorizing items or whole feeds. [More...](#details)

- **Header:** `#include <Syndication/Atom/Category>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS Syndication)`  
  `target_link_libraries(mytarget PRIVATE KF6::Syndication)`
- **Inherits:** [Syndication::ElementWrapper](syndication-elementwrapper.md)

[List of all members, including inherited members](syndication-atom-category-members.md)

## Public Functions

- [Category()](#Category)
- [Category(const QDomElement &element)](#Category-1)
- [QString debugInfo() const](#debugInfo)
- [QString label() const](#label)
- [QString scheme() const](#scheme)
- [QString term() const](#term)

## Detailed Description {#details}

A category can be an informal string set by the feed author ("General", "Stuff I like"), a tag assigned by readers, as known from flickr.com or de.licio.us ("KDE", "funny"), or a term from a formally defined ontology.

To represent the category in a user interface, use [label](syndication-atom-category.md#label)() (or [term](syndication-atom-category.md#term)() as fallback). To create a key for e.g. storage purposes, use [scheme](syndication-atom-category.md#scheme)() + [term](syndication-atom-category.md#term)().

## Member Function Documentation {#member-function-documentation}

### Category::Category() {#Category}

creates a null category object.

### \[explicit\] Category::Category(const QDomElement &*element*) {#Category-1}

creates a Category object wrapping an atom:category element.

`element` a DOM element, should be a atom:category element (although not enforced), otherwise this object will not parse anything useful

### QString Category::debugInfo() const {#debugInfo}

description of this category object for debugging purposes

### QString Category::label() const {#label}

Label of the category (optional).

If specified, this string should be used to represent this category in a user interface.

If not specified, use [term](syndication-atom-category.md#term)() instead.

Returns the label as plain text (no HTML, "&", "\<" etc. are unescaped!), or a null string if not specified

### QString Category::scheme() const {#scheme}

naming scheme the category term is part of. (optional)

A term is unique in its scheme (like in C++ identifiers are unique in their namespaces)

Returns a URI representing the scheme, or a null string if not specified

### QString Category::term() const {#term}

a term describing the category. (required)

Returns the category term as plain text (no HTML, "&", "\<" etc. are unescaped!)
