---
title: "KSyntaxHighlighting::AbstractHighlighter Class"
description: "Abstract base class for highlighters."
---

# KSyntaxHighlighting::AbstractHighlighter Class

Abstract base class for highlighters. [More...](#details)

- **Header:** `#include <KSyntaxHighlighting/AbstractHighlighter>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS KSyntaxHighlighting)`  
  `target_link_libraries(mytarget PRIVATE KF6::KSyntaxHighlighting)`
- **Inherited By:** [KSyntaxHighlighting::SyntaxHighlighter](ksyntaxhighlighting-syntaxhighlighter.md)

[List of all members, including inherited members](ksyntaxhighlighting-abstracthighlighter-members.md)

## Public Functions

- [KSyntaxHighlighting::Definition definition() const](#definition)
- [void setDefinition(const KSyntaxHighlighting::Definition &def)](#setDefinition)
- [void setTheme(const KSyntaxHighlighting::Theme &theme)](#setTheme)
- [KSyntaxHighlighting::Theme theme() const](#theme)

## Protected Functions

- [AbstractHighlighter()](#AbstractHighlighter)
- [void applyFolding(int offset, int length, KSyntaxHighlighting::FoldingRegion region)](#applyFolding)
- [void applyFormat(int offset, int length, const KSyntaxHighlighting::Format &format)](#applyFormat)
- [KSyntaxHighlighting::State highlightLine(QStringView text, const KSyntaxHighlighting::State &state)](#highlightLine)

## Detailed Description {#details}

The [AbstractHighlighter](ksyntaxhighlighting-abstracthighlighter.md) provides an interface to highlight text.

The SyntaxHighlighting framework already ships with one implementation, namely the [SyntaxHighlighter](ksyntaxhighlighting-syntaxhighlighter.md), which also derives from [QSyntaxHighlighter](https://doc.qt.io/qt-6/qsyntaxhighlighter.html), meaning that it can be used to highlight a [QTextDocument](https://doc.qt.io/qt-6/qtextdocument.html) or a QML [TextEdit](https://doc.qt.io/qt-6/qml-qtquick-textedit.html). In order to use the [SyntaxHighlighter](ksyntaxhighlighting-syntaxhighlighter.md), just call [setDefinition](ksyntaxhighlighting-abstracthighlighter.md#setDefinition)() and [setTheme](ksyntaxhighlighting-abstracthighlighter.md#setTheme)(), and the associated documents will automatically be highlighted.

However, if you want to use the SyntaxHighlighting framework to implement your own syntax highlighter, you need to sublcass from [AbstractHighlighter](ksyntaxhighlighting-abstracthighlighter.md).

In order to implement your own syntax highlighter, you need to inherit from [AbstractHighlighter](ksyntaxhighlighting-abstracthighlighter.md). Then, pass each text line that needs to be highlighted in order to [highlightLine](ksyntaxhighlighting-abstracthighlighter.md#highlightLine)(). Internally, [highlightLine](ksyntaxhighlighting-abstracthighlighter.md#highlightLine)() uses the Definition initially set through [setDefinition](ksyntaxhighlighting-abstracthighlighter.md#setDefinition)() and the State of the previous text line to parse and highlight the given text line. For each visual highlighting change, [highlightLine](ksyntaxhighlighting-abstracthighlighter.md#highlightLine)() will call [applyFormat](ksyntaxhighlighting-abstracthighlighter.md#applyFormat)(). Therefore, reimplement [applyFormat](ksyntaxhighlighting-abstracthighlighter.md#applyFormat)() to get notified of the Format that is valid in the range starting at the given offset with the specified length. Similarly, for each text part that starts or ends a code folding region, [highlightLine](ksyntaxhighlighting-abstracthighlighter.md#highlightLine)() will call [applyFolding](ksyntaxhighlighting-abstracthighlighter.md#applyFolding)(). Therefore, if you are interested in code folding, reimplement [applyFolding](ksyntaxhighlighting-abstracthighlighter.md#applyFolding)() to get notified of the starting and ending code folding regions, again specified in the range starting at the given offset with the given length.

The Format class itself depends on the current Theme. A theme must be initially set once such that the Format%s instances can be queried for concrete colors.

Optionally, you can also reimplement [setTheme](ksyntaxhighlighting-abstracthighlighter.md#setTheme)() and [setDefinition](ksyntaxhighlighting-abstracthighlighter.md#setDefinition)() to get notified whenever the Definition or the Theme changes.

*See also* [SyntaxHighlighter](ksyntaxhighlighting-syntaxhighlighter.md)

## Member Function Documentation {#member-function-documentation}

### \[protected\] AbstractHighlighter::AbstractHighlighter() {#AbstractHighlighter}

### \[virtual protected\] void AbstractHighlighter::applyFolding(int *offset*, int *length*, KSyntaxHighlighting::FoldingRegion *region*) {#applyFolding}

Reimplement this to apply folding to your output. The provided [FoldingRegion](ksyntaxhighlighting-foldingregion.md) `region` either stars or ends a code folding region in the interval \[ `offset`, `offset` + `length`).

`offset` The start column of the [FoldingRegion](ksyntaxhighlighting-foldingregion.md)

`length` The length of the matching text that starts / ends a folding region

`region` The [FoldingRegion](ksyntaxhighlighting-foldingregion.md) that applies to the range \[offset, offset + length)

> **Note:** The [FoldingRegion](ksyntaxhighlighting-foldingregion.md) `region` is @e always either of type [FoldingRegion::Type::Begin](ksyntaxhighlighting-foldingregion.md#Type-enum) or [FoldingRegion::Type::End](ksyntaxhighlighting-foldingregion.md#Type-enum).

*See also* [applyFormat](ksyntaxhighlighting-abstracthighlighter.md#applyFormat)(), [highlightLine](ksyntaxhighlighting-abstracthighlighter.md#highlightLine)(), [FoldingRegion](ksyntaxhighlighting-foldingregion.md)

### \[pure virtual protected\] void AbstractHighlighter::applyFormat(int *offset*, int *length*, const KSyntaxHighlighting::Format &*format*) {#applyFormat}

Reimplement this to apply formats to your output. The provided `format` is valid for the interval \[ `offset`, `offset` + `length`).

`offset` The start column of the interval for which `format` matches

`length` The length of the matching text

`format` The Format that applies to the range \[offset, offset + length)

> **Note:** Make sure to set a valid Definition, otherwise the parameter `format` is invalid for the entire line passed to [highlightLine](ksyntaxhighlighting-abstracthighlighter.md#highlightLine)() (cf. [Format::isValid](ksyntaxhighlighting-format.md#isValid)()).

*See also* [applyFolding](ksyntaxhighlighting-abstracthighlighter.md#applyFolding)(), [highlightLine](ksyntaxhighlighting-abstracthighlighter.md#highlightLine)()

### KSyntaxHighlighting::Definition AbstractHighlighter::definition() const {#definition}

Returns the syntax definition used for highlighting.

*See also* [setDefinition](ksyntaxhighlighting-abstracthighlighter.md#setDefinition)()

### \[protected\] KSyntaxHighlighting::State AbstractHighlighter::highlightLine(QStringView *text*, const KSyntaxHighlighting::State &*state*) {#highlightLine}

Highlight the given line. Call this from your derived class where appropriate. This will result in any number of [applyFormat](ksyntaxhighlighting-abstracthighlighter.md#applyFormat)() and [applyFolding](ksyntaxhighlighting-abstracthighlighter.md#applyFolding)() calls as a result.

`text` A string containing the text of the line to highlight.

`state` The highlighting state handle returned by the call to highlightLine() for the previous line. For the very first line, just pass a default constructed State().

Returns The state of the highlighting engine after processing the given line. This needs to passed into highlightLine() for the next line. You can store the state for efficient partial re-highlighting for example during editing.

*See also* [applyFormat](ksyntaxhighlighting-abstracthighlighter.md#applyFormat)(), [applyFolding](ksyntaxhighlighting-abstracthighlighter.md#applyFolding)()

### \[virtual\] void AbstractHighlighter::setDefinition(const KSyntaxHighlighting::Definition &*def*) {#setDefinition}

Sets the syntax definition used for highlighting.

Subclasses can re-implement this method to e.g. trigger re-highlighting or clear internal data structures if needed.

*See also* [definition](ksyntaxhighlighting-abstracthighlighter.md#definition)()

### \[virtual\] void AbstractHighlighter::setTheme(const KSyntaxHighlighting::Theme &*theme*) {#setTheme}

Sets the theme used for highlighting.

Subclasses can re-implement this method to e.g. trigger re-highlighing or to do general palette color setup.

*See also* [theme](ksyntaxhighlighting-abstracthighlighter.md#theme)()

### KSyntaxHighlighting::Theme AbstractHighlighter::theme() const {#theme}

Returns the currently selected theme for highlighting.

> **Note:** If no Theme was set through [setTheme](ksyntaxhighlighting-abstracthighlighter.md#setTheme)(), the returned Theme will be invalid, see [Theme::isValid](ksyntaxhighlighting-theme.md#isValid)().

*See also* [setTheme](ksyntaxhighlighting-abstracthighlighter.md#setTheme)()
