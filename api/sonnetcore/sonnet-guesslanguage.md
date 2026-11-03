---
title: "Sonnet::GuessLanguage Class"
description: "GuessLanguage determines the language of a given text."
---

# Sonnet::GuessLanguage Class

[GuessLanguage](sonnet-guesslanguage.md) determines the language of a given text. [More...](#details)

- **Header:** `#include <Sonnet/GuessLanguage>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS Sonnet)`  
  `target_link_libraries(mytarget PRIVATE KF6::SonnetCore)`

[List of all members, including inherited members](sonnet-guesslanguage-members.md)

## Public Functions

- [GuessLanguage()](#GuessLanguage)
- [QString identify(const QString &text, const QStringList &suggestions = QStringList()) const](#identify)
- [void setLimits(int maxItems, double minConfidence)](#setLimits)

## Detailed Description {#details}

[GuessLanguage](sonnet-guesslanguage.md) can determine the difference between ~75 languages for a given string. It is based off a Perl script originally written by Maciej Ceglowski called Languid. His script used a 2 part heuristic to determine language. First the text is checked for the scripts it contains, then for each set of languages using those scripts a n-gram frequency model of a given language is compared to a model of the text. The most similar language model is assumed to be the language. If no language is found an empty string is returned.

## Member Function Documentation {#member-function-documentation}

### GuessLanguage::GuessLanguage() {#GuessLanguage}

Constructor

Creates a new [GuessLanguage](sonnet-guesslanguage.md) instance.

### QString GuessLanguage::identify(const QString &*text*, const QStringList &*suggestions* = QStringList()) const {#identify}

Returns the 2 digit ISO 639-1 code for the language of the currently set text and.

Three digits are returned only in the case where a 2 digit code does not exist. If `text` isn't empty, set the text to checked. `text` to be identified

Returns list of the presumed languages of the text, sorted by decreasing confidence. Empty list means it is impossible to determine language with confidence required by [setLimits](sonnet-guesslanguage.md#setLimits)

### void GuessLanguage::setLimits(int *maxItems*, double *minConfidence*) {#setLimits}

Sets limits to number of languages returned by [identify](sonnet-guesslanguage.md#identify)(). The confidence for each language is computed as difference between this and next language on the list normalized to 0-1 range. Reasonable value to get fairly sure result is 0.1 . Default is returning best guess without caring about confidence - exactly as after call to setLimits(1,0).

`maxItems` The list returned by [identify](sonnet-guesslanguage.md#identify)() will never have more than maxItems item

`minConfidence` The list will have only enough items for their summary confidence equal or exceed minConfidence.
