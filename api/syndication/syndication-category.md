---
title: "Syndication::Category Class"
description: "A category for categorizing items or whole feeds."
---

# Syndication::Category Class

A category for categorizing items or whole feeds. [More...](#details)

- **Header:** `#include <Syndication/Category>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS Syndication)`  
  `target_link_libraries(mytarget PRIVATE KF6::Syndication)`

[List of all members, including inherited members](syndication-category-members.md)

## Public Functions

- [QString debugInfo() const](#debugInfo)
- [bool isNull() const](#isNull)
- [QString label() const](#label)
- [QString scheme() const](#scheme)
- [QString term() const](#term)

## Detailed Description {#details}

A category can be an informal string set by the feed author ("General", "Stuff I like"), a tag assigned by readers, as known from flickr.com or de.licio.us ("KDE", "funny"), or a term from a formally defined ontology.

To represent the category in a user interface, use [label](syndication-category.md#label)() (or [term](syndication-category.md#term)() as fallback). To create a key for e.g. storage purposes, use [scheme](syndication-category.md#scheme)() + [term](syndication-category.md#term)().

## Member Function Documentation {#member-function-documentation}

### \[virtual\] QString Category::debugInfo() const {#debugInfo}

Description of the category for debugging purposes.

Returns debug string

### \[pure virtual\] bool Category::isNull() const {#isNull}

returns whether this object is a null category

### \[pure virtual\] QString Category::label() const {#label}

An optional human-readable label of the category.

If specified, this string should be used to represent this category in a user interface. If not specified, use [term](syndication-category.md#term)() instead.

TODO: specify format (HTML, plain text?) and enforce it in the impl

Returns the label of this category, or a null string if not specified

### \[pure virtual\] QString Category::scheme() const {#scheme}

An optional scheme the term is part of. This can be some vocabulary/ontology such as Dublin Core. Think of it as the term's namespace, grouping a set of categories. When managing categories, scheme() + [term](syndication-category.md#term)() identifies a category unambiguously and can be used as key.

Returns the scheme this category is part of, or a null string if not specified

### \[pure virtual\] QString Category::term() const {#term}

A term identifying the category, e.g. "general", "life", "books" or "Basketball & other sport I like". The term must be unique in its scheme (see [scheme](syndication-category.md#scheme)()).

In user interfaces, use it only if there is no [label](syndication-category.md#label)() available. TODO: specify format (HTML, plain text?) and enforce it in the impl

Returns category term. This string is never empty.
