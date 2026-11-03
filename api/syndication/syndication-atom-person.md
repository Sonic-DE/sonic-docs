---
title: "Syndication::Atom::Person Class"
description: "describes a person, with name and optional URI and e-mail address. Used to describe authors and contributors of feeds/entries."
---

# Syndication::Atom::Person Class

describes a person, with name and optional URI and e-mail address. Used to describe authors and contributors of feeds/entries. [More...](#details)

- **Header:** `#include <Syndication/Atom/Person>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS Syndication)`  
  `target_link_libraries(mytarget PRIVATE KF6::Syndication)`
- **Inherits:** [Syndication::ElementWrapper](syndication-elementwrapper.md)

[List of all members, including inherited members](syndication-atom-person-members.md)

## Public Functions

- [Person()](#Person)
- [Person(const QDomElement &element)](#Person-1)
- [QString debugInfo() const](#debugInfo)
- [QString email() const](#email)
- [QString name() const](#name)
- [QString uri() const](#uri)

## Detailed Description {#details}

## Member Function Documentation {#member-function-documentation}

### Person::Person() {#Person}

creates a null person object

### \[explicit\] Person::Person(const QDomElement &*element*) {#Person-1}

creates a Person object wrapping an Atom Person Construct (atom:author, atom:contributor tags)

`element` a DOM element, should be a Atom Person Construct (although not enforced), otherwise this object will not parse anything useful

### QString Person::debugInfo() const {#debugInfo}

description for debugging purposes

Returns debug string

### QString Person::email() const {#email}

returns an e-mail address associated with the person. (optional)

Returns an e-mail address, or a null string if not specified

### QString Person::name() const {#name}

a human-readable name for the person. (required) The name is a required attribute of person constructs.

Returns a human-readable name of the person

### QString Person::uri() const {#uri}

A URI associated with the person (optional). Usually the homepage.

Returns the URI of the person, or a null string if not specified
