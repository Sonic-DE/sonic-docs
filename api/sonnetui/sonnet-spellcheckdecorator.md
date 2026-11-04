---
title: "Sonnet::SpellCheckDecorator Class"
description: "Connects a Sonnet::Highlighter to a QTextEdit extending the context menu of the text edit with spell check suggestions."
---

# Sonnet::SpellCheckDecorator Class

Connects a [Sonnet::Highlighter](sonnet-highlighter.md) to a [QTextEdit](https://doc.qt.io/qt-6/qtextedit.html) extending the context menu of the text edit with spell check suggestions. [More...](#details)

- **Header:** `#include <Sonnet/SpellCheckDecorator>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS Sonnet)`  
  `target_link_libraries(mytarget PRIVATE KF6::SonnetUi)`
- **Inherits:** [QObject](https://doc.qt.io/qt-6/qobject.html)

[List of all members, including inherited members](sonnet-spellcheckdecorator-members.md)

## Public Functions

- [SpellCheckDecorator(QPlainTextEdit \*textEdit)](#SpellCheckDecorator)
- [SpellCheckDecorator(QTextEdit \*textEdit)](#SpellCheckDecorator-1)
- [Sonnet::Highlighter \*highlighter() const](#highlighter)
- [void setHighlighter(Sonnet::Highlighter \*highlighter)](#setHighlighter)

## Protected Functions

- [bool isSpellCheckingEnabledForBlock(const QString &textBlock) const](#isSpellCheckingEnabledForBlock)

## Detailed Description {#details}

## Member Function Documentation {#member-function-documentation}

### \[explicit\] SpellCheckDecorator::SpellCheckDecorator(QPlainTextEdit \**textEdit*) {#SpellCheckDecorator}

Creates a spell-check decorator.

`textEdit` the [QPlainTextEdit](https://doc.qt.io/qt-6/qplaintextedit.html) in need of spell-checking. It also is used as the [QObject](https://doc.qt.io/qt-6/qobject.html) parent for the decorator.

### \[explicit\] SpellCheckDecorator::SpellCheckDecorator(QTextEdit \**textEdit*) {#SpellCheckDecorator-1}

Creates a spell-check decorator.

`textEdit` the [QTextEdit](https://doc.qt.io/qt-6/qtextedit.html) in need of spell-checking. It also is used as the [QObject](https://doc.qt.io/qt-6/qobject.html) parent for the decorator.

### Sonnet::Highlighter \*SpellCheckDecorator::highlighter() const {#highlighter}

Returns the hightlighter used by the decorator

*See also* [setHighlighter](sonnet-spellcheckdecorator.md#setHighlighter)()

### \[virtual protected\] bool SpellCheckDecorator::isSpellCheckingEnabledForBlock(const QString &*textBlock*) const {#isSpellCheckingEnabledForBlock}

Returns true if the spell checking should be enabled for a given block of text The default implementation always returns true.

### void SpellCheckDecorator::setHighlighter(Sonnet::Highlighter \**highlighter*) {#setHighlighter}

Set a custom highlighter on the decorator.

[SpellCheckDecorator](sonnet-spellcheckdecorator.md) does not take ownership of the new highlighter, and you must manually delete the old highlighter.

*See also* [highlighter](sonnet-spellcheckdecorator.md#highlighter)()
