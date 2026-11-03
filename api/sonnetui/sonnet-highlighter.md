---
title: "Sonnet::Highlighter Class"
description: "The sonnet Highlighter."
---

# Sonnet::Highlighter Class

The sonnet Highlighter. [More...](#details)

- **Header:** `#include <Sonnet/Highlighter>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS Sonnet)`  
  `target_link_libraries(mytarget PRIVATE KF6::SonnetUi)`

[List of all members, including inherited members](sonnet-highlighter-members.md)

## Public Functions

- [Highlighter(QPlainTextEdit \*textEdit, const QColor &col = QColor())](#Highlighter)
- [Highlighter(QTextEdit \*textEdit, const QColor &col = QColor())](#Highlighter-1)
- [void addWordToDictionary(const QString &word)](#addWordToDictionary)
- [bool autoDetectLanguageDisabled() const](#autoDetectLanguageDisabled)
- [bool automatic() const](#automatic)
- [bool checkerEnabledByDefault() const](#checkerEnabledByDefault)
- [QString currentLanguage() const](#currentLanguage)
- [void ignoreWord(const QString &word)](#ignoreWord)
- [bool isActive() const](#isActive)
- [bool isWordMisspelled(const QString &word)](#isWordMisspelled)
- [void setActive(bool active)](#setActive)
- [void setAutoDetectLanguageDisabled(bool autoDetectDisabled)](#setAutoDetectLanguageDisabled)
- [void setAutomatic(bool automatic)](#setAutomatic)
- [void setDocument(QTextDocument \*document)](#setDocument)
- [void setMisspelledColor(const QColor &color)](#setMisspelledColor)
- [bool spellCheckerFound() const](#spellCheckerFound)
- [QStringList suggestionsForWord(const QString &word, int max = 10)](#suggestionsForWord)
- [QStringList suggestionsForWord(const QString &word, const QTextCursor &cursor, int max = 10)](#suggestionsForWord-1)

## Public Slots

- [void setCurrentLanguage(const QString &language)](#setCurrentLanguage)
- [void slotAutoDetection()](#slotAutoDetection)
- [void slotRehighlight()](#slotRehighlight)

## Signals

- [void activeChanged(const QString &description)](#activeChanged)

## Protected Functions

- [bool intraWordEditing() const](#intraWordEditing)
- [void setIntraWordEditing(bool editing)](#setIntraWordEditing)
- [void setMisspelled(int start, int count)](#setMisspelled)
- [void unsetMisspelled(int start, int count)](#unsetMisspelled)

## Detailed Description {#details}

Used for drawing pretty red lines in text fields

## Member Function Documentation {#member-function-documentation}

### \[explicit\] Highlighter::Highlighter(QPlainTextEdit \**textEdit*, const QColor &*col* = QColor()) {#Highlighter}

Highlighter.

`col` define spellchecking color

### \[explicit\] Highlighter::Highlighter(QTextEdit \**textEdit*, const QColor &*col* = QColor()) {#Highlighter-1}

### \[signal\] void Highlighter::activeChanged(const QString &*description*) {#activeChanged}

Emitted when as-you-type spell checking is enabled or disabled.

`description` is a i18n description of the new state, with an optional reason

### void Highlighter::addWordToDictionary(const QString &*word*) {#addWordToDictionary}

Adds the given word permanently to the dictionary. It will never be marked as misspelled again, even after restarting the application.

`word` the word which will be added to the dictionary

### bool Highlighter::autoDetectLanguageDisabled() const {#autoDetectLanguageDisabled}

Returns whether the automatic language detection is disabled, overriding the Sonnet settings.

Returns true if the automatic language detection is disabled

*See also* [setAutoDetectLanguageDisabled](sonnet-highlighter.md#setAutoDetectLanguageDisabled)()

### bool Highlighter::automatic() const {#automatic}

Returns the state of the automatic disabling of spell checking.

Returns true if spell checking is automatically disabled if there's too many errors

*See also* [setAutomatic](sonnet-highlighter.md#setAutomatic)()

### bool Highlighter::checkerEnabledByDefault() const {#checkerEnabledByDefault}

Return true if checker is enabled by default

### QString Highlighter::currentLanguage() const {#currentLanguage}

Returns the language code for the current language.

*See also* [setCurrentLanguage](sonnet-highlighter.md#setCurrentLanguage)()

### void Highlighter::ignoreWord(const QString &*word*) {#ignoreWord}

Ignores the given word. This word will not be marked misspelled for this session. It will again be marked as misspelled when creating new highlighters.

`word` the word which will be ignored

### \[protected\] bool Highlighter::intraWordEditing() const {#intraWordEditing}

*See also* [setIntraWordEditing](sonnet-highlighter.md#setIntraWordEditing)()

### bool Highlighter::isActive() const {#isActive}

Returns the state of spell checking.

Returns true if spell checking is active

*See also* [setActive](sonnet-highlighter.md#setActive)()

### bool Highlighter::isWordMisspelled(const QString &*word*) {#isWordMisspelled}

Checks if a given word is marked as misspelled by the highlighter.

`word` the word to be checked

Returns true if the given word is misspelled.

### void Highlighter::setActive(bool *active*) {#setActive}

Enable/Disable spell checking.

If `active` is true then spell checking is enabled; otherwise it is disabled. Note that you have to disable automatic (de)activation with [setAutomatic](sonnet-highlighter.md#setAutomatic)() before you change the state of spell checking if you want to persistently enable/disable spell checking.

`active` if true, then spell checking is enabled

*See also* [isActive](sonnet-highlighter.md#isActive)(), [setAutomatic](sonnet-highlighter.md#setAutomatic)()

### void Highlighter::setAutoDetectLanguageDisabled(bool *autoDetectDisabled*) {#setAutoDetectLanguageDisabled}

Sets whether to disable the automatic language detection.

`autoDetectDisabled` if true, the language will not be detected automatically by the spell checker, even if the option is enabled in the Sonnet settings.

*See also* [autoDetectLanguageDisabled](sonnet-highlighter.md#autoDetectLanguageDisabled)()

### void Highlighter::setAutomatic(bool *automatic*) {#setAutomatic}

Sets whether to automatically disable spell checking if there's too many errors.

`automatic` if true, spell checking will be disabled if there's a significant amount of errors.

*See also* [automatic](sonnet-highlighter.md#automatic)()

### \[slot\] void Highlighter::setCurrentLanguage(const QString &*language*) {#setCurrentLanguage}

Set language to use for spell checking.

`language` the language code for the new language to use.

*See also* [currentLanguage](sonnet-highlighter.md#currentLanguage)()

### void Highlighter::setDocument(QTextDocument \**document*) {#setDocument}

Set a new QTextDocument for this highlighter to operate on.

`document` the new document to operate on.

### \[protected\] void Highlighter::setIntraWordEditing(bool *editing*) {#setIntraWordEditing}

*See also* [intraWordEditing](sonnet-highlighter.md#intraWordEditing)()

### \[virtual protected\] void Highlighter::setMisspelled(int *start*, int *count*) {#setMisspelled}

### void Highlighter::setMisspelledColor(const QColor &*color*) {#setMisspelledColor}

Sets the color in which the highlighter underlines misspelled words.

### \[slot\] void Highlighter::slotAutoDetection() {#slotAutoDetection}

Run auto detection, disabling spell checking if too many errors are found.

### \[slot\] void Highlighter::slotRehighlight() {#slotRehighlight}

Force a new highlighting.

### bool Highlighter::spellCheckerFound() const {#spellCheckerFound}

Returns whether a spell checking backend with support for the [currentLanguage](sonnet-highlighter.md#currentLanguage)() was found.

Returns true if spell checking is supported for the current language.

### QStringList Highlighter::suggestionsForWord(const QString &*word*, int *max* = 10) {#suggestionsForWord}

Returns a list of suggested replacements for the given misspelled word. If the word is not misspelled, the list will be empty.

`word` the misspelled word

`max` at most this many suggestions will be returned. If this is -1, as many suggestions as the spell backend supports will be returned.

Returns a list of suggested replacements for the word

### QStringList Highlighter::suggestionsForWord(const QString &*word*, const QTextCursor &*cursor*, int *max* = 10) {#suggestionsForWord-1}

Returns a list of suggested replacements for the given misspelled word. If the word is not misspelled, the list will be empty.

`word` the misspelled word

`cursor` the cursor pointing to the beginning of that word. This is used to determine the language to use, when AutoDetectLanguage is enabled.

`max` at most this many suggestions will be returned. If this is -1, as many suggestions as the spell backend supports will be returned.

Returns a list of suggested replacements for the word

### \[virtual protected\] void Highlighter::unsetMisspelled(int *start*, int *count*) {#unsetMisspelled}
