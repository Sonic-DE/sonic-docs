---
title: "KSyntaxHighlighting::FoldingRegion Class"
description: "Represents a begin or end of a folding region."
---

# KSyntaxHighlighting::FoldingRegion Class

Represents a begin or end of a folding region. [More...](#details)

- **Header:** `#include <KSyntaxHighlighting/FoldingRegion>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS KSyntaxHighlighting)`  
  `target_link_libraries(mytarget PRIVATE KF6::KSyntaxHighlighting)`

[List of all members, including inherited members](ksyntaxhighlighting-foldingregion-members.md)

## Public Types

- [enum FoldingRegion::Type](#Type-enum)

## Public Functions

- [FoldingRegion()](#FoldingRegion)
- [int id() const](#id)
- [bool isValid() const](#isValid)
- [KSyntaxHighlighting::FoldingRegion sibling() const](#sibling) (since 6.0)
- [KSyntaxHighlighting::FoldingRegion::Type type() const](#type)
- [bool FoldingRegion::operator==(const KSyntaxHighlighting::FoldingRegion &other) const](#operator-eq-eq)

## Detailed Description {#details}

## Member Type Documentation {#member-type-documentation}

### enum FoldingRegion::Type {#Type-enum}

Defines whether a [FoldingRegion](ksyntaxhighlighting-foldingregion.md) starts or ends a folding region.

| Constant |   |
| --- | --- |
| `KSyntaxHighlighting::FoldingRegion::None` | `0` |
| `KSyntaxHighlighting::FoldingRegion::Begin` | `1` |
| `KSyntaxHighlighting::FoldingRegion::End` | `2` |

## Member Function Documentation {#member-function-documentation}

### FoldingRegion::FoldingRegion() {#FoldingRegion}

Constructs an invalid folding region, meaning that [isValid](ksyntaxhighlighting-foldingregion.md#isValid)() returns `false`. To obtain valid instances, see [AbstractHighlighter::applyFolding](ksyntaxhighlighting-abstracthighlighter.md#applyFolding)().

### int FoldingRegion::id() const {#id}

Returns a unique identifier for this folding region.

As example, the C/C++ highlighter starts and ends a folding region for scopes, e.g.:

```cpp
void foo() {     // '{' starts a folding region
    if (bar()) { // '{' starts a (nested) folding region
    }            // '}' ends the (nested) folding region
}                // '}' ends the outer folding region
```

In this example, all braces '{' and '}' have the same id(), meaning that if you want to find the matching closing region for the first opening brace, you need to do kind of a reference counting to find the correct closing brace.

### bool FoldingRegion::isValid() const {#isValid}

Returns `true` if this is a valid folding region. A valid [FoldingRegion](ksyntaxhighlighting-foldingregion.md) is defined by a [type](ksyntaxhighlighting-foldingregion.md#type)() other than [Type::None](ksyntaxhighlighting-foldingregion.md#Type-enum).

> **Note:** The [FoldingRegion](ksyntaxhighlighting-foldingregion.md)%s passed in [AbstractHighlighter::applyFolding](ksyntaxhighlighting-abstracthighlighter.md#applyFolding)() are always valid.

### \[since 6.0\] KSyntaxHighlighting::FoldingRegion FoldingRegion::sibling() const {#sibling}

Returns the matching start or end region.

> **Note:** Will return invalid region for an invalid region.

This function was introduced in Qt 6.0.

### KSyntaxHighlighting::FoldingRegion::Type FoldingRegion::type() const {#type}

Returns whether this is the begin or end of a region.

> **Note:** The [FoldingRegion](ksyntaxhighlighting-foldingregion.md)%s passed in [AbstractHighlighter::applyFolding](ksyntaxhighlighting-abstracthighlighter.md#applyFolding)() are always valid, i.e. either [Type::Begin](ksyntaxhighlighting-foldingregion.md#Type-enum) or [Type::End](ksyntaxhighlighting-foldingregion.md#Type-enum).

### bool FoldingRegion::operator==(const KSyntaxHighlighting::FoldingRegion &*other*) const {#operator-eq-eq}

Compares two [FoldingRegion](ksyntaxhighlighting-foldingregion.md) instances for equality.
