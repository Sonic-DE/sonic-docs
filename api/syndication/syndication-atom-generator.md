---
title: "Syndication::Atom::Generator Class"
description: "Description of the agent used to generate the feed."
---

# Syndication::Atom::Generator Class

Description of the agent used to generate the feed. [More...](#details)

- **Header:** `#include <Syndication/Atom/Generator>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS Syndication)`  
  `target_link_libraries(mytarget PRIVATE KF6::Syndication)`
- **Inherits:** [Syndication::ElementWrapper](syndication-elementwrapper.md)

[List of all members, including inherited members](syndication-atom-generator-members.md)

## Public Functions

- [Generator()](#Generator)
- [Generator(const QDomElement &element)](#Generator-1)
- [QString debugInfo() const](#debugInfo)
- [QString name() const](#name)
- [QString uri() const](#uri)
- [QString version() const](#version)

## Detailed Description {#details}

## Member Function Documentation {#member-function-documentation}

### Generator::Generator() {#Generator}

default constructor, creates a null generator

### \[explicit\] Generator::Generator(const QDomElement &*element*) {#Generator-1}

creates a Generator wrapping an atom:generator element.

`element` a DOM element, should be a atom:generator element (although not enforced), otherwise this object will not parse anything useful

### QString Generator::debugInfo() const {#debugInfo}

a description of this generator for debugging purposes.

### QString Generator::name() const {#name}

human-readable name of the generator. (optional)

### QString Generator::uri() const {#uri}

A URI for the generator (e.g. its homepage) (optional)

### QString Generator::version() const {#version}

version of the agent (optional)
