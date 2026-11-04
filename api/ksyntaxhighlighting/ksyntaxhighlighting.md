---
title: "KSyntaxHighlighting Namespace"
description: "Syntax highlighting engine for Kate syntax definitions."
---

# KSyntaxHighlighting Namespace

Syntax highlighting engine for Kate syntax definitions. [More...](#details)

- **Header:** `#include <KSyntaxHighlighting>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS KSyntaxHighlighting)`  
  `target_link_libraries(mytarget PRIVATE KF6::KSyntaxHighlighting)`

## Detailed Description {#details}

In order to access the syntax highlighting Definition files, use the class Repository.

## Namespaces {#namespaces}

### namespace KSyntaxHighlighting::WildcardMatcher

## Classes {#classes}

### class [AbstractHighlighter](ksyntaxhighlighting-abstracthighlighter.md)

Abstract base class for highlighters.

### class [Definition](ksyntaxhighlighting-definition.md)

### class [DefinitionDownloader](ksyntaxhighlighting-definitiondownloader.md)

Helper class to download definition file updates.

### class [FoldingRegion](ksyntaxhighlighting-foldingregion.md)

Represents a begin or end of a folding region.

### class [Format](ksyntaxhighlighting-format.md)

Describes the format to be used for a specific text fragment. The actual format used for displaying is merged from the format information in the syntax definition file, and a theme.

### class [Repository](ksyntaxhighlighting-repository.md)

Syntax highlighting repository.

### class [State](ksyntaxhighlighting-state.md)

Opaque handle to the state of the highlighting engine.

### class [SyntaxHighlighter](ksyntaxhighlighting-syntaxhighlighter.md)

A [QSyntaxHighlighter](https://doc.qt.io/qt-6/qsyntaxhighlighter.html) implementation for use with [QTextDocument](https://doc.qt.io/qt-6/qtextdocument.html). This supports partial re-highlighting during editing and tracks syntax-based code folding regions.

### class [Theme](ksyntaxhighlighting-theme.md)

Color theme definition used for highlighting.

## Type Documentation {#type-documentation}

### enum KSyntaxHighlighting::CommentPosition {#CommentPosition-enum}

Defines the insert position when commenting code.

| Constant |   |
| --- | --- |
| `KSyntaxHighlighting::CommentPosition::StartOfLine` | `0` |
| `KSyntaxHighlighting::CommentPosition::AfterWhitespace` | `1` |

*See also* [Definition::singleLineCommentPosition](ksyntaxhighlighting-definition.md#singleLineCommentPosition)()
