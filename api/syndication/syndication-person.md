---
title: "Syndication::Person Class"
description: "Person objects hold information about a person, such as the author of the content syndicated in the feed."
---

# Syndication::Person Class

Person objects hold information about a person, such as the author of the content syndicated in the feed. [More...](#details)

- **Header:** `#include <Syndication/Person>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS Syndication)`  
  `target_link_libraries(mytarget PRIVATE KF6::Syndication)`

[List of all members, including inherited members](syndication-person-members.md)

## Public Functions

- [QString debugInfo() const](#debugInfo)
- [QString email() const](#email)
- [bool isNull() const](#isNull)
- [QString name() const](#name)
- [QString uri() const](#uri)
- [bool Person::operator==(const Syndication::Person &other) const](#operator-eq-eq)

## Detailed Description {#details}

Depending on the feed format, different information is available.

While according to the RSS2 spec, RSS2 author elements must contain only an e-mail address, Atom requires the person's name and the e-mail address is optional. Also, in reality, feeds often contain other information than what is specified in the specs. Syndication tries to find out what author information is contained and maps it to this representation.

## Member Function Documentation {#member-function-documentation}

### \[virtual\] QString Person::debugInfo() const {#debugInfo}

description of the person for debugging purposes.

### \[pure virtual\] QString Person::email() const {#email}

e-mail address of the person (optional)

### \[pure virtual\] bool Person::isNull() const {#isNull}

returns whether this object is a null person

### \[pure virtual\] QString Person::name() const {#name}

Returns the name of the person as plain text, or a null string if not specified

### \[pure virtual\] QString Person::uri() const {#uri}

a URI associated with the person. (optional) This is usually the URL of the person's homepage.

### \[virtual\] bool Person::operator==(const Syndication::Person &*other*) const {#operator-eq-eq}

compares two person instances. Persons are equal if and only if their respective [name](syndication-person.md#name)(), [uri](syndication-person.md#uri)() and [email](syndication-person.md#email)() values are equal.

`other` another person instance
