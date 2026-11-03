---
title: "KSyntaxHighlighting::SyntaxHighlighter Class"
description: "A QSyntaxHighlighter implementation for use with QTextDocument. This supports partial re-highlighting during editing and tracks syntax-based code folding regions."
---

# KSyntaxHighlighting::SyntaxHighlighter Class

A [QSyntaxHighlighter](https://doc.qt.io/qt-6/qsyntaxhighlighter.html) implementation for use with [QTextDocument](https://doc.qt.io/qt-6/qtextdocument.html). This supports partial re-highlighting during editing and tracks syntax-based code folding regions. [More...](#details)

- **Header:** `#include <KSyntaxHighlighting/SyntaxHighlighter>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS KSyntaxHighlighting)`  
  `target_link_libraries(mytarget PRIVATE KF6::KSyntaxHighlighting)`
- **Inherits:** [QSyntaxHighlighter](https://doc.qt.io/qt-6/qsyntaxhighlighter.html) and [KSyntaxHighlighting::AbstractHighlighter](ksyntaxhighlighting-abstracthighlighter.md)

[List of all members, including inherited members](ksyntaxhighlighting-syntaxhighlighter-members.md)

## Public Functions

- [SyntaxHighlighter(QObject \*parent = nullptr)](#SyntaxHighlighter)
- [SyntaxHighlighter(QTextDocument \*document)](#SyntaxHighlighter-1)
- [QTextBlock findFoldingRegionEnd(const QTextBlock &startBlock) const](#findFoldingRegionEnd)
- [bool startsFoldingRegion(const QTextBlock &startBlock) const](#startsFoldingRegion)

## Detailed Description {#details}

## Member Function Documentation {#member-function-documentation}

### \[explicit\] SyntaxHighlighter::SyntaxHighlighter(QObject \**parent* = nullptr) {#SyntaxHighlighter}

### \[explicit\] SyntaxHighlighter::SyntaxHighlighter(QTextDocument \**document*) {#SyntaxHighlighter-1}

### QTextBlock SyntaxHighlighter::findFoldingRegionEnd(const QTextBlock &*startBlock*) const {#findFoldingRegionEnd}

Finds the end of the folding region starting at `startBlock`. If multiple folding regions begin at `startBlock`, the end of the last/innermost one is returned. This returns an invalid block if no folding region end is found, which typically indicates an unterminated region and thus folding until the document end. This method performs a sequential search starting at `startBlock` for the matching folding region end, which is a potentially expensive operation.

*See also* [startsFoldingRegion](ksyntaxhighlighting-syntaxhighlighter.md#startsFoldingRegion)

### bool SyntaxHighlighter::startsFoldingRegion(const QTextBlock &*startBlock*) const {#startsFoldingRegion}

Returns whether there is a folding region beginning at `startBlock`. This only considers syntax-based folding regions, not indention-based ones as e.g. found in Python.

*See also* [findFoldingRegionEnd](ksyntaxhighlighting-syntaxhighlighter.md#findFoldingRegionEnd)
