---
title: "SignOn::AuthService::IdentityRegExp Class"
description: "The class represents a regular expression."
---

# SignOn::AuthService::IdentityRegExp Class

The class represents a regular expression. [More...](#details)

- **Header:** `#include <SignOn/AuthService>`
- **CMake:** `find_package(SignOnQt6 REQUIRED)`  
  `target_link_libraries(mytarget PRIVATE SignOnQt6::SignOnQt6)`

[List of all members, including inherited members](signon-authservice-identityregexp-members.md)

## Public Functions

- [IdentityRegExp(const QString &pattern)](#IdentityRegExp)
- [IdentityRegExp(const SignOn::AuthService::IdentityRegExp &src)](#IdentityRegExp-1)
- [bool isValid() const](#isValid)
- [QString pattern() const](#pattern)

## Detailed Description {#details}

It is used for filtering identity querying.

> **Note:** This is for internal use only.

*See also* [queryIdentities](signon-authservice.md#queryIdentities)()

## Member Function Documentation {#member-function-documentation}

### IdentityRegExp::IdentityRegExp(const QString &*pattern*) {#IdentityRegExp}

Constructor creates an [IdentityRegExp](signon-authservice-identityregexp.md), as specified by `pattern`, the regular expression as a string.

### IdentityRegExp::IdentityRegExp(const SignOn::AuthService::IdentityRegExp &*src*) {#IdentityRegExp-1}

Copy constructor, creates a copy of `src`.

### bool IdentityRegExp::isValid() const {#isValid}

Returns the validity of regular expression: always false, validity check not implemented.

### QString IdentityRegExp::pattern() const {#pattern}

Returns the pattern of this regular expression as string.
