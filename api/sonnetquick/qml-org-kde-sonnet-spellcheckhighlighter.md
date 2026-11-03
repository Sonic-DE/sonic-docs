---
title: "SpellcheckHighlighter QML Type"
description: "The Sonnet Highlighter class, used for drawing red lines in text fields when detecting spelling mistakes."
---

# SpellcheckHighlighter QML Type

The Sonnet Highlighter class, used for drawing red lines in text fields when detecting spelling mistakes. [More...](#details)

- Import Statement: import org.kde.sonnet

## Detailed Description {#details}

[SpellcheckHighlighter](qml-org-kde-sonnet-spellcheckhighlighter.md) is adapted for QML applications. In usual Kirigami/QQC2-desktop-style applications, this can be used directly by adding `Kirigami.SpellCheck.enabled: true` on a TextArea.

On other QML applications, you can add the [SpellcheckHighlighter](qml-org-kde-sonnet-spellcheckhighlighter.md) as a child of a TextArea.

> **Note:** TextField is not supported, as it lacks QTextDocument API that Sonnet relies on.

```qml
TextArea {
    id: textArea
    Sonnet.SpellcheckHighlighter {
        id: spellcheckhighlighter
        document: textArea.textDocument
        cursorPosition: textArea.cursorPosition
        selectionStart: textArea.selectionStart
        selectionEnd: textArea.selectionEnd
        misspelledColor: Kirigami.Theme.negativeTextColor
        active: true

        onChangeCursorPosition: {
            textArea.cursorPosition = start;
            textArea.moveCursorSelection(end, TextEdit.SelectCharacters);
        }
    }
}
```

Additionally [SpellcheckHighlighter](qml-org-kde-sonnet-spellcheckhighlighter.md) provides some convenient methods to create a context menu with suggestions.

## Property Documentation {#property-documentation}

### active : bool {#active-prop}

This property holds whether spell checking is enabled.

If `active` is true then spell checking is enabled; otherwise it is disabled. Note that you have to disable automatic (de)activation with automatic before you change the state of spell checking if you want to persistently enable/disable spell checking.

### autoDetectLanguageDisabled : bool {#autoDetectLanguageDisabled-prop}

This property holds whether the automatic language detection is disabled overriding the Sonnet global settings.

### automatic : bool {#automatic-prop}

This property holds whether spell checking is automatically disabled if there's too many errors.

### currentLanguage : int {#currentLanguage-prop}

This property holds the current language used for spell checking.

### cursorPosition : int {#cursorPosition-prop}

This property holds the current cursor position.

### document : QQuickTextDocument {#document-prop}

This property holds the underneath document from a QML TextEdit.

### misspelledColor : int {#misspelledColor-prop}

This property holds the spell color. By default, it's red.

### selectionEnd : int {#selectionEnd-prop}

This property holds the end of the selection.

### selectionStart : int {#selectionStart-prop}

This property holds the start of the selection.

### spellCheckerFound : bool {#spellCheckerFound-prop}

This property holds whether a spell checking backend with support for the [currentLanguage](qml-org-kde-sonnet-spellcheckhighlighter.md#currentLanguage-prop) was found.

### wordIsMisspelled : int {#wordIsMisspelled-prop}

This property holds whether the current word under the mouse is misspelled.

### wordUnderMouse : int {#wordUnderMouse-prop}

This property holds the current word under the mouse.

## Method Documentation {#method-documentation}

### void addWordToDictionary(string *word*) {#addWordToDictionary-method}

Adds the given word permanently to the dictionary. It will never be marked as misspelled again, even after restarting the application.

`word` the word which will be added to the dictionary

### void ignoreWord(string *word*) {#ignoreWord-method}

Ignores the given word. This word will not be marked misspelled for this session. It will again be marked as misspelled when creating new highlighters.

`word` the word which will be ignored

### bool isWordMisspelled(string *word*) {#isWordMisspelled-method}

Checks if a given word is marked as misspelled by the highlighter.

`word` the word to be checked Returns true if the given word is misspelled.

### void replaceWord(string *word*, int *at* = -1) {#replaceWord-method}

Replace word at the current cursor position, or `at` if `at` is not -1.

### list\<string\> suggestions(int *position*, int *max* = 5) {#suggestions-method}

Returns a list of suggested replacements for the given misspelled word. If the word is not misspelled, the list will be empty.

`word` the misspelled word

`max` at most this many suggestions will be returned. If this is -1, as many suggestions as the spell backend supports will be returned.

Returns a list of suggested replacements for the word
