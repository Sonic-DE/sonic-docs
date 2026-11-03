---
title: "KSyntaxHighlighting C++ Classes"
description: "KSyntaxHighlighting is a stand-alone implementation of the Kate syntax highlighting engine."
---

# KSyntaxHighlighting C++ Classes

[KSyntaxHighlighting](ksyntaxhighlighting-module.md) is a stand-alone implementation of the Kate syntax highlighting engine. [More...](#details)

## Namespaces {#namespaces}

- [KSyntaxHighlighting](ksyntaxhighlighting.md): Syntax highlighting engine for Kate syntax definitions.
- [KSyntaxHighlighting::WildcardMatcher](ksyntaxhighlighting-wildcardmatcher.md)

## Classes {#classes}

- [KSyntaxHighlighting::AbstractHighlighter](ksyntaxhighlighting-abstracthighlighter.md): Abstract base class for highlighters.
- [KSyntaxHighlighting::Definition](ksyntaxhighlighting-definition.md)
- [KSyntaxHighlighting::DefinitionDownloader](ksyntaxhighlighting-definitiondownloader.md): Helper class to download definition file updates.
- [KSyntaxHighlighting::FoldingRegion](ksyntaxhighlighting-foldingregion.md): Represents a begin or end of a folding region.
- [KSyntaxHighlighting::Format](ksyntaxhighlighting-format.md): Describes the format to be used for a specific text fragment. The actual format used for displaying is merged from the format information in the syntax definition file, and a theme.
- [KSyntaxHighlighting::Repository](ksyntaxhighlighting-repository.md): Syntax highlighting repository.
- [KSyntaxHighlighting::State](ksyntaxhighlighting-state.md): Opaque handle to the state of the highlighting engine.
- [KSyntaxHighlighting::SyntaxHighlighter](ksyntaxhighlighting-syntaxhighlighter.md): A QSyntaxHighlighter implementation for use with QTextDocument. This supports partial re-highlighting during editing and tracks syntax-based code folding regions.
- [KSyntaxHighlighting::Theme](ksyntaxhighlighting-theme.md): Color theme definition used for highlighting.

## Detailed Description {#details}

It's meant as a building block for text editors as well as for simple highlighted text rendering (e.g. as HTML), supporting both integration with a custom editor as well as a ready-to-use [QSyntaxHighlighter](https://doc.qt.io/qt-6/qsyntaxhighlighter.html) sub-class.
