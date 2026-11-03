---
title: "KSyntaxHighlighting::State Class"
description: "Opaque handle to the state of the highlighting engine."
---

# KSyntaxHighlighting::State Class

Opaque handle to the state of the highlighting engine. [More...](#details)

- **Header:** `#include <KSyntaxHighlighting/State>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS KSyntaxHighlighting)`  
  `target_link_libraries(mytarget PRIVATE KF6::KSyntaxHighlighting)`

[List of all members, including inherited members](ksyntaxhighlighting-state-members.md)

## Public Functions

- [State()](#State)
- [bool indentationBasedFoldingEnabled() const](#indentationBasedFoldingEnabled)
- [bool State::operator!=(const KSyntaxHighlighting::State &other) const](#operator-not-eq)
- [bool State::operator==(const KSyntaxHighlighting::State &other) const](#operator-eq-eq)

## Detailed Description {#details}

This needs to be fed into [AbstractHighlighter](ksyntaxhighlighting-abstracthighlighter.md) for every line of text and allows concrete highlighter implementations to store state per line for fast re-highlighting of specific lines (e.g. during editing).

## Member Function Documentation {#member-function-documentation}

### State::State() {#State}

Creates an initial state, ie. what should be used for the first line in a document.

### bool State::indentationBasedFoldingEnabled() const {#indentationBasedFoldingEnabled}

Returns whether or not indentation-based folding is enabled in this state. When using a Definition with indentation-based folding, use this method to check if indentation-based folding has been suspended in the current line.

*See also* [Definition::indentationBasedFoldingEnabled](ksyntaxhighlighting-definition.md#indentationBasedFoldingEnabled)()

### bool State::operator!=(const KSyntaxHighlighting::State &*other*) const {#operator-not-eq}

Compares two states for inequality. This is the opposite of operator==().

### bool State::operator==(const KSyntaxHighlighting::State &*other*) const {#operator-eq-eq}

Compares two states for equality. For two equal states and identical text input, [AbstractHighlighter](ksyntaxhighlighting-abstracthighlighter.md) guarantees to produce equal results. This can be used to only re-highlight as many lines as necessary during editing.
