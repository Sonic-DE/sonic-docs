---
title: "KTextEdit Class"
description: "A KDE'ified QTextEdit."
---

# KTextEdit Class

A KDE'ified [QTextEdit](https://doc.qt.io/qt-6/qtextedit.html). [More...](#details)

- **Header:** `#include <KTextEdit>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS TextWidgets)`  
  `target_link_libraries(mytarget PRIVATE KF6::TextWidgets)`
- **Inherits:** [QTextEdit](https://doc.qt.io/qt-6/qtextedit.html)
- **Inherited By:** [KRichTextEdit](krichtextedit.md)

[List of all members, including inherited members](ktextedit-members.md)

## Properties

- [checkSpellingEnabled : bool](#checkSpellingEnabled-prop)
- [spellCheckingLanguage : QString](#spellCheckingLanguage-prop)

## Public Functions

- [KTextEdit(QWidget \*parent = nullptr)](#KTextEdit)
- [KTextEdit(const QString &text, QWidget \*parent = nullptr)](#KTextEdit-1)
- [bool checkSpellingEnabled() const](#checkSpellingEnabled)
- [void createHighlighter()](#createHighlighter)
- [void enableFindReplace(bool enabled)](#enableFindReplace)
- [void forceSpellChecking()](#forceSpellChecking)
- [void highlightWord(int length, int pos)](#highlightWord)
- [Sonnet::Highlighter \*highlighter() const](#highlighter)
- [QMenu \*mousePopupMenu()](#mousePopupMenu)
- [void setCheckSpellingEnabled(bool check)](#setCheckSpellingEnabled)
- [void setHighlighter(Sonnet::Highlighter \*\_highLighter)](#setHighlighter)
- [void setReadOnly(bool readOnly)](#setReadOnly)
- [bool shouldBlockBeSpellChecked(const QString &block) const](#shouldBlockBeSpellChecked)
- [void showAutoCorrectButton(bool show)](#showAutoCorrectButton)
- [void showTabAction(bool show)](#showTabAction)
- [const QString &spellCheckingLanguage() const](#spellCheckingLanguage)

## Public Slots

- [void addTextDecorator(Sonnet::SpellCheckDecorator \*decorator)](#addTextDecorator)
- [void checkSpelling()](#checkSpelling)
- [void clearDecorator()](#clearDecorator)
- [void replace()](#replace)
- [void setSpellCheckingLanguage(const QString &language)](#setSpellCheckingLanguage)
- [void showSpellConfigDialog(const QString &windowIcon = QString())](#showSpellConfigDialog)

## Signals

- [void aboutToShowContextMenu(QMenu \*menu)](#aboutToShowContextMenu)
- [void checkSpellingChanged(bool)](#checkSpellingChanged)
- [void languageChanged(const QString &language)](#languageChanged)
- [void spellCheckStatus(const QString &)](#spellCheckStatus)
- [void spellCheckerAutoCorrect(const QString &currentWord, const QString &autoCorrectWord)](#spellCheckerAutoCorrect)
- [void spellCheckingCanceled()](#spellCheckingCanceled)
- [void spellCheckingFinished()](#spellCheckingFinished)

## Protected Functions

- [void deleteWordBack()](#deleteWordBack)
- [void deleteWordForward()](#deleteWordForward)

## Detailed Description {#details}

This is just a little subclass of [QTextEdit](https://doc.qt.io/qt-6/qtextedit.html), implementing some standard KDE features, like cursor auto-hiding, configurable wheelscrolling (fast-scroll or zoom), spell checking and deleting of entire words with Ctrl-Backspace or Ctrl-Delete.

This text edit provides two ways of spell checking: background checking, which will mark incorrectly spelled words red, and a spell check dialog, which lets the user check and correct all incorrectly spelled words.

Basic rule: whenever you want to use [QTextEdit](https://doc.qt.io/qt-6/qtextedit.html), use [KTextEdit](ktextedit.md)!

## Property Documentation {#property-documentation}

### checkSpellingEnabled : bool {#checkSpellingEnabled-prop}

**Access functions:**

- virtual `bool` **[checkSpellingEnabled](ktextedit.md#checkSpellingEnabled)**() const
- virtual `void` **[setCheckSpellingEnabled](ktextedit.md#setCheckSpellingEnabled)**(`bool` *check*)

### spellCheckingLanguage : QString {#spellCheckingLanguage-prop}

**Access functions:**

- const `QString` &**[spellCheckingLanguage](ktextedit.md#spellCheckingLanguage)**() const
- `void` **[setSpellCheckingLanguage](ktextedit.md#setSpellCheckingLanguage)**(const `QString` &*language*)

## Member Function Documentation {#member-function-documentation}

### \[explicit\] KTextEdit::KTextEdit(QWidget \**parent* = nullptr) {#KTextEdit}

Constructs a [KTextEdit](ktextedit.md) object. See [QTextEdit::QTextEdit](https://doc.qt.io/qt-6/qtextedit.html) for details.

### \[explicit\] KTextEdit::KTextEdit(const QString &*text*, QWidget \**parent* = nullptr) {#KTextEdit-1}

Constructs a [KTextEdit](ktextedit.md) object. See [QTextEdit::QTextEdit](https://doc.qt.io/qt-6/qtextedit.html) for details.

### \[signal\] void KTextEdit::aboutToShowContextMenu(QMenu \**menu*) {#aboutToShowContextMenu}

Emitted before the context `menu` is displayed.

The signal allows you to add your own entries into the the context menu that is created on demand.

> **Note:** Do not store the pointer to the [QMenu](https://doc.qt.io/qt-6/qmenu.html) provided through since it is created and deleted on demand.

### \[slot\] void KTextEdit::addTextDecorator(Sonnet::SpellCheckDecorator \**decorator*) {#addTextDecorator}

Add custom spell checker `decorator`

### \[slot\] void KTextEdit::checkSpelling() {#checkSpelling}

Show a dialog to check the spelling. The [spellCheckStatus](ktextedit.md#spellCheckStatus)() signal will be emitted when the spell checking dialog is closed.

### \[signal\] void KTextEdit::checkSpellingChanged(*bool*) {#checkSpellingChanged}

emit signal when we activate or not autospellchecking

### \[virtual\] bool KTextEdit::checkSpellingEnabled() const {#checkSpellingEnabled}

Returns true if background spell checking is enabled for this text edit. Note that it even returns true if this is a read-only [KTextEdit](ktextedit.md), where spell checking is actually disabled. By default spell checking is disabled.

> **Note:** Getter function for property [checkSpellingEnabled](ktextedit.md#checkSpellingEnabled-prop).

*See also* [setCheckSpellingEnabled](ktextedit.md#setCheckSpellingEnabled)()

### \[slot\] void KTextEdit::clearDecorator() {#clearDecorator}

clearDecorator clear the spellcheckerdecorator

### \[virtual\] void KTextEdit::createHighlighter() {#createHighlighter}

Allows to create a specific highlighter if reimplemented.

This highlighter is set each time spell checking is toggled on by calling [setCheckSpellingEnabled](ktextedit.md#setCheckSpellingEnabled)(), but can later be overridden by calling [setHighlighter](ktextedit.md#setHighlighter)().

*See also* [setHighlighter](ktextedit.md#setHighlighter)(), [highlighter](ktextedit.md#highlighter)()

### \[virtual protected\] void KTextEdit::deleteWordBack() {#deleteWordBack}

Deletes a word backwards from the current cursor position, if available.

### \[virtual protected\] void KTextEdit::deleteWordForward() {#deleteWordForward}

Deletes a word forwards from the current cursor position, if available.

### void KTextEdit::enableFindReplace(bool *enabled*) {#enableFindReplace}

Sets the find/replace action to the value of `enabled`.

### void KTextEdit::forceSpellChecking() {#forceSpellChecking}

create a modal spellcheck dialogbox and [spellCheckingFinished](ktextedit.md#spellCheckingFinished) signal we sent when we finish spell checking or [spellCheckingCanceled](ktextedit.md#spellCheckingCanceled) signal when we cancel spell checking

### void KTextEdit::highlightWord(int *length*, int *pos*) {#highlightWord}

Selects the characters at the specified position. Any previous selection will be lost. The cursor is moved to the first character of the new selection.

`length` The length of the selection, in number of characters

`pos` The position of the first character of the selection

### Sonnet::Highlighter \*KTextEdit::highlighter() const {#highlighter}

Returns the current highlighter, which is 0 if spell checking is disabled. The default highlighter is the one created by [createHighlighter](ktextedit.md#createHighlighter)(), but might be overridden by [setHighlighter](ktextedit.md#setHighlighter)().

*See also* [setHighlighter](ktextedit.md#setHighlighter)(), [createHighlighter](ktextedit.md#createHighlighter)()

### \[signal\] void KTextEdit::languageChanged(const QString &*language*) {#languageChanged}

Emitted when the user changes the language in the spellcheck dialog shown by [checkSpelling](ktextedit.md#checkSpelling)() or when calling [setSpellCheckingLanguage](ktextedit.md#setSpellCheckingLanguage)().

`language` the new language the user selected

### \[virtual\] QMenu \*KTextEdit::mousePopupMenu() {#mousePopupMenu}

Returns standard [KTextEdit](ktextedit.md) popupMenu

### \[slot\] void KTextEdit::replace() {#replace}

Create replace dialogbox

### \[virtual\] void KTextEdit::setCheckSpellingEnabled(bool *check*) {#setCheckSpellingEnabled}

Turns background spell checking for this text edit to the value of `check`. Note that spell checking is only available in read-writable KTextEdits.

Enabling spell checking will set back the current highlighter to the one returned by [createHighlighter](ktextedit.md#createHighlighter)().

> **Note:** Setter function for property [checkSpellingEnabled](ktextedit.md#checkSpellingEnabled-prop).

*See also* [checkSpellingEnabled](ktextedit.md#checkSpellingEnabled)(), [setReadOnly](ktextedit.md#setReadOnly)()

### void KTextEdit::setHighlighter(Sonnet::Highlighter \**\_highLighter*) {#setHighlighter}

Sets a custom background spellcheck highlighter for this text edit. Normally, the highlighter returned by [createHighlighter](ktextedit.md#createHighlighter)() will be used to detect and highlight incorrectly spelled words, but this function allows to set a custom highlighter.

This has to be called after enabling spell checking with [setCheckSpellingEnabled](ktextedit.md#setCheckSpellingEnabled)(), otherwise it has no effect.

Ownership is transferred to the [KTextEdit](ktextedit.md)

`_highLighter` is the spellcheck highlighter to use

*See also* [highlighter](ktextedit.md#highlighter)(), [createHighlighter](ktextedit.md#createHighlighter)()

### \[virtual\] void KTextEdit::setReadOnly(bool *readOnly*) {#setReadOnly}

Sets the text edit control to the state of `readOnly`.

Reimplemented to set a proper "deactivated" background color.

### \[slot\] void KTextEdit::setSpellCheckingLanguage(const QString &*language*) {#setSpellCheckingLanguage}

Set the spell check `language` which will be used for highlighting spelling mistakes and for the spellcheck dialog. The [languageChanged](ktextedit.md#languageChanged)() signal will be emitted when the new language is different from the old one.

> **Note:** Setter function for property [spellCheckingLanguage](ktextedit.md#spellCheckingLanguage-prop).

*See also* [spellCheckingLanguage](ktextedit.md#spellCheckingLanguage)()

### \[virtual\] bool KTextEdit::shouldBlockBeSpellChecked(const QString &*block*) const {#shouldBlockBeSpellChecked}

Returns true if the given paragraph or `block` should be spellchecked. For example, a mail client does not want to check quoted text, and would return false here (by checking whether the block starts with a quote sign).

Always returns true by default.

### void KTextEdit::showAutoCorrectButton(bool *show*) {#showAutoCorrectButton}

Shows the auto-correct button if the value of `show` is true.

### \[slot\] void KTextEdit::showSpellConfigDialog(const QString &*windowIcon* = QString()) {#showSpellConfigDialog}

Opens a [Sonnet::ConfigDialog](../sonnetui/sonnet-configdialog.md) for this text edit. The spellcheck language of the config dialog is set to the current spellcheck language of the textedit. If the user changes the language in that dialog, the [languageChanged](ktextedit.md#languageChanged)() signal is emitted.

`windowIcon` the icon which is used for the titlebar of the spell dialog window. Can be empty, then no icon is set.

### void KTextEdit::showTabAction(bool *show*) {#showTabAction}

Sets the show tab action to the value of `show`.

### \[signal\] void KTextEdit::spellCheckStatus(*const QString &*) {#spellCheckStatus}

Signal sends when spell checking is finished/stopped/completed

### \[signal\] void KTextEdit::spellCheckerAutoCorrect(const QString &*currentWord*, const QString &*autoCorrectWord*) {#spellCheckerAutoCorrect}

This signal is emitted when the spell checker wants the user to decide if `currentWord` should be replaced with `autoCorrectWord`.

### \[signal\] void KTextEdit::spellCheckingCanceled() {#spellCheckingCanceled}

signal spellCheckingCanceled is sent when we cancel spell checking.

### \[signal\] void KTextEdit::spellCheckingFinished() {#spellCheckingFinished}

signal spellCheckingFinished is sent when we finish spell check or we click on "Terminate" button in sonnet dialogbox

### const QString &KTextEdit::spellCheckingLanguage() const {#spellCheckingLanguage}

Returns the spell checking language which was set by [setSpellCheckingLanguage](ktextedit.md#setSpellCheckingLanguage)(), the spellcheck dialog or the spellcheck config dialog, or an empty string if that has never been called.

> **Note:** Getter function for property [spellCheckingLanguage](ktextedit.md#spellCheckingLanguage-prop).

*See also* [setSpellCheckingLanguage](ktextedit.md#setSpellCheckingLanguage)()
