---
title: "KSyntaxHighlighting::WildcardMatcher Namespace"
description: "Stand-alone implementation of the Kate syntax highlighting engine."
---

# KSyntaxHighlighting::WildcardMatcher Namespace

Stand-alone implementation of the Kate syntax highlighting engine. [More...](#details)

- Header: KSyntaxHighlighting/WildcardMatcher
- CMake: find\_package(KF6 REQUIRED COMPONENTS KSyntaxHighlighting) target\_link\_libraries(mytarget PRIVATE KF6::KSyntaxHighlighting)

## Detailed Description {#details}

## Function Documentation {#function-documentation}

### bool WildcardMatcher::exactMatch(QStringView *candidate*, QStringView *wildcard*) {#exactMatch}

Matches a string against a given wildcard case-sensitively. The wildcard supports '\*' (".\*" in regex) and '?' ("." in regex), not more.

`candidate` Text to match

`wildcard` Wildcard to use

Returns `true` for an exact match, false otherwise
